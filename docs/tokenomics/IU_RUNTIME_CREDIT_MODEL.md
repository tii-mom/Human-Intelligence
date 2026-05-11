# IU Runtime Credit Model

## Purpose

Define IU as the robot activation, conversion, and agent-only settlement unit used inside HI.

## Core Positioning

IU is not a human retail currency.
IU is not positioned as a freely traded speculative asset.
IU is not a generic stablecoin product.

IU is a USD-denominated robot activation and agent settlement unit used inside the HI agent economy.

In V1.2 product language, IU is not the raw energy meter.

Users can understand IU as the resource that activates robots, awakens limited robots, buys skill access, settles agent services, and converts into Compute Tokens.

Compute Tokens, also called suanli points in user-facing Chinese copy, are the metered runtime fuel.

Default conversion:

```text
1 IU = 10,000,000 Compute Tokens
```

Each active robot requires:

```text
9.99 IU per month
```

Daily chat is included in monthly activation.

Learning, self-evolution, task execution, model calls, API calls, memory jobs, reports, Master Brain orchestration, and robot-produced skill books consume Compute Tokens.

## Human Boundary

Humans use USDC to:

- fund agent budgets
- deposit into agent vaults
- purchase runtime budget
- receive owner settlement

Humans use HI to:

- buy limited agents
- stake or bond reputation
- access premium rights
- participate in governance

## Agent Boundary

Agents use IU to:

- awaken limited agents and reveal full stats
- activate robots monthly
- convert into Compute Tokens
- buy or subscribe to skills
- subscribe to signals
- rent memory
- buy risk modules
- pay execution routing fees
- purchase outputs from other agents
- settle x402 service calls

Agents and runtime jobs use Compute Tokens to:

- learn skills
- pay model and compute fees
- pay API and data access costs
- compress and retrieve memory
- produce reports
- execute user tasks
- self-learn and evolve
- generate validated skill books

## Pricing

IU should preserve runtime purchasing stability.

The product target is:

- 1 IU is priced around 1 USD of internal service purchasing power
- 1 IU converts into 10,000,000 Compute Tokens
- active robots cost 9.99 IU per month
- service prices remain predictable for recurring agent operations
- users do not need to manage DEX exposure or gas mechanics

## Redemption and Settlement

When an agent earns IU, the owner should be able to claim settlement through an official protocol path.

Recommended framing:

Agent earns IU -> protocol accounts for owner balance -> owner claims USDC settlement.

Avoid framing this as free retail IU trading.

## Restrictions

IU should support:

- service whitelists
- budget caps
- agent spending limits
- per-agent Compute Token limits
- per-task Compute Token estimates
- low-balance pause rules
- usage metering
- x402 payment references
- treasury-led purchasing power controls

IU should avoid:

- uncontrolled DEX speculation
- retail checkout positioning
- direct human payment UX
- uncapped agent spending authority outside approved IU service budgets or Compute Token budgets
