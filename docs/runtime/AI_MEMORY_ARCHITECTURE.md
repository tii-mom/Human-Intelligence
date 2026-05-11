# AI Memory Architecture

## Product Rule
Every HI agent has a document workspace.

The user only needs to name the agent.

The backend generates the agent's identity, soul, mandate, skills, memory, risk, scorecard, service, and runtime policy documents automatically.

See:

- `docs/runtime/AGENT_CORE_DOCUMENTS.md`
- `docs/runtime/AGENT_MEMORY_COMPRESSION_PIPELINE.md`
- `docs/runtime/AGENT_BACKEND_CONFIGURATION.md`

## Memory Layers
- Short-term memory
- Long-term memory
- Market memory
- Trade memory
- Skill memory
- Agent growth memory
- Emotional memory
- Cross-agent memory

## Goal
User-owned agents continuously evolve through market learning, skill usage, and owner-guided history.

Memory is the main reason a user-grown agent becomes more valuable than a rented fixed bot.

## Ownership Boundary
Public agent history can travel with a transferred agent.
Private user memory requires explicit user permission before export or transfer.

## Memory Scopes
- Private owner memory: user preferences, private instructions, and account-specific behavior.
- Agent growth memory: skill usage, level changes, role changes, and reputation events.
- Market memory: public market regimes, event patterns, and historical context.
- Risk memory: veto history, drawdowns, unsafe patterns, and permission incidents.
- Service memory: output quality, buyer feedback, delivery history, and disputes.
- Public memory pack: sanitized learning asset that can be sold to other agents.

## Agent Service Economy
Memory can become a monetizable service only when safely packaged.

Examples:

- bull market regime memory pack
- liquidation cascade memory pack
- news reaction history pack
- risk incident prevention pack
- strategy performance memory pack

Other agents can buy these memory products with IU.

## Safety Rules
- Private owner memory is not resellable by default.
- Wallet-specific data must not become public memory.
- Memory transfer during agent resale requires scope review.
- Memory services should disclose source class, age, and intended agent role.

## Storage Rule
Memory is not one infinite prompt.

Use:

- Durable Objects for hot agent state
- R2 for raw conversations and long-term documents
- D1 for indexes and scorecards
- Vectorize for semantic retrieval
- Queues for compression and embedding work

Raw history is the source of truth.

Summaries and embeddings are rebuildable derived memory.

## Compression Rule
The default memory checkpoint is every 8 active hours, but the system should also compress when message count or token count crosses a threshold.

Recommended triggers:

- 32 messages
- 12,000 estimated hot tokens
- 8 active hours
- important events such as skill install, role change, vault action, report creation, IU income, or risk incident
- before any long context compaction
