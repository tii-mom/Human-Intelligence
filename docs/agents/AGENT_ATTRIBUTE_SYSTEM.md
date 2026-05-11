# Agent Attribute System

## Current Source

The current V1.2 robot cultivation, IU awakening, and evolution rules are defined in `docs/prd/HI_PRODUCT_SPEC_V1_2.md`.

The detailed v1.1 free-agent randomization, limited-agent guarantees, rarity, personality bias, and attribute cap rules remain defined in `docs/prd/HI_PRODUCT_SPEC_V1_1.md`.

## Purpose

Define a simple, game-like attribute system for HI agents.

Attributes make each agent feel different, collectible, and worth upgrading without making the product too complex.

## Core Principle

Attributes should create desire.

Users should be able to look at an agent and immediately understand:

- what it is naturally good at
- what role it may grow into
- why a limited agent feels rare
- why a high-attribute agent may have resale value
- why upgrading skills and memory matters

Attributes do not guarantee profit.
They express tendency, growth potential, and specialization.

In V1.2, attributes are part of the pet-style cultivation loop.

Users should understand them as a robot's natural talent and growth ceiling, not as a guaranteed return signal.

## Attribute Set

Keep the system simple.

Each agent has six core attributes and one growth value.

### Alpha

Ability to discover profitable opportunities.

Good for:

- signal agents
- strategy agents
- meme hunters
- arbitrage agents

### Risk

Ability to avoid bad losses and respect risk limits.

Good for:

- risk agents
- portfolio agents
- conservative mandates
- fund-eligible agents

### Execution

Ability to act efficiently after a decision is made.

Good for:

- trading agents
- execution agents
- arbitrage agents
- high-frequency mandates

### Research

Ability to understand market information and produce useful analysis.

Good for:

- news agents
- macro agents
- on-chain agents
- research agents

### Memory

Ability to learn from past behavior, market regimes, and user history.

Good for:

- long-term portfolio agents
- strategy agents
- professional agents
- agents with resale value

### Charisma

Ability to communicate, report, attract users, and sell outputs.

Good for:

- reporting agents
- advisor agents
- copy-pool leaders
- fund managers
- personality-heavy limited agents

### Growth Potential

How much the agent can improve through skills, memory, and operating history.

Growth Potential is the main FOMO attribute.

It should be visible, scarce, and hard to improve.

## Attribute Range

Recommended simple range:

- 1-100 for each core attribute
- 1-100 for Growth Potential

Display tiers:

- C: 1-39
- B: 40-59
- A: 60-79
- S: 80-94
- S+: 95-100

This makes attributes easy to understand and visually collectible.

## Evolution Display

The user-facing card should show:

- stage
- level
- rarity
- top two attributes
- Growth Potential
- active skill slots
- monthly activation state
- Compute Token balance
- next evolution requirement

The product should not force normal users to inspect every underlying attribute unless they want detail.

## Agent Rarity

Agent rarity can be derived from starting attributes and Growth Potential.

Suggested rarity:

- Common
- Rare
- Epic
- Legendary
- Mythic

Rarity should influence:

- visual identity
- starting attribute distribution
- special title
- starter skill bias
- resale appeal
- collection value

Rarity should not directly grant automatic vault authority.

## Free Blank Agent Attributes

Free agents should start with modest randomized attributes.

Example:

- Alpha: 42
- Risk: 55
- Execution: 38
- Research: 48
- Memory: 45
- Charisma: 40
- Growth Potential: 52

Free agents can still become strong through training, skills, memory, and operating history.

This preserves fairness and makes free users feel that growth matters.

## Attribute Generation Rules

Attribute generation should be simple, transparent, and exciting.

Each agent receives:

- six core attributes
- one Growth Potential value
- one rarity tier
- two highlighted strengths

### Free Agent Generation

Free blank agents should usually start modest but occasionally reveal something special.

Suggested free agent rarity distribution:

| Rarity | Probability |
| --- | --- |
| Common | 70% |
| Rare | 24% |
| Epic | 5% |
| Legendary | 0.9% |
| Mythic | 0.1% |

Suggested free agent attribute rules:

- most attributes roll between 30 and 65
- at least one attribute should be 45 or above
- one highlighted strength is selected automatically
- S attribute is possible but rare
- S+ attribute is extremely rare

Suggested free S/S+ chance:

| Result | Probability |
| --- | --- |
| At least one S attribute | 1% |
| At least one S+ attribute | 0.1% |
| Growth Potential S | 0.5% |
| Growth Potential S+ | 0.05% |

This keeps free claims exciting without weakening limited drops.

### Limited Agent Generation

Limited agents should have stronger starting ranges and better Growth Potential odds.

Suggested limited agent rarity distribution:

| Rarity | Probability |
| --- | --- |
| Rare | 55% |
| Epic | 34% |
| Legendary | 10% |
| Mythic | 1% |

Suggested limited agent attribute rules:

- no Common rarity
- at least two attributes should match the agent archetype
- at least one attribute should be A or above
- Growth Potential has higher minimum range
- S and S+ attributes are meaningfully more likely

Suggested limited S/S+ chance:

| Result | Probability |
| --- | --- |
| At least one S attribute | 12% |
| At least one S+ attribute | 2% |
| Growth Potential S | 8% |
| Growth Potential S+ | 1% |

### Limited Drop Guarantees

Every limited drop can define public guarantees.

Example for a 999-agent drop:

- no Common agents
- every agent has numbered edition
- every agent has at least one A attribute
- at least 100 agents have one S attribute
- at least 10 agents have one S+ attribute
- at least 1 Mythic agent exists

Guarantees create trust and FOMO at the same time.

## Reveal Rules

The purchase experience can use a reveal flow:

1. User pays HI for a limited agent.
2. User receives unrevealed agent shell.
3. User spends IU to awaken the limited agent.
4. Reveal shows archetype, edition number, rarity, attributes, Growth Potential, attribute caps, personality bias, and starter skill bias.
5. Agent becomes active or tradable after reveal, depending on drop rules.

Awakening should feel like opening a rare character, not buying a guaranteed yield product.

## Pity and Fairness

Optional pity rules can improve user trust:

- after a defined number of limited purchases, user receives at least Epic
- each drop can have a public rarity table
- unrevealed metadata should be generated fairly and consistently
- team and treasury allocations should be clearly separated

Do not overcomplicate this in v1.
The first version can use public probability tables and numbered editions.

## Limited Agent Attributes

Limited agents can have:

- higher starting attribute totals
- rare Growth Potential ranges
- special attribute bias
- unique title
- numbered edition
- visual skin
- personality package
- starter skill bundle
- exclusive growth path

Example:

### Ancient Emperor Agent

- Alpha: 65
- Risk: 82
- Execution: 58
- Research: 72
- Memory: 76
- Charisma: 88
- Growth Potential: 91

Natural bias:

- portfolio management
- macro command
- treasury discipline
- long-term mandate

### On-chain Detective Agent

- Alpha: 78
- Risk: 61
- Execution: 64
- Research: 87
- Memory: 72
- Charisma: 55
- Growth Potential: 89

Natural bias:

- on-chain intelligence
- whale tracking
- signal discovery
- research outputs

### Meme Hunter Agent

- Alpha: 92
- Risk: 38
- Execution: 81
- Research: 54
- Memory: 48
- Charisma: 74
- Growth Potential: 86

Natural bias:

- early momentum
- signal hunting
- high-risk trading
- fast execution

## Attribute Effects

Attributes should influence:

- recommended role
- compatible starter skills
- skill learning speed
- UI personality tone
- report style
- marketplace filters
- resale value
- copy-pool appeal
- graduation confidence

Attributes should not directly bypass:

- graduation
- Certified Autonomous Vault requirements
- Risk Guard
- user-selected mandate
- profit and loss reality

## Growth Rules

Attributes can improve slowly through:

- installing compatible skills
- successful vault operation
- low drawdown behavior
- profitable mandates
- high-quality reports
- IU service sales
- memory growth
- fund or copy-pool performance

Growth Potential affects how fast and how far attributes can improve.

## FOMO Design Rules

FOMO should come from visible scarcity and identity:

- numbered limited editions
- S and S+ attribute badges
- rare Growth Potential
- rare archetype combinations
- public scorecards
- fund eligibility
- copy-pool popularity
- resale history
- agent titles

Avoid fake complexity.
The user should understand the agent within five seconds.

## Attribute Card

Each agent card should show:

- rarity
- edition number
- Growth Potential
- top two attributes
- recommended role
- mandate fit
- current level
- return rate if active
- max drawdown if active
- fund or copy-pool eligibility

## Product Rule

Attributes are a game-like expression of agent tendency and growth.

They create collectible value and FOMO.

They do not guarantee profit and do not replace real performance.
