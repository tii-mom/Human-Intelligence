# Certified Autonomous Vault

## V1.1 Source

The complete v1.1 vault authority, user intervention boundary, profit handling, and command/event contract is defined in `docs/prd/HI_PRODUCT_SPEC_V1_1.md`.

## Purpose

Define the dedicated funding container that lets a graduated agent fully operate user-deposited capital.

This model protects the user's primary wallet while allowing certified agents to perform real autonomous trading and portfolio management.

## Core Principle

Agent autonomy should be real, but scoped.

A certified agent can fully control the capital the user intentionally deposits into a Certified Autonomous Vault.

The agent cannot control the user's primary wallet or assets outside the vault.

## Vault Structure

```txt
User Primary Wallet
  -> deposits USDC into a dedicated vault

Certified Autonomous Vault
  -> assigned to one graduated agent
  -> governed by certificate scope
  -> connected to approved execution adapters
  -> audited by risk and compliance systems

Execution Accounts
  -> venue-specific accounts or adapters
  -> cannot withdraw to unauthorized destinations
```

## What Full Vault Control Means

Inside its certified vault scope, the agent can:

- allocate capital
- open positions
- close positions
- rebalance
- manage stop loss
- manage take profit
- manage leverage within certified limits
- move capital across approved venues
- buy required agent services with approved IU service budget
- burn approved Compute Tokens for analysis, model calls, APIs, and execution support
- compound, de-risk, or pause exposure

The agent does not need manual approval for every action once the user has enabled certified autonomy for that vault.

## What Full Vault Control Does Not Mean

The agent cannot:

- access the user's primary wallet
- withdraw to arbitrary wallets
- change vault ownership
- increase vault capacity by itself
- bypass certificate limits
- bypass emergency shutdown
- trade unsupported assets
- use unsupported venues
- hide activity from audit logs

## Required Inputs

Before a vault becomes autonomous, the user must define:

- assigned agent
- certificate level required
- USDC deposit amount
- vault mandate
- asset universe
- venue whitelist
- max leverage
- max daily loss
- max drawdown
- max position size
- strategy mandate
- emergency shutdown preference
- profit sweep preference
- IU service budget
- Compute Token runtime budget

## Mandate Templates

Users should be able to choose simple mandate templates:

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

The mandate defines the agent's style before execution starts.

After execution starts, the user should not manually interfere with normal trading unless a pre-set risk line is reached.

## Autonomy Modes

### Manual

Agent recommends actions.
User approves each action.

### Semi-Auto

Agent executes pre-approved action classes.
User approval is required for higher-risk actions.

### Certified Auto

Graduated agent fully controls the dedicated vault within certificate scope.

### Professional Auto

Higher-capacity autonomy for professional agents with stronger audit, bonding, reputation, and renewal requirements.

## Profit and Loss Handling

The vault should track:

- starting USDC balance
- realized PnL
- unrealized PnL
- fees
- IU service spending
- drawdown
- performance attribution
- skill contribution
- agent decision log

Profit sweep can be configured by the user:

- manual claim
- periodic sweep to owner wallet
- reinvest inside vault
- split between reinvestment and owner settlement

The user chooses this before or during vault setup.

## User Intervention Boundary

Once a Certified Autonomous Vault is active, the agent should be allowed to execute its mandate without emotional user interference.

The user can intervene only through pre-defined controls:

- position management line
- max drawdown line
- stop-loss line
- safe-mode trigger
- vault pause rule
- vault close rule

Normal profitable or losing fluctuations should not automatically give the user manual trade override unless the chosen mandate allows it.

## Risk System Role

Risk Guard should not block normal certified agent operation.

Risk Guard should intervene only when:

- certificate limit is violated
- emergency threshold is reached
- user-defined position management line is reached
- user-defined loss line is reached
- unsupported venue or asset is requested
- suspicious withdrawal route appears
- abnormal execution pattern appears
- skill or certificate expires
- black swan mode is triggered

## Certificate Binding

A Certified Autonomous Vault must be bound to:

- agent id
- certificate level
- role track
- allowed strategy scope
- allowed asset universe
- allowed venue set
- vault capacity tier
- renewal date

If the certificate is suspended, the vault should fall back to safe mode.

## User Controls

The user can:

- deposit more USDC
- withdraw available USDC
- reduce vault capacity
- define intervention lines before execution
- pause agent autonomy when a pre-set line is reached
- switch to manual mode when a pre-set line is reached
- close the vault when a pre-set line is reached
- change profit sweep settings
- require automatic re-evaluation

The user cannot expect the vault to avoid all losses.
The product should communicate that autonomous trading can lose money.

## Product Rule

Do not describe this as an agent controlling the user's wallet.

Describe it as:

The user funds a dedicated autonomous vault.
The graduated agent can fully operate that vault.
The user's primary wallet remains outside agent control.
