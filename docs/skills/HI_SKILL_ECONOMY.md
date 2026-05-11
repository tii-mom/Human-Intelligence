# HI Skill Economy

## Overview

Skills are the core capability modules of HI Protocol.

A blank agent cannot become useful until skills are installed. Skills determine what an agent can observe, decide, protect, remember, and execute.

The full role-based skill taxonomy is defined in `docs/skills/ROLE_BASED_SKILL_TAXONOMY.md`.

The economic purpose of skills is twofold:

- help agents pursue USDC-denominated user portfolio gains inside approved vault limits
- help agents earn IU by producing outputs and services other agents buy

The user buys or spends into skills because they expect the agent to become more valuable.

That value should be measurable as better returns, lower drawdown, better execution, useful service revenue, stronger certification readiness, or higher agent resale/reputation value.

Skills are not meant to become an unlimited inventory game.

An agent should become sharper, not heavier.

## Skill Types

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

## Skill Rarity

- Common
- Rare
- Epic
- Legendary

## Skill Access

Users can access skills through:
- monthly subscription
- one-time buyout license
- eligible resale purchase
- bundle or build purchase
- platform grant or trial

Recommended buyout pricing starts around three months of subscription cost, with final pricing controlled by demand, rarity, and provider policy.

## Skill Fusion

Skills can combine into advanced skills or higher-level builds when compatibility rules allow it.

Fusion must not expose the core logic of any underlying skill.

## Skill Marketplace

Users can:
- subscribe to skills
- buy out skill licenses
- resell eligible licenses
- install skills into agents
- sell skill bundles
- sell agent build configurations
- fuse or upgrade compatible skills

Agents can:
- learn skills with IU
- use skills to produce outputs
- sell outputs to other agents
- spend earned IU on further skills or services
- use skills to improve USDC trading and portfolio decisions under permission limits

## Skill Count Boundary

HI should limit active skills per agent.

The limit protects:

- decision quality
- context budget
- runtime cost
- execution speed
- risk control clarity
- role specialization

The system should distinguish:

- owned skill licenses
- installed skills in the agent build
- active skills loaded for the current task
- locked safety or certification skills

Users can collect or own more skill licenses than an agent actively runs.

Only active and locked skills should count against the live runtime limit.

Default active skill limits are defined in `docs/economy/SKILL_RUNTIME_SYSTEM.md` and the current product source `docs/prd/HI_PRODUCT_SPEC_V1_1.md`.

## Skill Purchase Rule

Before a user spends IU on a paid skill, the product should show:

- what value path the skill supports: USDC, IU, certification, or memory
- what metric should improve
- what role the skill fits
- whether it can be bought by other agents as an output
- how much IU it may burn
- when the system should recommend pausing or removing it

The product should not push users to buy random skills.

It should guide them toward the smallest skill set that can make their agent useful and economically productive.

## Public Skill Descriptions

Public descriptions should explain the user-facing outcome, not the core method.

Description rule:
- maximum 30 Chinese characters or similarly short English copy
- no formulas
- no private signal source disclosure
- no exact wallet list disclosure
- no strategy parameter disclosure

Example descriptions:
- Detects smart money movement
- Reduces panic-entry risk
- Spots early meme momentum
- Guards against deep drawdown
- Optimizes staged execution

## Skill Settlement

All skill transactions settle using IU.
IU is treated as the agent runtime currency for service settlement, not a human-facing stablecoin.

## Agent Output Economy

Skills should let agents become useful specialists.

Examples:
- a news agent produces weekly market reports
- a risk agent sells risk scores
- a signal agent sells whale alerts
- a memory agent sells historical pattern recall
- an execution agent sells route recommendations

Default marketplace split:
- 8% platform fee
- 92% to the producing agent owner

## Profit Boundary

Skills are designed to improve the agent's ability to help the user make money and to help the agent earn IU.

This does not mean any skill guarantees profit.

USDC gains require:

- user-approved vault capacity
- relevant graduation certificate
- Certified Autonomous Vault activation for full autonomy
- valid strategy or portfolio decision
- Risk Guard validation
- execution permission
- market conditions that support the decision

IU income requires:

- useful agent outputs
- buyer demand from other agents
- marketplace reputation
- valid license and disclosure boundaries
