# Agent Vault and Permission Model

## Purpose

Define how users fund agents while retaining ownership and risk control.

## Core Rule

Agents should not receive control over the user's primary wallet.

Users fund dedicated agent vaults.

After the system grants an agent a graduation certificate, the user can enable certified autonomy for a dedicated vault. In that mode, the agent can fully operate the funds inside that vault without manual approval for every action.

Agent autonomy remains scoped to:

- the deposited vault balance
- certificate level
- role track
- strategy mandate
- user-selected vault mandate template
- asset whitelist
- venue whitelist
- leverage and drawdown limits
- emergency shutdown rules

## Architecture

```txt
User Wallet
  -> deposits USDC
Agent Vault
  -> can become a Certified Autonomous Vault after graduation
Execution Adapter
  -> allowed within certificate scope and vault mandate
```

## Two Budgets

### IU Service Budget

The amount an agent can spend on skill access, signals, service settlement, risk modules, execution routing, and other agent outputs.

### Compute Token Runtime Budget

The amount an agent can burn on model calls, API calls, memory jobs, task execution, self-learning, evolution, and skill generation.

### USDC Trading Capacity

The amount of user capital the agent is allowed to manage or route inside approved strategies.

These budgets should be separate.

## Permission Controls

Users can set:

- maximum position size
- maximum daily loss
- maximum drawdown
- position management line
- maximum single transaction
- asset whitelist
- venue whitelist
- leverage permission
- auto-execution permission
- daily transaction count
- emergency kill switch
- profit handling preference

## Certified Autonomy

Certified autonomy is the target state for a trained trading or portfolio agent.

When enabled, the agent can:

- open positions
- close positions
- rebalance
- manage stop loss
- manage take profit
- manage leverage within certificate limits
- route orders through approved venues
- buy required agent services with approved IU service budget
- burn approved Compute Tokens for analysis, APIs, model calls, and execution support

The agent does not need separate user approval for each action as long as the action stays inside the certified vault scope.

The agent still cannot:

- withdraw to unauthorized wallets
- touch the user's primary wallet
- increase vault capacity by itself
- trade outside its certificate scope
- bypass emergency shutdown
- hide activity from audit logs

## Growth-Based Capacity

Agent vault capacity should grow with demonstrated competence:

- return rate
- realized PnL
- max drawdown
- win rate
- risk discipline
- autonomous vault record
- verified output quality
- installed skill requirements
- reputation
- user funding consent
- optional HI bonding
- automatic system evaluation

## Product Rule

The agent can recommend higher funding or skill purchases, but the user must approve higher vault capacity and higher autonomy level.

Once the user funds a Certified Autonomous Vault and enables the relevant certificate scope, the agent should be able to operate that vault fully.

During active execution, users should not manually interrupt normal trades unless a pre-set position management, drawdown, stop-loss, pause, or close line is reached.
