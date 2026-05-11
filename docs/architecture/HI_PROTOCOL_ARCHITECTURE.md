# HI Protocol Architecture

## V1.1 Product and Integration Source

The canonical product and integration contract for v1.1 is `docs/prd/HI_PRODUCT_SPEC_V1_1.md`.

`hi` should consume the v1.1 read models from that spec.

`hi-core` should own command validation, event emission, memory jobs, vault state transitions, and read model projection.

## Frontend
- Next.js
- TailwindCSS
- Framer Motion

## Backend
- Node.js
- PostgreSQL
- Redis
- Cloudflare Workers
- Cloudflare Agents SDK
- Durable Objects
- D1
- R2
- Vectorize
- Queues
- Workflows

## AI Layer
- LangGraph
- AutoGen
- CrewAI
- Agent builder runtime
- Skill compatibility engine
- Agent core document workspace
- Memory compression pipeline
- Context router

## Blockchain
- Base
- TON

## Payments
- x402
- IU as agent runtime settlement asset
- USDC as the human funding and owner settlement boundary

## Economic Layers
- HI: human-facing governance, identity, reputation, premium access, and agent ownership coordination
- IU: agent-facing skill settlement, billing, routing, and runtime payments
- USDC: user deposits, agent vault funding, and owner settlement
- Blank Agent: user-owned agent identity and growth container
- Limited Agent: HI-purchased scarce agent identity and starter archetype
- Skill: capability license installed into agents
- Build: a reusable skill loadout configuration
- Agent Output: reports, signals, risk scores, memory packs, and execution routes sold by specialized agents
- x402: agent payment rail
- Base: settlement layer for IU
- TON: human ecosystem and governance layer

## Vault and Permission Layer
- Agent vaults
- Certified Autonomous Vaults
- Graduation certificate registry
- Permission manager
- Risk guard
- IU runtime budget
- USDC trading capacity
- Certificate-bound execution scope

## Runtime Integrations
- Binance API
- OKX API
- Bybit API
- Coinbase API
- Market data providers
- Skill provider services
- Agent output provider services

## Infrastructure
- Vercel
- Supabase
- Cloudflare

## Agent Memory and Document Layer
- Each agent has a generated document workspace after the user gives it a name.
- Core documents define identity, personality, mandate, skills, memory, risk, scorecard, and services.
- Durable Objects hold hot per-agent runtime state.
- R2 stores core documents, raw conversations, summaries, reports, and trade reviews.
- D1 stores global metadata, lookup indexes, and marketplace discovery records.
- Vectorize stores semantic memory references.
- Queues and Workflows run compression, embedding, summaries, and long-context reviews.

## Product Boundary
The protocol is centered on user-owned agent growth and skill composition.
Trading execution is a runtime output of configured agents, not the primary product identity.
