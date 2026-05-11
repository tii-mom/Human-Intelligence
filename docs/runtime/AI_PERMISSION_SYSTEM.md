# AI Permission System

## Permission Levels
- Observe
- Suggest
- Semi-auto
- Auto Spot
- Auto Futures
- Certified Auto Vault
- Professional Auto Vault
- High Risk

## Skill Permission Classes
- Observe-only skill
- Suggestion skill
- Risk-control skill
- Execution-request skill
- Autonomous execution skill

## Risk Controls
- Max leverage
- Max drawdown
- Daily loss limit
- Max position size
- Max single transaction
- Daily transaction count
- Asset whitelist
- Venue whitelist
- Emergency shutdown
- AI veto authority

## Goal
Users maintain transparent control over what capital enters agent autonomy while allowing certified agents to fully operate dedicated vaults.

## Product Rule
Installing a skill does not automatically grant trading authority.
The agent can only act within user funding, certificate scope, skill license permissions, and vault mode.

## Budget Separation

Agent permissions must separate:
- IU activation and service budget for monthly activation, skills, subscriptions, service settlement, signals, and execution routing
- Compute Token budget for model calls, API calls, memory jobs, task execution, self-learning, evolution, and skill generation
- USDC trading capacity for user-funded vault operations

Increasing IU or Compute Token budget does not automatically increase trading capacity.
Increasing trading capacity requires user deposit and approval.

Certified agents can fully use approved trading capacity inside a Certified Autonomous Vault.

## Growth-Based Permissions

Higher-risk permissions should unlock only after:
- sufficient operating history
- positive or improving return rate
- risk discipline
- compatible installed skills
- automatic graduation certificate
- user approval
- optional HI bonding
- automatic system evaluation

## Certified Vault Permissions

Certified Auto Vault permission means:

- the user has funded a dedicated vault
- the agent has earned the required certificate automatically
- the vault is bound to the agent id and certificate scope
- the agent can execute autonomously inside that vault
- user approval is not required for every individual trade

This permission does not allow:

- primary wallet access
- unauthorized withdrawals
- vault capacity increases
- certificate scope bypass
- ownership changes
