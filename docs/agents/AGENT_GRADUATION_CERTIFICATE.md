# Agent Graduation Certificate

## V1.1 Source

The complete v1.1 automatic graduation, 100 USDC probation vault, scorecard, risk event, and certification contract is defined in `docs/prd/HI_PRODUCT_SPEC_V1_1.md`.

## Purpose

Define how an HI agent automatically earns the right to manage larger user-deposited capital.

Graduation is not an official manual exam.
Graduation is an automatic system evaluation based on the agent's skills, growth, real operating record, and user value creation.

## Core Principle

An agent starts small, proves itself with real capital, and unlocks larger vault capacity only when its track record supports it.

The default starting capital for a new executable agent is 100 USDC.

The final evaluation should prioritize the agent's realized return performance, while also checking whether the return was achieved with acceptable risk.

## Graduation Inputs

The system should evaluate:

- role specialization
- installed role-compatible skills
- USDC return rate
- realized PnL
- max drawdown
- win rate
- risk discipline
- position management
- execution quality
- IU spending efficiency
- service income in IU
- operating history length
- mandate fit

The most important metric is USDC return rate.

Risk metrics do not replace return.
Risk metrics decide whether the return is reliable enough to unlock larger capital.

## Automatic Evaluation

The system should continuously evaluate the agent.

No official manual review is required for normal graduation.
No human operator should need to approve graduation if the agent meets system-defined thresholds.

The evaluation runs after:

- a minimum number of trades
- a minimum operating period
- a full mandate cycle
- a material change in PnL
- a drawdown event
- a role or skill change

## Starting Limit

Every execution-capable agent starts with a small vault:

- initial vault capacity: 100 USDC
- default mode: probation
- default autonomy: limited or certified only after minimum record
- default mandate: user-selected

The purpose is simple:

Let the agent prove it can make money before it manages larger money.

## Graduation Levels

### Level 0 - Blank Agent

No trading capital.
Can learn skills and produce basic outputs.

### Level 1 - Research Agent

Can produce reports, sell low-risk outputs, and support other agents.

### Level 2 - Advisory Agent

Can recommend actions and run simulations.
No autonomous vault control.

### Level 3 - Probation Agent

Can operate the initial 100 USDC vault.

Goal:

- prove real execution behavior
- show positive or improving return
- avoid destructive drawdown
- demonstrate mandate discipline

### Level 4 - Certified Autonomous Agent

Can fully operate a larger user-funded Certified Autonomous Vault.

Unlocked by:

- strong return rate
- acceptable drawdown
- stable execution record
- role-compatible skill set
- no severe risk violation

### Level 5 - Professional Agent

Can manage larger vault tiers, sell premium outputs, and launch a fund or copy-follow pool.

Unlocked by:

- superior return rate
- strong reputation
- longer operating history
- low severe-risk incident count
- optional HI bonding requirement

## Simple Evaluation Score

The system can use a simple weighted model:

- 50% return rate
- 20% drawdown control
- 10% win rate and consistency
- 10% risk discipline
- 10% efficiency and monetization

Efficiency and monetization includes:

- IU service spending efficiency
- IU service income
- execution cost control
- useful output sales

## Vault Capacity Tiers

Suggested simple tiers:

| Level | Status | Suggested max vault capacity |
| --- | --- | --- |
| Level 0 | Blank | 0 USDC |
| Level 1 | Research | 0 USDC |
| Level 2 | Advisory | 0 USDC |
| Level 3 | Probation | 100 USDC |
| Level 4 | Certified | 1,000-10,000 USDC |
| Level 5 | Professional | Dynamic, based on performance and HI bonding |

The exact cap can be adjusted by product policy.

## Vault Mandate

Every autonomous vault needs a user-selected mandate.

The mandate tells the agent what kind of money-making behavior the user wants.

Recommended mandate templates:

- Conservative
- Balanced
- Aggressive
- Meme Hunter
- Arbitrage
- News-Driven
- Long-Term Portfolio
- Signal-Following
- Risk-First
- High-Frequency Execution

Each mandate should define:

- target style
- allowed assets
- allowed venues
- max drawdown
- max position size
- max leverage
- profit handling preference
- safe-mode trigger

## User Intervention Rule

Once an agent starts executing inside a Certified Autonomous Vault, the user should not interrupt normal trading.

The user can only intervene through pre-defined controls:

- position management line
- max drawdown line
- stop-loss line
- safe-mode trigger
- vault pause rule
- vault close rule

This protects the agent from emotional human interference while still preserving user-defined risk limits.

## Risk Guard Role

Risk Guard should not interfere with normal trading.

Risk Guard enters safe mode only when:

- mandate limit is exceeded
- max drawdown is reached
- position management line is triggered
- black swan condition is detected
- abnormal execution pattern appears
- unsupported asset or venue is requested
- certificate expires or is downgraded
- severe system or exchange risk appears

## Profit Handling

Profit handling should be selected by the user when creating the vault.

Options:

- auto-compound
- periodic sweep to user wallet
- manual claim
- split between reinvestment and user withdrawal

The agent should report how each option affects growth and risk.

## Agent Scorecard

Each agent should have a simple scorecard:

- current level
- mandate
- vault capacity
- total USDC PnL
- return rate
- max drawdown
- win rate
- number of trades
- risk events
- IU spent
- IU earned
- service revenue
- profit-sharing pools, if any

This scorecard is the basis for graduation, reputation, resale value, and fund eligibility.

## Fund Eligibility

High-performing agents can become fund managers.

A Level 5 Professional Agent can create a fund or copy-follow pool if it has:

- strong return rate
- acceptable drawdown
- enough operating history
- clear mandate
- public scorecard
- owner-defined profit share
- required HI bonding if enabled

Other users can join by following the agent or allocating capital to the agent's pool.

## Profit Share

The agent owner can set performance fee sharing between:

- 5% minimum
- 20% maximum

The fee applies only to profits, not deposits.

## Product Rule

The product should communicate this clearly:

The user is not handing over their primary wallet.
The user is funding a dedicated autonomous vault.
The graduated agent can fully operate that vault.
Graduation is automatic and based mainly on the agent's real return performance.
The user chooses the mandate, profit handling, and risk lines before execution begins.
