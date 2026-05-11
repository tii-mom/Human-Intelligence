# HI Agent System

## V1.2 Source

The current robot cultivation, IU awakening, active work limit, and Master Brain rules are defined in `docs/prd/HI_PRODUCT_SPEC_V1_2.md`.

## Agent Model

Every user can claim exactly one free blank agent.

The free claim is a lifetime account-level right.

If the free agent is transferred, sold, or listed, the user does not receive another free claim by default.

A blank agent is a unique, ownable, transferable AI trading entity. It starts with limited capability and becomes useful only after skills are installed.

## Agent Lifecycle

- Sealed
- Dormant
- Young
- Trainee
- Specialist
- Trial
- Certified
- Professional
- Master Brain
- Listed
- Transferred

Free blank agents begin at Young.

Limited agents begin as Sealed or Dormant until IU awakening.

## Agent Archetypes

Archetypes are not fixed products. They emerge from installed skills, role specialization, memory, and operating history.

- Meme hunter build
- Whale tracker build
- Conservative risk build
- Trend follower build
- On-chain scanner build
- Quant execution build
- News analyst build
- Research reporter build
- Risk auditor build
- Portfolio manager build

## Role System

Each agent should have one primary financial role and optional secondary roles.

Roles are mapped from human finance jobs into agent jobs, including research, strategy, portfolio management, execution, risk, compliance, treasury, operations, reporting, and governance.

The full role system is defined in `docs/agents/AGENT_ROLE_SYSTEM.md`.

## Limited Agents

In addition to free blank agents, HI can issue limited edition agents purchased with HI.

Limited agents can have rare identity, personality archetypes, role bias, special starter slots, or unique growth paths.

Users can hold unlimited limited agents.

Limited agents must be awakened with IU before full hidden stats are revealed and before the full agent workspace is activated.

Limited agents must not guarantee higher returns or bypass permission and risk requirements.

## Agent Properties

- Owner
- Unique agent id
- Rarity
- Edition number, if limited
- Attribute profile
- Growth Potential
- Personality
- Risk profile
- Reputation
- Skill slots
- Skill loadout
- Memory
- Growth level
- Historical performance
- Ownership history
- Agent vault reference
- Settlement account reference
- IU service budget
- monthly activation state
- Compute Token balance
- USDC vault capacity
- Service output history
- Evolution stage
- Next evolution requirement
- Active working status
- Master Brain assignment, if any

## Attribute System

Agents should have simple game-like attributes:

- Alpha
- Risk
- Execution
- Research
- Memory
- Charisma
- Growth Potential

Attributes help users understand an agent's natural strengths, role fit, growth potential, and resale appeal.

Attributes do not guarantee profit or bypass graduation.

The full attribute system is defined in `docs/agents/AGENT_ATTRIBUTE_SYSTEM.md`.

## Agent Coordination

Agents can reason, compare skill outputs, request risk approval, and coordinate with other agents before high-impact actions.

Agents can also buy outputs from specialized agents, such as news reports, risk scores, memory packs, signals, and execution routes.

## Multi-Agent Work Limit

A user can own many agents, but only up to 50 agents can work at the same time.

If more than 5 agents are working at the same time, the user must designate one Master Brain agent.

The Master Brain counts as one active working agent and can coordinate up to 49 worker agents.

The Master Brain:

- receives user goals
- breaks goals into task threads
- assigns work to agents
- allocates Compute Token budgets
- tracks progress
- collects outputs
- asks risk or control agents for checks
- reports progress through Telegram, WeChat, web, or mobile

The Master Brain does not automatically receive trading authority.

If the Master Brain trades or operates a vault, it must graduate and be certified like any other agent.

## Agent States

- Scanning
- Configuring
- Learning
- Executing
- Rebalancing
- Waiting
- Risk Lockdown
- Reporting
- Selling Output
- Coordinating
- Paused for Low IU

## Reputation Layer

Each agent tracks:
- Win rate
- Max drawdown
- Sharpe ratio
- Skill reliability
- Build stability
- Historical behavior
- Output quality
- Risk permission discipline

## Ownership Layer

The user owns the agent itself.
Skill ownership is separate and depends on subscription, buyout, or transferable license rules.

## Fund Control Rule

Agents operate through controlled agent vaults and permission managers.

Agents should never control the user's primary wallet.

A graduated agent can fully operate a user-funded Certified Autonomous Vault when the vault is bound to the agent's certificate scope.
