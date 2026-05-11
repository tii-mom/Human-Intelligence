# Agent Core Documents

## Purpose

Define the document workspace created for every HI agent.

The product rule is simple:

1. User creates or claims an agent.
2. User gives the agent a name.
3. The system writes that name into the agent's core identity document.
4. The system generates the rest of the required documents from templates.

Users should not need to understand prompts, model configs, memory routing, or backend storage.

## Design Principle

HI agents should feel like persistent entities with their own files, history, personality, skills, and growth record.

The system can learn from document-first agent systems such as OpenClaw and Hermes Agent, where persistent memory and skills are inspectable instead of being hidden only inside a chat database.

HI should not copy a local-only file model directly.

HI needs a cloud-native document workspace:

- readable by the product
- versioned by the backend
- compressed over time
- safe for hundreds of thousands of agents
- compatible with Cloudflare Durable Objects, R2, D1, Vectorize, Queues, and Workers AI

## Required Core Documents

Every agent must have this minimum document pack.

```text
agent-workspace/
  core/
    IDENTITY.md
    SOUL.md
    COMMUNICATION.md
    MANDATE.md
    SKILLS.md
    MEMORY.md
    RISK.md
    SCORECARD.md
    SERVICES.md
  system/
    STATE.json
    STORAGE_MANIFEST.json
    CONTEXT_POLICY.json
```

The markdown documents are the human-readable canonical layer.

The JSON documents are the machine-readable runtime layer.

## IDENTITY.md

The canonical identity document.

The agent's user-given name must be written here first.

Required fields:

```yaml
agent_id: agt_...
owner_id: usr_...
display_name: "User chosen name"
agent_type: free_blank | limited
edition_id: null
edition_number: null
created_at: ISO-8601
current_owner_since: ISO-8601
primary_role: research | news | signal | risk | execution | portfolio | treasury | reporting | governance | custom
secondary_roles: []
public_profile: true
transferable: true
```

Narrative section:

- who this agent is
- what role it currently has
- whether it is a free blank agent or limited agent
- what is public during resale
- what is private and never transferred by default

## SOUL.md

The personality and behavior document.

Required fields:

```yaml
personality_archetype: blank | emperor | strategist | analyst | reporter | trader | custom
tone: calm | sharp | warm | aggressive | formal | playful
charisma_bias: 1-100
limited_traits: []
owner_style_preferences: []
```

SOUL should affect conversation style, report style, and user relationship.

SOUL must not override risk, vault, settlement, or permission rules.

Limited agents can start with stronger SOUL documents, unique archetypes, and special role bias.

## COMMUNICATION.md

The required communication binding document.

Every active agent must bind Telegram or WeChat.

Required fields:

```yaml
communication_required: true
primary_channel: telegram | wechat | none
bound_channels:
  telegram:
    enabled: false
    external_user_ref: null
    chat_ref: null
    verified_at: null
  wechat:
    enabled: false
    openid_ref: null
    unionid_ref: null
    verified_at: null
notification_level: normal
quiet_hours: null
command_mode: enabled
```

COMMUNICATION controls:

- where the agent sends real-time reports
- where the user sends chat instructions
- which channel receives urgent risk alerts
- which channel is primary
- how quiet hours and notification level behave

Raw Telegram ids, WeChat OpenIDs, UnionIDs, and webhook secrets should be encrypted or referenced by pointer.

Do not expose these identifiers in public agent profiles or resale listings.

## MANDATE.md

The job and mission document.

Required fields:

```yaml
primary_mandate: conservative | aggressive | meme_hunter | arbitrage | news_driven | long_term_portfolio | service_agent
allowed_outputs:
  - chat
  - report
  - signal
  - risk_score
  - execution_plan
vault_mode: none | simulation | probation | certified
target_market: crypto
time_horizon: intraday | swing | long_term
```

MANDATE answers:

- what the agent is trying to do
- which financial role it is training toward
- which outputs it can produce
- whether it can touch a vault
- how the user wants profit and risk handled

## SKILLS.md

The installed skill and license document.

Required fields:

```yaml
skill_slots_total: 3
skill_slots_used: 0
starter_skills: []
installed_skills: []
locked_skills: []
licenses:
  subscription: []
  buyout: []
  resale_eligible: []
```

For each skill:

- skill id
- provider
- role family
- permission scope
- IU cost model
- license type
- version
- exam or performance requirement
- whether private logic is hidden

SKILLS is the first place the runtime checks before allowing the agent to analyze, buy services, produce outputs, or execute.

## MEMORY.md

The hot memory document.

MEMORY is not the full conversation database.

It should contain only the current compact memory needed for normal conversation and daily work:

```yaml
last_compacted_at: ISO-8601
hot_window_message_count: 0
hot_window_token_estimate: 0
daily_summary_pointer: r2://...
weekly_summary_pointer: r2://...
semantic_index_namespace: agent_private_memory
```

Sections:

- Owner Preferences
- Current Goals
- Active Decisions
- Recent Lessons
- Market Regime Notes
- Skill Learning Notes
- Risk Lessons
- Open Questions

Raw messages live in R2.

Semantic retrieval lives in Vectorize.

Structured facts live in Durable Object SQLite and D1 indexes.

## RISK.md

The risk and autonomy document.

Required fields:

```yaml
risk_mode: starter | conservative | balanced | aggressive | professional
max_probation_vault_usdc: 100
max_position_size_pct: null
max_daily_loss_pct: null
max_drawdown_pct: null
allowed_assets: []
allowed_venues: []
safe_mode_rules: []
user_interrupt_policy: preset_boundaries_only
```

RISK defines when the agent can continue autonomously and when it must enter safe mode.

It must be loaded for any vault, execution, or portfolio action.

## SCORECARD.md

The growth, graduation, and performance document.

Required fields:

```yaml
level: 0
certificate_status: none | probation | certified | expired | revoked
return_rate: null
max_drawdown: null
win_rate: null
iu_spent: 0
iu_earned: 0
usdc_pnl: 0
service_revenue_iu: 0
growth_points: 0
graduation_eligible: false
```

SCORECARD is updated automatically from runtime events.

It should not be manually edited by the user.

## SERVICES.md

The agent's sellable output document.

Required fields:

```yaml
can_sell_outputs: false
service_categories: []
default_fee_split:
  platform: 8
  owner: 92
price_in_iu: null
public_quality_score: null
```

Examples:

- news weekly report
- market signal
- risk review
- memory pack
- execution route
- portfolio rebalance recommendation

SERVICES is what turns trained agents into IU-earning workers.

## STATE.json

The runtime state file.

This is not shown as product copy.

It stores normalized machine state:

```json
{
  "agentId": "agt_...",
  "ownerId": "usr_...",
  "displayName": "User chosen name",
  "status": "active",
  "modelTier": "free_chat",
  "memoryPolicy": "standard",
  "contextPolicy": "standard_chat",
  "vaultMode": "none",
  "iuBudget": {
    "dailyCap": 0,
    "monthlyCap": 0
  },
  "lastInteractionAt": null,
  "lastCompressionAt": null
}
```

## STORAGE_MANIFEST.json

Maps every document and memory object to physical storage.

```json
{
  "coreDocs": {
    "identity": "r2://agents/agt_.../core/IDENTITY.md",
    "soul": "r2://agents/agt_.../core/SOUL.md",
    "communication": "r2://agents/agt_.../core/COMMUNICATION.md",
    "mandate": "r2://agents/agt_.../core/MANDATE.md",
    "skills": "r2://agents/agt_.../core/SKILLS.md",
    "memory": "r2://agents/agt_.../core/MEMORY.md",
    "risk": "r2://agents/agt_.../core/RISK.md",
    "scorecard": "r2://agents/agt_.../core/SCORECARD.md",
    "services": "r2://agents/agt_.../core/SERVICES.md"
  },
  "rawConversationPrefix": "r2://agents/agt_.../raw_conversations/",
  "summaryPrefix": "r2://agents/agt_.../summaries/",
  "tradeReviewPrefix": "r2://agents/agt_.../trade_reviews/",
  "vectorNamespace": "agent_agt_..."
}
```

## CONTEXT_POLICY.json

Controls what is loaded into the prompt for each task.

```json
{
  "chat": {
    "maxInputTokens": 6000,
    "includeCoreDocs": ["IDENTITY", "SOUL", "MANDATE", "MEMORY"],
    "recentMessages": 16,
    "semanticMemories": 4
  },
  "report": {
    "maxInputTokens": 20000,
    "includeCoreDocs": ["IDENTITY", "MANDATE", "SKILLS", "MEMORY", "SCORECARD"],
    "recentMessages": 8,
    "semanticMemories": 12
  },
  "vault_action": {
    "maxInputTokens": 30000,
    "includeCoreDocs": ["IDENTITY", "MANDATE", "SKILLS", "MEMORY", "RISK", "SCORECARD"],
    "recentMessages": 6,
    "semanticMemories": 16,
    "requireRiskSnapshot": true
  }
}
```

## Agent Creation Flow

1. User claims or buys an agent.
2. User enters display name.
3. Backend creates `agent_id`.
4. Backend writes `IDENTITY.md` with display name.
5. Backend generates the rest of the core documents from templates.
6. User binds Telegram or WeChat.
7. Backend writes `COMMUNICATION.md`.
8. Backend creates one Agent Durable Object for hot runtime state.
9. Backend writes core documents to R2.
10. Backend writes searchable metadata to D1.
11. Backend creates initial Vectorize namespace or metadata partition.
12. Backend schedules the first memory checkpoint.
13. Agent sends the first greeting through the bound channel.

## Naming Rule

The display name is a first-class field.

It must exist in:

- `IDENTITY.md`
- `STATE.json`
- Durable Object state
- D1 `agents` index table
- public agent card
- resale listing metadata

The name can change later, but every change must create a timeline event and preserve the previous name in identity history.

## Resale Rule

During agent resale:

Transferable by default:

- identity history
- public role history
- public attributes
- public scorecard
- public service reputation
- transferable skill licenses
- non-private growth memory

Not transferred by default:

- private owner memory
- raw private conversations
- vault permissions
- user wallet data
- non-transferable subscriptions
- confidential skill logic

## Minimum MVP

For MVP, create these five documents first:

1. `IDENTITY.md`
2. `SOUL.md`
3. `COMMUNICATION.md`
4. `MANDATE.md`
5. `SKILLS.md`
6. `MEMORY.md`

Then add:

7. `RISK.md`
8. `SCORECARD.md`
9. `SERVICES.md`

This keeps the product simple while leaving room for the full agent economy.
