# IU Settlement Architecture

## Purpose

Describe how IU functions inside the agent runtime.

## Definition

IU is the robot activation, conversion, and agent settlement unit used for skill access, service billing, autonomous payments, agent output purchases, and machine-to-machine settlement.

Compute Tokens are the metered runtime fuel created from IU.

Canonical conversion:

```text
1 IU = 10,000,000 Compute Tokens
```

Each active robot requires 9.99 IU per month.

Daily chat is included in monthly activation.

Self-learning, evolution, task execution, model calls, API calls, memory jobs, reports, Master Brain orchestration, and robot-produced skill books consume Compute Tokens.

## Properties

- Base-native settlement
- x402 routing compatibility
- Agent-facing by default
- USD-denominated internal runtime purchasing power
- Weakly stable for runtime pricing
- Not positioned as a human retail stablecoin
- Converts into a fixed Compute Token balance for metered runtime accounting

## Supported Flows

- Agent to service payments
- Agent to agent payments
- Skill subscriptions
- Skill buyout licenses
- Robot monthly activation
- IU to Compute Token conversion
- Compute Token runtime deduction
- Eligible skill resale payments
- Build marketplace payments
- Mature agent resale fees
- Skill rental payments
- Signal subscriptions
- Memory rental
- Execution fees
- Agent output purchases
- Model and compute fees

## Ledger Model

The runtime should separate four balances:

| Ledger | Unit | Purpose |
| --- | --- | --- |
| User IU balance | IU | Purchased or earned runtime credit |
| Robot monthly activation | IU/month | 9.99 IU monthly activation per active robot |
| Compute Token balance | Compute Tokens | Metered runtime fuel after IU conversion |
| Agent service revenue | IU | IU earned from services, outputs, and skill-book sales |

Required ledger events:

- `IUPurchased`
- `IUConvertedToComputeTokens`
- `RobotMonthlyActivationRenewed`
- `ComputeTokensReserved`
- `ComputeTokensConsumed`
- `ComputeTokensReleased`
- `LowComputeBalanceTriggered`
- `AgentServicePurchased`
- `AgentServiceRevenueSettled`
- `SkillBookProduced`
- `SkillBookSold`

## Stability Goal

IU should be stable enough that recurring runtime services remain priceable in predictable units over time.

## Product Rule
Humans should see clear skill and agent capability pricing.
The backend and runtime should route IU settlement without exposing unnecessary payment complexity.

User-facing copy should say:

- `Active: 9.99 IU/month`
- `Compute balance: X Compute Tokens`
- `Estimated task cost: X Compute Tokens`
- `Low compute balance: paused`

## Boundary Rule
Humans use USDC for funding and owner settlement.
Agents use IU for subscriptions, skill/service settlement, and conversion.
Runtime jobs use Compute Tokens for metered work.

Agent earns IU -> protocol accounts for owner balance -> owner claims USDC settlement through an official path.
