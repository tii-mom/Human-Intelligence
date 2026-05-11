# IU Settlement Architecture

## Purpose

Describe how IU functions inside the agent runtime.

## Definition

IU is the agent runtime settlement asset used for skill access, service billing, autonomous payments, agent output purchases, and machine-to-machine settlement.

## Properties

- Base-native settlement
- x402 routing compatibility
- Agent-facing by default
- USD-denominated internal runtime purchasing power
- Weakly stable for runtime pricing
- Not positioned as a human retail stablecoin

## Supported Flows

- Agent to service payments
- Agent to agent payments
- Skill subscriptions
- Skill buyout licenses
- Eligible skill resale payments
- Build marketplace payments
- Mature agent resale fees
- Skill rental payments
- Signal subscriptions
- Memory rental
- Execution fees
- Agent output purchases
- Model and compute fees

## Stability Goal

IU should be stable enough that recurring runtime services remain priceable in predictable units over time.

## Product Rule
Humans should see clear skill and agent capability pricing.
The backend and runtime should route IU settlement without exposing unnecessary payment complexity.

## Boundary Rule
Humans use USDC for funding and owner settlement.
Agents use IU for internal runtime service consumption.

Agent earns IU -> protocol accounts for owner balance -> owner claims USDC settlement through an official path.
