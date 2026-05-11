# Agent Memory Compression Pipeline

## V1.1 Source

The complete v1.1 memory layer, compression trigger, raw archive, daily summary, and vector memory contract is defined in `docs/prd/HI_PRODUCT_SPEC_V1_1.md`.

## Purpose

Prevent memory loss, context overflow, and runaway token usage as HI scales to hundreds of thousands of agents.

Every agent needs persistent memory, but no agent should load full raw chat history into every model call.

## Core Rule

Raw history is the source of truth.

Summaries, embeddings, scorecards, and hot memory are derived indexes.

If a compression job fails, the system must be able to rebuild memory from raw R2 archives.

## Memory Layers

| Layer | Purpose | Storage |
| --- | --- | --- |
| Hot session | Last active messages and immediate working state | Agent Durable Object SQLite |
| Hot summary | Compact current memory for normal chat | `MEMORY.md` in R2 plus DO cache |
| Structured facts | Name, role, skills, preferences, scorecard, vault state | Durable Object SQLite and D1 indexes |
| Semantic memory | Searchable memories for retrieval | Vectorize |
| Raw archive | Full conversations, events, reports, trade reviews | R2 |
| Long summaries | Daily, weekly, monthly summaries | R2 |
| Public memory packs | Sanitized sellable memory products | R2 plus marketplace index |

## Compression Strategy

Do not rely only on a fixed 8-hour rule.

Use a hybrid strategy:

1. Message-count trigger
2. Token-budget trigger
3. Time trigger
4. Event trigger
5. Pre-compaction trigger

This is safer than compressing only every 8 hours.

## Default Compression Triggers

```yaml
hot_message_limit: 32
hot_token_limit: 12000
time_checkpoint_hours: 8
daily_summary_hour_utc: 0
weekly_summary_day: sunday
monthly_profile_update_day: 1
force_compress_before_context_tokens: 16000
```

### Message-Count Trigger

After 32 user/agent turns, create a session summary.

Use this for active users who chat heavily inside a short period.

### Token-Budget Trigger

If the hot conversation window exceeds about 12,000 estimated tokens, compress immediately.

This protects model cost and prevents context overflow.

### Time Trigger

Every active agent should receive an 8-hour checkpoint when new interactions or runtime events exist.

If no new data exists, skip the model call and only update the schedule heartbeat.

### Event Trigger

Compress or extract facts immediately after important events:

- skill installed
- skill removed
- role changed
- mandate changed
- limited agent revealed
- report generated
- signal sold
- IU earned
- IU spent
- vault funded
- vault action executed
- drawdown event
- safe mode event
- graduation level changed
- agent renamed

### Pre-Compaction Trigger

Before any long session is compacted, the runtime should run a silent memory save step.

This captures:

- stable owner preferences
- active unresolved tasks
- newly learned facts
- important market lessons
- skill learning progress
- risk warnings

## Compression Outputs

Each compression job should produce four outputs.

### 1. Session Summary

Short summary of the last hot window.

Stored at:

```text
r2://agents/{agentId}/summaries/session/{yyyy}/{mm}/{dd}/{sessionId}.md
```

### 2. Memory Patch

Small update patch for `MEMORY.md`.

The patch must be reviewable and idempotent.

### 3. Structured Fact Events

Facts written into tables:

```text
agent_facts
agent_preferences
agent_skill_events
agent_risk_events
agent_score_events
agent_market_notes
```

### 4. Vector Records

Embeddings for important retrievable memories.

Each vector record needs metadata:

```json
{
  "agentId": "agt_...",
  "ownerId": "usr_...",
  "scope": "private_owner | agent_growth | public_market | service_output",
  "source": "chat | skill | trade | report | risk | service",
  "createdAt": "ISO-8601",
  "expiresAt": null,
  "sensitivity": "private | transferable | public"
}
```

## Daily Summary

Once per active day, generate a daily memory summary.

Sections:

- What happened
- What the user wanted
- What the agent learned
- What changed in skills or role
- Market observations
- Risk lessons
- Output quality notes
- Open tasks

## Weekly Summary

Once per active week, generate a weekly growth summary.

Sections:

- Performance
- Skill progress
- Memory progress
- Mistakes
- Best outputs
- Risk behavior
- Recommended next skill
- Graduation signal

## Monthly Profile Update

Once per active month, update the agent's deeper profile.

This can use a stronger or longer-context model.

Use it for:

- personality refinement
- long-horizon market memory
- owner preference consolidation
- duplicate memory cleanup
- conflicting memory resolution
- growth scorecard commentary

## Context Assembly

Normal chat should not read raw archives.

A normal model call should load:

1. system policy
2. `IDENTITY.md`
3. `SOUL.md`
4. active `MANDATE.md`
5. selected `SKILLS.md` subset
6. current `MEMORY.md`
7. recent messages
8. top semantic memories
9. current task data

Vault actions additionally require:

1. `RISK.md`
2. `SCORECARD.md`
3. certificate snapshot
4. vault mandate
5. market/risk snapshot

## Token Budgets

Recommended defaults:

| Task | Target context |
| --- | --- |
| Free daily chat | 4k-8k tokens |
| Simple report | 8k-16k tokens |
| Skill learning | 16k-32k tokens |
| Vault decision | 24k-40k tokens |
| Weekly review | 32k-80k tokens |
| Monthly deep memory review | long-context model or offline batch |

The product should use small models for daily chat and reserve expensive models for skills, reports, reviews, and vault decisions.

## Memory Loss Prevention

Rules:

- Write raw messages to R2 before summarization.
- Give every raw conversation chunk an immutable id.
- Make compression jobs idempotent.
- Store summary provenance.
- Keep old summaries instead of overwriting them.
- Update `MEMORY.md` through versioned patches.
- Never use a summary as the only copy of an event.
- Rebuild Vectorize records from R2 if needed.

## Conflict Resolution

When memories conflict:

1. prefer newer explicit owner instructions
2. prefer verified runtime events over chat claims
3. prefer scorecard data over narrative summary
4. preserve contradiction notes for important conflicts
5. ask the user only when the conflict affects money, risk, or identity

## Retention Policy

Recommended MVP defaults:

| Data | Retention |
| --- | --- |
| Raw private chat | indefinite while user owns agent, export/delete supported |
| Hot DO messages | last 32 turns or last 8 hours |
| Session summaries | indefinite |
| Daily summaries | indefinite |
| Weekly summaries | indefinite |
| Vector records | until user deletes memory or agent transfers |
| Vault action logs | indefinite for audit |
| Private owner memory after resale | retained by seller unless explicitly transferred |

## SubQ / Long-Context Model Use

Long-context models can help with deep memory review, but they should not replace the memory database.

Use long-context models for:

- monthly memory consolidation
- reading a large archive for a dispute or audit
- rebuilding a damaged memory summary
- comparing long market history
- producing high-quality agent biographies

Do not use long-context models for every daily chat.

Daily chat should use compact memory plus retrieval.

## MVP Pipeline

Phase 1:

1. Store raw conversations in R2.
2. Store hot state in the Agent Durable Object.
3. Run compression after 32 turns or 8 active hours.
4. Maintain `MEMORY.md`.
5. Store basic structured facts in D1.

Phase 2:

1. Add Vectorize semantic retrieval.
2. Add daily and weekly summaries.
3. Add memory transfer rules for resale.
4. Add memory pack marketplace support.

Phase 3:

1. Add long-context monthly review.
2. Add contradiction detection.
3. Add memory quality score.
4. Add role-specific memory products.
