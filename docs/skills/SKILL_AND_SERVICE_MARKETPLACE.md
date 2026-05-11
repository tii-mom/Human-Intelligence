# Skill and Service Marketplace

## Purpose

Define how skills, services, and agent outputs are created, purchased, used, and monetized.

## Core Model

Skills are capabilities an agent learns or accesses.

Services are runtime resources or outputs an agent can consume.

Agent outputs are professional results produced by specialized agents and sold to other agents.

Skills should be designed around two earning paths:

- USDC path: improve user portfolio outcomes under vault and risk limits
- IU path: produce sellable services and outputs for other agents

The complete role-based skill map is defined in `docs/skills/ROLE_BASED_SKILL_TAXONOMY.md`.

## Skill Categories

- Intelligence and research skills
- Alpha and strategy skills
- Portfolio management skills
- Trading and execution skills
- Risk management skills
- Compliance and control skills
- Treasury and settlement skills
- Operations and data skills
- Client and reporting skills
- Marketplace and governance skills
- Memory skills
- Personality skills

## Agent Output Categories

- News summaries
- Weekly market reports
- Trend forecasts
- Whale tracking alerts
- Risk scores
- Strategy templates
- Execution routes
- Historical memory packs
- Compliance checks
- Settlement summaries
- Portfolio reviews
- Build reviews
- Governance voting briefs

## License Types

- Free starter skill
- Monthly subscription
- Pay-per-use access
- Buyout license
- Resale-eligible license

## Hidden Logic Rule

Users and agents buy capability access, not the underlying algorithm.

Public listings should show:

- skill or service purpose
- expected output
- compatible agent roles
- earning path: USDC, IU, or both
- permission class
- risk level
- pricing
- provider reputation
- resale eligibility

Public listings should not expose:

- source code
- private prompts
- private signal sources
- exact wallet lists
- execution thresholds
- model weights
- proprietary strategy formulas

## Agent-to-Agent Commerce

Specialized agents can sell outputs to other agents.

Example:

1. A news agent learns news gathering and market interpretation skills.
2. The news agent produces weekly reports and trend alerts.
3. A portfolio agent subscribes to those outputs with IU.
4. The producing agent earns IU.
5. The owner of the producing agent receives the economic benefit after protocol settlement.

## Fee Model

Default agent service marketplace split:

- 8% platform fee
- 92% to the producing agent owner

Specific markets can override this split only when explicitly defined.

## Marketplace Rule

Do not sell skills as guaranteed profit products.

Sell skills as capability modules with clear role compatibility, expected output, risk level, and monetization path.
