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

The goal is not to maximize skill count.

The goal is to maximize agent value per active skill.

Too many active skills can make an agent worse by increasing context size, tool conflict, IU burn, decision latency, and responsibility ambiguity.

## Runtime Rules
- A blank agent can hold skills only in supported slots.
- An agent can own more skill licenses than it actively runs.
- Runtime must distinguish owned, installed, active, and locked skills.
- Some skills observe only.
- Some skills can suggest actions.
- Some skills can request execution.
- Risk skills can override or block unsafe actions.
- Expired subscriptions deactivate automatically.
- Buyout licenses remain active within their allowed scope.

## Skill State Model

| State | Meaning | Counts against active slot limit |
| --- | --- | --- |
| Owned | The user or agent owns access to the skill license | No |
| Installed | The skill is attached to an agent build | No, unless activated |
| Active | The skill is loaded for the current task, context, or vault decision | Yes |
| Locked | The skill is required by a certificate, mandate, or safety rule | Yes, reserved slot |
| Suspended | The skill is expired, incompatible, or blocked by policy | No |

## Active Skill Slot Limits

Default limits:

| Agent level | Active skill slots | Locked safety slots |
| --- | --- | --- |
| L0 Blank | 2 | 0 |
| L1 Research/Service | 3 | 0-1 |
| L2 Advisory | 4 | 1 |
| L3 Probation | 5 | 1-2 |
| L4 Certified | 6 | 2 |
| L5 Professional | 8 | 2-3 |

The runtime can allow temporary task-specific overrides only when:

- the task is non-vault and low risk
- the context budget remains safe
- Compute Token budget is sufficient
- there is no permission conflict
- the extra skill has a clear expected value thesis

## Loadout Quality Rules

Good loadouts are focused.

A normal active loadout should include:

- one primary role skill
- one information or research skill
- one risk or permission skill
- one execution, reporting, or service skill when needed
- one memory skill when useful

Bad loadouts should be rejected or warned:

- many skills with the same job
- multiple contradictory strategies
- execution skill without risk guard
- high-IU skills without expected value
- skills irrelevant to the current task
- personality or reporting skills loaded into vault execution
- vault execution skills loaded into simple chat or education tasks

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
- active slot weight
- expected value path
- deactivation rule

## Skill ROI

Every paid skill should have an expected value thesis before purchase or activation.

Examples:

- this skill may reduce slippage by improving route selection
- this skill may reduce drawdown by blocking unsafe leverage
- this skill may increase IU income by producing better reports
- this skill may improve certification readiness by adding auditable risk control

Runtime should track:

- IU spent on the skill license, subscription, or service settlement
- Compute Tokens spent during skill learning and runtime
- outputs produced
- revenue generated
- estimated USDC saved or earned
- risk events avoided
- contribution to certification

Skills that burn IU without measurable value should be downgraded, paused, or recommended for removal.

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
- Treasury and settlement agents install IU budgeting, Compute Token metering, x402 billing, settlement, and revenue split skills.
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
- IU subscription or service budget
- Compute Token runtime budget
- USDC trading capacity
- Risk Guard approval
- role and license compatibility
