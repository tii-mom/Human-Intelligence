# Skill Licensing and Disclosure

## Purpose
Define how skills are sold, subscribed to, transferred, and publicly described.

## License Types

### Subscription
A subscription grants temporary usage rights.

- billed monthly or by configured period
- expires if payment stops
- cannot be freely resold unless explicitly allowed
- does not expose core skill logic

### Buyout License
A buyout grants longer-term usage rights for a skill.

- suggested baseline price: around three months of subscription cost
- may be transferable if the skill provider allows resale
- does not grant source code ownership
- does not grant access to private data sources

### Trial
A trial grants limited access for onboarding or promotion.

- time-limited
- feature-limited or budget-limited
- non-transferable by default

## Resale Rules

Only eligible buyout licenses can be resold.

Skill resale should preserve:
- license id
- skill metadata
- provider attribution
- allowed usage scope
- resale royalty or platform fee

Skill resale should not transfer:
- provider source code
- private model weights
- hidden signal sources
- internal parameters
- privileged API keys

## Build Sales
A build is a saved skill loadout configuration.

Selling a build can transfer:
- recommended skill combination
- slot layout
- risk profile
- public performance summary
- setup metadata

Selling a build does not automatically transfer unavailable or expired skill subscriptions.

## Service Outputs

A skill can enable an agent to produce outputs that other agents buy.

Examples:
- market reports
- live alerts
- risk scores
- route recommendations
- memory packs
- strategy templates

Output purchases should settle in IU.
Default split is 8% platform fee and 92% to the producing agent owner.

## Public Disclosure

Skill cards must be short and outcome-focused.

Public description rules:
- keep copy under 30 Chinese characters when possible
- describe the benefit
- hide the mechanism
- show risk level
- show compatible agent types
- show subscription and buyout price

Do not disclose:
- exact strategy formulas
- private signal sources
- wallet lists
- execution thresholds
- model prompts
- proprietary data weights

## User Promise
Users buy capability access, not the underlying algorithm.

## Agent Promise
Agents buy usable outputs and service access, not provider source code or private data.
