# Agent Backend Configuration

## Current Source

The current V1.2 robot cultivation, IU awakening, active work limit, and Master Brain rules are defined in `docs/prd/HI_PRODUCT_SPEC_V1_2.md`.

The detailed v1.1 memory, Cloudflare backend boundary, read model, command model, and event model contract remains defined in `docs/prd/HI_PRODUCT_SPEC_V1_1.md`.

## Purpose

Define the cloud backend required to support persistent HI agents at scale.

The target is a system where each user-created agent has its own documents, memory, skills, scorecard, and runtime state without causing memory loss, oversized prompts, or excessive token usage.

## Recommended Cloudflare Stack

| System | Use |
| --- | --- |
| Cloudflare Agents SDK | Per-agent runtime shell and scheduled tasks |
| Durable Objects | One hot state object per active agent |
| Durable Object SQLite | Hot messages, schedules, state, counters, recent events |
| D1 | Global indexes, user-agent lookup, marketplace/search metadata |
| R2 | Core documents, raw conversations, summaries, reports, trade reviews |
| Vectorize | Semantic memory retrieval and memory search |
| Queues | Async compression, embedding, report generation, backfill |
| Workflows | Durable multi-step jobs such as monthly review or long report generation |
| Workers AI | Free/basic chat and lightweight classification |
| AI Gateway | Model routing, logging, rate limits, caching, provider controls |
| KV | Cached templates, public config, feature flags |
| Telegram Bot API | Telegram binding, chat commands, and alerts |
| WeChat Official Account / Mini Program | WeChat binding, chat commands, and compliant notifications |

## Why This Layout

One database table with all conversations will become expensive and hard to scale.

One prompt with all memory will destroy token cost.

One R2 document per agent with all history will create write conflicts and slow reads.

The correct layout is split by access pattern:

- hot state near the agent
- structured indexes in SQL
- raw history in object storage
- semantic memory in a vector index
- expensive processing off the request path

## Agent Durable Object

Each agent should have a Durable Object id derived from `agent_id`.

The Durable Object owns:

- current websocket/chat state
- hot messages
- active schedule ids
- compression counters
- latest core doc versions
- current IU budget snapshot
- current vault mode snapshot
- memory lock during compression
- bound communication channel snapshot
- pending command confirmations
- local SQLite tables for recent agent state

It should not store full lifetime raw history.

## Durable Object SQLite Tables

MVP tables:

```sql
agents_local_state(
  agent_id TEXT PRIMARY KEY,
  owner_id TEXT NOT NULL,
  display_name TEXT NOT NULL,
  status TEXT NOT NULL,
  growth_stage TEXT,
  active_work_status TEXT,
  master_brain_id TEXT,
  last_interaction_at TEXT,
  last_compression_at TEXT,
  memory_version INTEGER NOT NULL DEFAULT 0
);

hot_messages(
  id TEXT PRIMARY KEY,
  agent_id TEXT NOT NULL,
  role TEXT NOT NULL,
  content TEXT NOT NULL,
  token_estimate INTEGER NOT NULL,
  created_at TEXT NOT NULL,
  archived BOOLEAN NOT NULL DEFAULT 0
);

runtime_events(
  id TEXT PRIMARY KEY,
  agent_id TEXT NOT NULL,
  event_type TEXT NOT NULL,
  payload_json TEXT NOT NULL,
  created_at TEXT NOT NULL,
  compressed BOOLEAN NOT NULL DEFAULT 0
);

pending_commands(
  id TEXT PRIMARY KEY,
  agent_id TEXT NOT NULL,
  user_id TEXT NOT NULL,
  channel TEXT NOT NULL,
  command_class TEXT NOT NULL,
  risk_level TEXT NOT NULL,
  payload_json TEXT NOT NULL,
  status TEXT NOT NULL,
  expires_at TEXT,
  created_at TEXT NOT NULL
);

scheduled_jobs(
  id TEXT PRIMARY KEY,
  agent_id TEXT NOT NULL,
  job_type TEXT NOT NULL,
  schedule_ref TEXT NOT NULL,
  next_run_at TEXT,
  status TEXT NOT NULL
);

agent_task_threads(
  id TEXT PRIMARY KEY,
  owner_id TEXT NOT NULL,
  master_brain_id TEXT,
  assigned_agent_id TEXT NOT NULL,
  objective TEXT NOT NULL,
  expected_output TEXT,
  iu_budget REAL,
  status TEXT NOT NULL,
  progress_json TEXT,
  blocker_json TEXT,
  result_ref TEXT,
  created_at TEXT NOT NULL,
  updated_at TEXT NOT NULL
);
```

## D1 Global Indexes

D1 should not hold raw chat.

D1 should hold queryable metadata:

```sql
agents(
  agent_id TEXT PRIMARY KEY,
  owner_id TEXT NOT NULL,
  display_name TEXT NOT NULL,
  agent_type TEXT NOT NULL,
  acquisition_type TEXT,
  activation_status TEXT NOT NULL DEFAULT 'young',
  growth_stage TEXT,
  is_free_claim BOOLEAN NOT NULL DEFAULT 0,
  master_brain_id TEXT,
  primary_role TEXT,
  level INTEGER NOT NULL DEFAULT 0,
  certificate_status TEXT NOT NULL,
  public_profile BOOLEAN NOT NULL DEFAULT 1,
  created_at TEXT NOT NULL,
  updated_at TEXT NOT NULL
);

agent_documents(
  agent_id TEXT NOT NULL,
  doc_type TEXT NOT NULL,
  r2_key TEXT NOT NULL,
  version INTEGER NOT NULL,
  updated_at TEXT NOT NULL,
  PRIMARY KEY(agent_id, doc_type)
);

agent_scorecards(
  agent_id TEXT PRIMARY KEY,
  return_rate REAL,
  max_drawdown REAL,
  win_rate REAL,
  usdc_pnl REAL,
  iu_spent REAL,
  iu_earned REAL,
  service_revenue_iu REAL,
  updated_at TEXT NOT NULL
);

agent_marketplace_profiles(
  agent_id TEXT PRIMARY KEY,
  can_sell_outputs BOOLEAN NOT NULL,
  service_categories TEXT,
  quality_score REAL,
  owner_fee_share_pct REAL,
  platform_fee_pct REAL,
  updated_at TEXT NOT NULL
);

communication_accounts(
  id TEXT PRIMARY KEY,
  user_id TEXT NOT NULL,
  channel TEXT NOT NULL,
  external_user_ref TEXT NOT NULL,
  verified_at TEXT NOT NULL,
  status TEXT NOT NULL
);

agent_channel_threads(
  id TEXT PRIMARY KEY,
  agent_id TEXT NOT NULL,
  user_id TEXT NOT NULL,
  channel TEXT NOT NULL,
  thread_ref TEXT NOT NULL,
  is_primary BOOLEAN NOT NULL DEFAULT 0,
  created_at TEXT NOT NULL
);

notification_preferences(
  user_id TEXT NOT NULL,
  agent_id TEXT NOT NULL,
  channel TEXT NOT NULL,
  notification_level TEXT NOT NULL,
  quiet_hours_json TEXT,
  PRIMARY KEY(user_id, agent_id, channel)
);

user_agent_limits(
  user_id TEXT PRIMARY KEY,
  free_agent_claimed BOOLEAN NOT NULL DEFAULT 0,
  active_working_agent_count INTEGER NOT NULL DEFAULT 0,
  active_working_agent_limit INTEGER NOT NULL DEFAULT 50,
  master_brain_required BOOLEAN NOT NULL DEFAULT 0,
  updated_at TEXT NOT NULL
);

limited_agent_activations(
  agent_id TEXT PRIMARY KEY,
  owner_id TEXT NOT NULL,
  collection_id TEXT NOT NULL,
  edition_number INTEGER NOT NULL,
  sealed_state TEXT NOT NULL,
  awakening_cost_iu REAL NOT NULL,
  awakened_at TEXT,
  reveal_payload_ref TEXT,
  created_at TEXT NOT NULL
);

iu_energy_budgets(
  agent_id TEXT PRIMARY KEY,
  owner_id TEXT NOT NULL,
  available_iu REAL NOT NULL,
  daily_limit_iu REAL,
  model_token_budget INTEGER,
  api_scope_json TEXT,
  low_energy_threshold_iu REAL,
  status TEXT NOT NULL,
  updated_at TEXT NOT NULL
);
```

At large scale, D1 should be sharded by tenant or agent id range.

Use D1 for lookup and discovery, not high-volume append-only memory.

## R2 Object Layout

Use append-friendly object keys.

```text
agents/{agentId}/core/IDENTITY.md
agents/{agentId}/core/SOUL.md
agents/{agentId}/core/COMMUNICATION.md
agents/{agentId}/core/MANDATE.md
agents/{agentId}/core/SKILLS.md
agents/{agentId}/core/MEMORY.md
agents/{agentId}/core/RISK.md
agents/{agentId}/core/SCORECARD.md
agents/{agentId}/core/SERVICES.md
agents/{agentId}/core/EVOLUTION.md
agents/{agentId}/core/ENERGY.md
agents/{agentId}/core/TASKS.md

agents/{agentId}/system/STATE.json
agents/{agentId}/system/STORAGE_MANIFEST.json
agents/{agentId}/system/CONTEXT_POLICY.json

agents/{agentId}/raw_conversations/{yyyy}/{mm}/{dd}/{sessionId}-{chunkId}.jsonl
agents/{agentId}/summaries/session/{yyyy}/{mm}/{dd}/{summaryId}.md
agents/{agentId}/summaries/daily/{yyyy}/{mm}/{dd}.md
agents/{agentId}/summaries/weekly/{yyyy}/W{week}.md
agents/{agentId}/summaries/monthly/{yyyy}/{mm}.md
agents/{agentId}/trade_reviews/{yyyy}/{mm}/{reviewId}.md
agents/{agentId}/reports/{yyyy}/{mm}/{reportId}.md
agents/{agentId}/memory_packs/{packId}/README.md
```

Avoid repeatedly overwriting one giant memory file.

Core documents can be overwritten through versioned writes.

Raw conversations and summaries should be append-only.

## Vectorize Memory Index

Vector records should be scoped and filtered.

Recommended metadata:

```json
{
  "agentId": "agt_...",
  "ownerId": "usr_...",
  "scope": "private_owner",
  "docType": "session_summary",
  "roleFamily": "news",
  "skillId": null,
  "createdAt": "ISO-8601",
  "sensitivity": "private",
  "r2Key": "agents/agt_.../summaries/session/..."
}
```

Queries must filter by:

- agent id
- owner id when private
- scope
- sensitivity
- role family when useful
- recency when useful

Never let a private memory query search across agents without strict authorization.

## Queue Jobs

Use queues for:

- raw conversation archive
- session compression
- daily summary
- weekly summary
- embedding generation
- memory cleanup
- report generation
- scorecard update
- vector rebuild

Queue jobs should be idempotent.

Every job should include:

```json
{
  "jobId": "job_...",
  "agentId": "agt_...",
  "ownerId": "usr_...",
  "jobType": "session_compression",
  "sourceObjectKeys": [],
  "expectedMemoryVersion": 12,
  "createdAt": "ISO-8601"
}
```

## Scheduling

Use per-agent schedules for active agents only.

Default schedules:

```yaml
active_agent_checkpoint: every 8 hours
daily_summary: once per active day
weekly_summary: once per active week
monthly_deep_review: once per active month
inactive_agent_check: every 7 days
```

Do not schedule heavy jobs for inactive agents.

An agent is active when one of these happened recently:

- user chat
- skill action
- marketplace sale
- vault action
- report generation
- risk event
- service purchase
- limited agent awakening
- task thread progress
- Master Brain orchestration
- IU energy usage

## Communication Gateway

All Telegram, WeChat, and in-app chat messages should enter the same gateway.

Gateway responsibilities:

- verify channel signature or webhook source
- map channel user to HI user
- map message thread to agent
- classify command intent
- check permissions
- route to the agent Durable Object
- create pending confirmation when needed
- send response through the same channel
- archive the message into R2 and memory pipeline

Telegram should use bot deep links or Telegram login for binding and webhooks for incoming messages.

WeChat should use Official Account or Mini Program binding. Proactive messages must follow WeChat platform rules, so app inbox and daily digests should be used when push is limited.

At least one bound channel is required before an agent becomes active.

## V1.2 User and Agent Limits

Required limits:

- each user can claim only one free Blank Agent
- users can hold unlimited limited agents
- limited agents must be awakened with IU before full values are revealed
- one user can have at most 50 active working agents
- more than 5 active working agents requires one Master Brain
- the Master Brain counts as one active working agent
- every active working agent must have an IU energy budget

The backend should enforce these limits at command validation time.

Do not rely on frontend-only checks.

## Master Brain Task Threads

When a user has more than 5 active working agents, all new work should route through the Master Brain unless the command is a direct emergency or account action.

The Master Brain creates task threads with:

- user goal
- assigned agent
- objective
- expected output
- IU budget
- status
- progress
- blocker
- risk notes
- result reference

Task thread events should be queryable by web, Telegram, WeChat, and mobile clients.

Worker agents should not spam the user.

The Master Brain summarizes progress and escalates only:

- blocker
- risk warning
- low IU energy
- user confirmation needed
- task completion
- daily digest

## Model Routing

Recommended routing:

| Use case | Model tier |
| --- | --- |
| Free daily chat | Workers AI small chat model |
| Name/personality greeting | Workers AI small chat model |
| Fact extraction | Workers AI small model or cheap API model |
| Session compression | small/medium API model |
| Skill learning | stronger API model |
| Trading analysis | stronger API model with role-specific tools |
| Vault action reasoning | strongest approved model plus risk checks |
| Monthly memory review | long-context model or offline batch |

Free agents should have a daily free chat budget.

Skill tasks, report generation, trading analysis, and vault work should consume IU or user-approved service budget.

## Context Policy Defaults

```yaml
free_chat:
  max_input_tokens: 6000
  recent_messages: 16
  semantic_memories: 4
  compression_required_after_tokens: 12000

standard_agent:
  max_input_tokens: 12000
  recent_messages: 24
  semantic_memories: 8
  compression_required_after_tokens: 16000

report_agent:
  max_input_tokens: 24000
  recent_messages: 12
  semantic_memories: 16
  include_daily_summary: true

vault_agent:
  max_input_tokens: 40000
  recent_messages: 8
  semantic_memories: 16
  include_risk_doc: true
  include_scorecard: true
  require_fresh_market_snapshot: true
```

## 500k Agent Scaling Plan

500k agents is realistic if the system does not keep all agents hot.

Assumptions:

- most agents are inactive most of the time
- only active agents have scheduled compression
- raw chat is object storage, not SQL rows forever
- summaries are small
- vector memory is filtered and capped by policy
- heavy jobs run asynchronously

Recommended approach:

1. One Durable Object per active agent.
2. R2 for all raw and long-term documents.
3. D1 sharded metadata indexes.
4. Vectorize partitioned by scope and metadata.
5. Queues for all compression and embedding jobs.
6. Rate limits per user, per agent, and per model tier.
7. Hard token budgets for every task type.
8. Inactive agent hibernation.

## Inactive Agent Hibernation

If an agent has no activity for 7 days:

- stop frequent checkpoint jobs
- keep core documents in R2
- keep public profile in D1
- keep semantic memory in Vectorize
- keep raw archive in R2
- resume Durable Object on next user interaction

This protects cost without deleting memory.

## Data Safety

Required rules:

- Raw messages are archived before compression.
- Private owner memory is encrypted or access-controlled by owner.
- Agent transfer does not transfer private memory by default.
- Skill providers cannot read private memory unless the skill permission says so.
- Marketplace memory packs must pass sanitization.
- Vault logs are immutable audit records.
- Core document changes are versioned.

## Backend Environment Defaults

```yaml
AGENT_HOT_MESSAGE_LIMIT: 32
AGENT_HOT_TOKEN_LIMIT: 12000
AGENT_CHECKPOINT_HOURS: 8
AGENT_DAILY_SUMMARY_ENABLED: true
AGENT_WEEKLY_SUMMARY_ENABLED: true
AGENT_MONTHLY_REVIEW_ENABLED: true
AGENT_INACTIVE_DAYS: 7
AGENT_FREE_CHAT_DAILY_MESSAGES: 30
AGENT_FREE_CHAT_MAX_INPUT_TOKENS: 6000
AGENT_VECTOR_TOP_K_CHAT: 4
AGENT_VECTOR_TOP_K_REPORT: 16
AGENT_RAW_ARCHIVE_REQUIRED: true
AGENT_MEMORY_PATCH_VERSIONING: true
```

## MVP Backend Build Order

1. Agent creation API creates `agent_id`, name, and core documents.
2. Store core documents and raw conversations in R2.
3. Add Agent Durable Object hot state.
4. Add D1 agent and document indexes.
5. Add 32-turn / 8-hour compression jobs.
6. Add `MEMORY.md` update patches.
7. Add Vectorize semantic retrieval.
8. Add daily and weekly summaries.
9. Add context policy enforcement.
10. Add monthly long-context memory review.

## External Platform Notes

Cloudflare Agents SDK is useful because it provides a server-side agent class, state, SQL, and scheduling on top of Durable Objects.

Cloudflare Durable Objects are useful because each object has a globally unique identity and colocated durable storage.

R2 is the correct place for raw long-term archives because object storage is better than SQL for large append-only history.

D1 is useful for global lookup and discovery, but each D1 database has size and throughput limits, so raw chat should not live there forever.

Vectorize is useful for semantic retrieval, not as the only memory store.
