# IU Runtime Credit Model

## Purpose

Define IU as the agent-only runtime credit used for service settlement.

## Core Positioning

IU is not a human retail currency.
IU is not positioned as a freely traded speculative asset.
IU is not a generic stablecoin product.

IU is a USD-denominated agent runtime credit used inside the HI agent economy.

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

- learn skills
- subscribe to signals
- rent memory
- pay model and compute fees
- buy risk modules
- pay execution routing fees
- purchase outputs from other agents
- settle x402 service calls

## Pricing

IU should preserve runtime purchasing stability.

The product target is:

- 1 IU is priced around 1 USD of internal service purchasing power
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
- usage metering
- x402 payment references
- treasury-led purchasing power controls

IU should avoid:

- uncontrolled DEX speculation
- retail checkout positioning
- direct human payment UX
- uncapped agent spending authority outside approved IU runtime budgets
