# Frontend System

## Philosophy
HI is not a dashboard. It is a living interface for claiming, training, and growing user-owned AI trading agents.

## Core Principles
- AI-first interfaces
- Operational realism
- Ambient intelligence
- Emotional immersion
- Mobile-first
- Chat-native
- Telegram first
- WeChat priority
- Pet-style robot cultivation
- Simple default controls
- Master Brain for multi-robot work

## Primary Modules

Default user-facing modules:

- My Robots
- Train
- Workroom
- Earnings and Review
- Market

Advanced modules can remain available behind detail views:

- AI Terminal
- Chat Command Center
- Agent Builder
- Agent Role Builder
- Skill and Service Economy
- Skill Loadout
- Agent Build Marketplace
- Limited Agent Marketplace
- Agent Output Marketplace
- Runtime Budget and Vault Controls
- Growth Timeline
- Risk Center
- Consensus Engine

## V1.2 Simplification

The default user path should be:

Pick robot -> activate with IU -> allocate Compute Tokens -> learn skill -> send to work -> see result -> evolve.

The frontend should hide role, memory, permission, settlement, and backend complexity until the user asks for details.

Robot cards should show:

- stage
- level
- rarity
- edition number if limited
- top attributes
- monthly activation state
- Compute Token balance
- active job
- earning status
- next evolution requirement
- sealed, dormant, active, working, paused, or listed state

If more than 5 robots are active, the app should require a Master Brain setup flow before starting more work.

## Agent Role UX
The frontend should let users choose agent roles in human financial terms.

Role families should include:

- intelligence and research
- alpha and strategy
- portfolio management
- trading and execution
- risk management
- compliance and control
- treasury and settlement
- operations and data
- client and reporting
- marketplace and governance

The role selection flow should explain what the agent can produce, what skills it needs, what services it may buy, and what permissions it can request.

## Frontend Stack
- Next.js
- React
- TailwindCSS
- Framer Motion
- Zustand
- React Query
