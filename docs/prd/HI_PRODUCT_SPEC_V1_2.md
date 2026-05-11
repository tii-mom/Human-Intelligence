# HI Product Spec v1.2

## Purpose

This is the current product source document for HI Protocol.

V1.2 simplifies the product around one core experience:

Users cultivate financial agents like valuable game pets, then deploy them to create measurable value.

This document supersedes `docs/prd/HI_PRODUCT_SPEC_V1_1.md` for product rules that involve:

- free agent claim limits
- limited agent ownership and activation
- IU subscription and compute-token runtime
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
I activate it with IU.
I give it compute tokens to work.
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
| IU | Billing, subscription, and settlement unit | robot monthly activation, limited-agent awakening, skill purchases, service settlement, compute-token conversion |
| Compute Tokens / suanli points | Metered runtime fuel | model calls, API calls, memory jobs, task execution, self-learning, evolution, skill generation |

IU should feel like the user's simple payment and activation unit.

Users can understand it simply:

Your robot needs an active 9.99 IU monthly activation to stay awake.
When it actually works, learns, evolves, calls APIs, or produces skills, it burns compute tokens.

Default conversion:

```text
1 IU = 10,000,000 compute tokens
```

Use the user-facing label `Compute Tokens` or `suanli points` instead of raw model-token language.

Advanced users can still see model, API, and service cost details.

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
- can become valuable through monthly activation, compute-token-funded learning, skills, memory, and operating history

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
- monthly activation state
- compute-token balance
- current job
- next evolution requirement
- value score
- earning status

### Evolution Requirements

Evolution should require a mix of:

- active 9.99 IU monthly activation
- compute tokens spent on useful learning or runtime
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

### Skill Book Economy

The user-facing marketplace should stay simple:

| User-facing tier | Internal use |
| --- | --- |
| Basic Skill Book | starter and low-risk skills |
| Advanced Skill Book | stronger role, data, model, or service skills |
| Expert Skill Book | certification-grade, vault-grade, or fund-grade skills |

The existing starter, advanced, and certification skill taxonomy remains valid internally.

Platform skills can be sold as fixed official skill books.

Trained robots can also produce skill books when they have:

- active monthly activation
- enough compute tokens
- role-compatible installed skills
- useful work evidence
- no private owner data leakage
- no hidden strategy disclosure

When a robot produces a skill book, it enters the user's backpack.

The user can install it, hold it, or list it for sale.

Default user skill-book marketplace split:

- 8% platform fee
- 92% to the producing robot owner

Spending compute tokens alone must not guarantee skill production.

The robot must create a useful, validated output.

## 4. IU Subscription and Compute Token Runtime

IU is required for meaningful robot operation, but IU should not be presented as a raw model-token meter.

Canonical rule:

```text
1 IU = 10,000,000 compute tokens
```

IU is the billing, subscription, and settlement unit.

Compute Tokens are the metered runtime fuel.

### Monthly Robot Activation

Each active robot requires:

```text
9.99 IU per month
```

The monthly activation:

- keeps the robot awake for work
- unlocks normal daily conversation
- enables skill learning eligibility
- enables self-learning eligibility
- enables task execution eligibility
- enables evolution eligibility
- activates full stats display for limited robots after awakening

Daily conversation should be included in the monthly activation and should not ask the user for extra compute-token approval.

High-cost reports, deep research, API-heavy analysis, self-learning, task execution, evolution, skill production, and Master Brain orchestration consume compute tokens from the user's balance.

If the monthly activation expires, the robot becomes dormant:

- ownership remains
- memory remains
- public profile remains
- daily work stops
- self-learning stops
- evolution stops
- paid tasks cannot start

### What Burns Compute Tokens

Compute tokens pay for:

- awakening limited agents
- skill learning
- active skill runtime
- model usage
- exchange, market data, news, on-chain, or social API access
- memory compression and retrieval
- reports and backtests
- execution analysis
- risk checks
- agent-to-agent service purchases
- Master Brain orchestration
- self-learning
- evolution attempts
- skill-book generation

### Evolution Cost Rule

Self-learning, evolution, and robot-produced skill books require all of these:

- active 9.99 IU monthly activation
- enough compute tokens
- role-compatible skill path
- useful work, learning, service, or performance evidence
- no unresolved critical risk event

Do not let spending alone guarantee evolution or valuable skill generation.

Growth must be tied to useful output and risk discipline.

Each active agent should have:

- active monthly status
- compute-token balance
- daily compute-token limit
- per-task compute-token estimate
- API scopes
- model tier
- auto-stop rule when compute tokens are low

The product should show this simply:

- Active: 9.99 IU/month
- Compute: enough for today
- Compute: low
- Compute: paused

Advanced views can show IU conversion, model, API, memory, and service itemization.

### Budget Protection Rules

Every robot must support:

- daily compute-token cap
- per-task estimate before paid work
- self-learning on/off switch
- low-balance auto-pause
- high-cost confirmation
- API scope limits
- Master Brain total budget cap
- refund or reversal policy for failed platform-side jobs when applicable

## 5. Money-Making Activation

Robots should not be presented as money-making by default.

Money-making ability must be earned.

Default path:

1. Claim or awaken agent.
2. Pay or renew 9.99 IU monthly activation.
3. Convert IU into compute tokens.
4. Bind Telegram or WeChat.
5. Learn starter skills.
6. Complete simulation tasks.
7. Learn money, risk, or service skills.
8. Enter Trial stage.
9. Operate 100 USDC probation vault or service trial.
10. Pass automatic graduation.
11. Activate Certified Autonomous Vault or publish paid services.

This keeps the user promise honest:

The agent must be cultivated before it can create financial value.

## 6. Multi-Agent Work Limits

Users can own unlimited limited agents, but active work must be bounded.

Rules:

- One user can have at most 50 agents working at the same time.
- The free agent counts toward the active working limit.
- Dormant, sealed, listed, or inactive agents do not count.
- Each active working agent needs active monthly activation.
- Each active working agent needs compute-token budget.
- Each active working agent needs a job, role, or mandate.

### More Than 5 Active Agents

If a user wants more than 5 agents working at the same time, the user must designate one Master Brain agent.

The Master Brain:

- counts as one of the 50 active working agents
- coordinates up to 49 worker agents
- receives user goals
- decomposes work into task threads
- assigns work to agents
- allocates compute-token budgets
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
- compute-token budget
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
- paused for low compute tokens

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
- compute tokens low
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

Pick robot -> activate with IU -> allocate compute tokens -> learn skill -> send to work -> see result -> evolve.

### Robot Card

Each robot card should show:

- stage
- level
- rarity
- edition number if limited
- top attributes
- monthly activation state
- compute-token balance
- active job
- earning status
- next evolution
- whether it is sealed, dormant, active, working, paused, or listed

### Master Brain View

The Master Brain view should show:

- user goal
- active task threads
- worker agents
- compute-token budget usage
- progress
- blockers
- next report time

## 10. Source of Truth Updates

After V1.2, subsystem docs should align to these product rules:

- one free agent per user
- unlimited limited-agent holding
- IU activation required to reveal full limited-agent stats
- 9.99 IU monthly activation per active robot
- 1 IU = 10,000,000 compute tokens
- compute tokens as runtime fuel for learning, model use, API use, memory, tasks, evolution, and skill generation
- pet-style growth and evolution
- active skill limits
- maximum 50 active working agents per user
- more than 5 active working agents require a Master Brain
- Master Brain coordinates worker agents through task threads
- Telegram and WeChat are primary progress channels
