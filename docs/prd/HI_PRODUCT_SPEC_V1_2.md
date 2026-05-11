# HI Product Spec v1.2

## Purpose

This is the current product source document for HI Protocol.

V1.2 simplifies the product around one core experience:

Users cultivate financial agents like valuable game pets, then deploy them to create measurable value.

This document supersedes `docs/prd/HI_PRODUCT_SPEC_V1_1.md` for product rules that involve:

- free agent claim limits
- limited agent ownership and activation
- IU-powered training and runtime
- pet-style growth and evolution
- active skill limits
- multi-agent work limits
- Master Brain orchestration
- Telegram and WeChat progress feedback

V1.1 remains the detailed role, skill, vault, memory, and integration reference unless V1.2 overrides it.

## Core Product Positioning

HI is not a generic trading dashboard.

HI is not a fixed bot subscription.

HI is a financial agent cultivation game and operating system.

The user should feel:

I own a rare agent.
I feed it IU.
I teach it skills.
It evolves.
It works for me.
It reports back.
If it proves itself, it can manage a dedicated vault and make money.

## Economic Purpose

The user spends HI and IU for one reason:

To build an agent that can create measurable value.

Value means:

- USDC profit inside approved vault limits
- lower avoidable losses
- better execution quality
- useful research, signal, risk, memory, or reporting outputs
- IU service income
- certification readiness
- stronger reputation and resale value

If a purchase, skill, activation, or runtime action does not improve one of these value paths, the product should treat it as optional, cosmetic, or low priority.

## HI and IU Roles

| Asset | Human meaning | Product use |
| --- | --- | --- |
| HI | Ownership, scarcity, premium access, reputation, bonding | limited agent purchase, premium rights, fund bonding, ecosystem identity |
| IU | Agent energy and runtime credit | activation, skill learning, model tokens, API access, memory, reports, data, execution analysis, agent-to-agent services |

IU should feel like the agent's energy bar.

Users can understand it simply:

Your robot needs IU to wake up, learn, think, call APIs, and work.

Advanced users can still see token, model, API, and service cost details.

## 1. Agent Ownership Rules

### Free Agent Rule

Each user can claim only one free Blank Agent.

This is a lifetime account-level claim right.

If the user transfers, sells, burns, or loses access to the free agent, the user does not receive another free claim by default.

The free Blank Agent starts as an undeveloped young agent:

- low or modest attributes
- limited active skill slots
- no autonomous trading authority
- no live money-making ability until trained
- can become valuable through IU-funded learning, skills, memory, and operating history

### Limited Agent Rule

Users can hold unlimited limited agents.

Limited agents are purchased with HI.

Limited agents are scarce agent identities with:

- collection id
- edition number
- visual identity
- archetype
- rarity range
- role bias
- personality bias
- growth path
- potential starter advantage

Limited agents do not guarantee profit and do not bypass graduation, risk, vault, or skill rules.

### Limited Agent Activation Rule

A purchased limited agent starts as `sealed` or `dormant`.

Before IU activation, the user can see:

- collection
- edition number
- visual shell
- public rarity table
- possible archetype range
- activation cost

Before IU activation, the user cannot see full hidden values:

- full attributes
- exact Growth Potential
- personality bias details
- attribute caps
- active skill slot profile
- starter skill bias
- hidden role affinity

The user must spend IU to awaken the limited agent.

Awakening reveals the full agent profile and creates the complete agent core document package.

This gives IU a clear product purpose beyond skill subscriptions:

IU wakes agents up.

## 2. Pet-Style Growth System

The user-facing system should feel closer to cultivating a valuable RPG pet than configuring enterprise software.

Use simple stages:

| Stage | User-facing meaning | System capability |
| --- | --- | --- |
| Sealed | Purchased but not awakened | limited metadata only |
| Dormant | Owned but not active | no work, no full stats |
| Young | Claimed or awakened starter agent | basic chat and starter training |
| Trainee | Learning its first role | starter skills, reports, simulations |
| Specialist | Clear role identity | advanced skills and sellable outputs |
| Trial | Proving with small capital or service record | 100 USDC probation vault or service trial |
| Certified | Trusted for scoped autonomy | Certified Autonomous Vault eligibility |
| Professional | High-performing mature agent | larger vault, Copy Pool, Signal Pool, Agent Fund |
| Master Brain | Coordinator agent | can orchestrate other agents |

### Growth Surfaces

The frontend should expose only the most important growth surfaces:

- Level
- Stage
- Rarity
- top two attributes
- Growth Potential
- active skill slots
- IU energy
- current job
- next evolution requirement
- value score
- earning status

### Evolution Requirements

Evolution should require a mix of:

- IU spent on learning or runtime
- role-compatible skills
- memory milestones
- output quality
- completed tasks
- risk discipline
- service income
- simulation or probation performance
- certification score

Evolution is not only cosmetic.

Each evolution should unlock at least one meaningful capability:

- more active skill slots
- better model or API access
- higher memory budget
- service publishing
- probation vault access
- Certified Autonomous Vault eligibility
- multi-agent coordination
- fund or copy pool eligibility

## 3. Skill and Training Simplicity

Skills should be presented as skill books or training modules.

The user should not need to understand all internal role, permission, memory, and runtime details.

The product should recommend a small path:

1. starter skill
2. money or service skill
3. risk skill
4. execution or reporting skill
5. certification skill

Active skills remain limited.

The agent can own many skills, but only a small number can be active in the current job context.

Default active skill slots:

| Stage | Active skill slots |
| --- | ---: |
| Young | 2 |
| Trainee | 3 |
| Specialist | 4 |
| Trial | 5 |
| Certified | 6 |
| Professional | 8 |
| Master Brain | 10 orchestration slots |

Skill purchase and activation must show a value reason:

- helps make USDC
- helps reduce loss
- helps earn IU
- helps pass certification
- helps remember and adapt
- helps coordinate other agents

## 4. IU Runtime and API Consumption

IU is required for meaningful agent operation.

IU pays for:

- awakening limited agents
- skill learning
- active skill runtime
- model token usage
- exchange, market data, news, on-chain, or social API access
- memory compression and retrieval
- reports and backtests
- execution analysis
- risk checks
- agent-to-agent service purchases
- Master Brain orchestration

Each active agent should have:

- IU balance or allocated budget
- daily IU limit
- per-task IU estimate
- API scopes
- model tier
- token budget
- auto-stop rule when IU is low

The product should show this simply:

- Energy: enough for today
- Energy: low
- Energy: paused

Advanced views can show token and API itemization.

## 5. Money-Making Activation

Robots should not be presented as money-making by default.

Money-making ability must be earned.

Default path:

1. Claim or awaken agent.
2. Recharge or allocate IU.
3. Bind Telegram or WeChat.
4. Learn starter skills.
5. Complete simulation tasks.
6. Learn money, risk, or service skills.
7. Enter Trial stage.
8. Operate 100 USDC probation vault or service trial.
9. Pass automatic graduation.
10. Activate Certified Autonomous Vault or publish paid services.

This keeps the user promise honest:

The agent must be cultivated before it can create financial value.

## 6. Multi-Agent Work Limits

Users can own unlimited limited agents, but active work must be bounded.

Rules:

- One user can have at most 50 agents working at the same time.
- The free agent counts toward the active working limit.
- Dormant, sealed, listed, or inactive agents do not count.
- Each active working agent needs IU budget.
- Each active working agent needs a job, role, or mandate.

### More Than 5 Active Agents

If a user wants more than 5 agents working at the same time, the user must designate one Master Brain agent.

The Master Brain:

- counts as one of the 50 active working agents
- coordinates up to 49 worker agents
- receives user goals
- decomposes work into task threads
- assigns work to agents
- allocates IU budgets
- tracks progress
- collects outputs
- asks risk/control agents for checks
- reports status to the user through Telegram, WeChat, web, or mobile

The Master Brain does not automatically receive trading authority.

If it trades or manages a vault, it must graduate like any other agent.

## 7. Master Brain Thread System

The Master Brain should feel like a team manager.

It should create agent work threads similar to a coding agent thread system:

```text
User goal
  -> Master Brain plan
  -> agent task threads
  -> progress updates
  -> output review
  -> user summary
  -> memory and scorecard update
```

Each task thread should track:

- task id
- assigned agent
- objective
- expected output
- IU budget
- status
- progress
- blockers
- result
- risk notes
- next action

Progress states:

- queued
- running
- waiting for data
- waiting for risk check
- waiting for user confirmation
- completed
- failed
- paused for low IU

## 8. User Feedback Rules

The user should not need to watch dashboards all day.

Agents and Master Brain must report through:

- Telegram
- WeChat
- HI web app
- mobile app

Default feedback:

- job started
- meaningful progress
- blocker
- IU low
- risk warning
- task completed
- daily summary

For users with a Master Brain, worker agents should not spam the user.

The Master Brain summarizes and escalates only what matters.

## 9. Simplified Frontend

The main app should have five primary modules:

- My Robots
- Train
- Workroom
- Earnings and Review
- Market

Avoid making users manage every technical subsystem directly.

Advanced users can open detailed views, but the default path should be:

Pick robot -> feed IU -> learn skill -> send to work -> see result -> evolve.

### Robot Card

Each robot card should show:

- stage
- level
- rarity
- edition number if limited
- top attributes
- IU energy
- active job
- earning status
- next evolution
- whether it is sealed, dormant, active, working, paused, or listed

### Master Brain View

The Master Brain view should show:

- user goal
- active task threads
- worker agents
- IU budget usage
- progress
- blockers
- next report time

## 10. Source of Truth Updates

After V1.2, subsystem docs should align to these product rules:

- one free agent per user
- unlimited limited-agent holding
- IU activation required to reveal full limited-agent stats
- IU as energy for learning, token use, API use, and work
- pet-style growth and evolution
- active skill limits
- maximum 50 active working agents per user
- more than 5 active working agents require a Master Brain
- Master Brain coordinates worker agents through task threads
- Telegram and WeChat are primary progress channels

