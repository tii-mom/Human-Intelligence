# Skill Runtime System

## Purpose
Define how AI skills install, activate, combine, and evolve inside user-owned agents.

## Core Systems
- Skill loading
- Skill slots
- Skill activation
- Skill compatibility checks
- Skill conflicts
- Skill inheritance
- Skill fusion
- Skill mutation
- Skill monetization
- Skill decay
- Skill attribution

## Goal
Skills become living capability assets that make blank agents useful, differentiated, and valuable.

Skills are also the production machinery of the Agent Service Economy.
A news skill can help create reports.
A risk skill can help create risk scores.
A signal skill can help create subscription alerts.
An execution skill can help create routing outputs.

The role-based skill map is defined in `docs/skills/ROLE_BASED_SKILL_TAXONOMY.md`.

Every skill should help at least one of two economic paths:

- USDC path: improve the user's trading, portfolio, risk, or execution outcomes
- IU path: produce outputs or services that other agents can buy

## Runtime Rules
- A blank agent can hold skills only in supported slots.
- Some skills observe only.
- Some skills can suggest actions.
- Some skills can request execution.
- Risk skills can override or block unsafe actions.
- Expired subscriptions deactivate automatically.
- Buyout licenses remain active within their allowed scope.

## Skill Object
Each skill should define:

- category
- compatible agent roles
- required data permissions
- output type
- risk tier
- license model
- IU pricing model
- earning path
- hidden logic boundary
- resale eligibility
- audit status

## License Models
- Starter skill: free, basic, non-resellable.
- Subscription: recurring IU runtime access.
- Pay-per-use: IU charged per call or output.
- Buyout: persistent access inside the allowed scope.
- Resale-eligible license: transferable under marketplace rules.

## Agent Role Compatibility
Skills should reinforce specialization:

- Intelligence and research agents install gathering, summarization, source ranking, and thesis skills.
- Alpha and strategy agents install signal, factor, backtest, and scenario skills.
- Portfolio management agents install allocation, rebalance, position sizing, and reporting skills.
- Trading and execution agents install routing, TWAP, slippage, liquidity, and protection skills.
- Risk management agents install drawdown, exposure, volatility, stress test, and veto skills.
- Compliance and control agents install license validation, permission checking, audit, and policy skills.
- Treasury and settlement agents install IU budgeting, x402 billing, settlement, and revenue split skills.
- Operations and data agents install normalization, reconciliation, monitoring, and feed quality skills.
- Client and reporting agents install explanation, education, localization, voice, and Telegram skills.
- Marketplace and governance agents install curation, reputation, dispute review, and proposal summary skills.

## Monetizable Outputs
When a skilled agent produces professional output, that output can become an agent service:

- market report
- signal stream
- risk score
- memory pack
- execution route
- strategy template
- portfolio review

Other agents can buy these outputs with IU.
The default service marketplace split is 8% platform fee and 92% to the producing agent owner.

## Safety Boundary
Skill installation does not grant wallet control.

Execution authority still requires:

- user approval or standing permission
- graduation certificate for autonomous vault operation
- Agent Vault capacity
- IU runtime budget
- USDC trading capacity
- Risk Guard approval
- role and license compatibility
