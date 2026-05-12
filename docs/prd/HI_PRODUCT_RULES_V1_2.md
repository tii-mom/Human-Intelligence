# HI Product Rules v1.2

## Purpose

This is the short source document for the V1.2 product rules.

Use this when a team member needs the simple answer before opening the detailed specs.

Detailed references:

- `docs/prd/HI_PRODUCT_SPEC_V1_2.md`
- `MVP_PRODUCT_SPEC.md`
- `docs/prd/HI_PRODUCT_SPEC_V1_1.md`

## Core Promise

Users spend HI and IU to cultivate robots that can create measurable value.

Value means:

- better USDC outcomes inside approved vault limits
- lower avoidable losses
- useful research, signal, risk, execution, memory, or reporting output
- IU service income
- stronger certification readiness
- higher agent reputation and resale value

If a feature does not help one of these paths, it is secondary.

## User Ownership Rules

- One user can claim only one free Blank Robot.
- The free robot starts weak and cannot make live money by default.
- Users can own unlimited limited robots.
- Limited robots are bought with HI.
- Limited robots start sealed or dormant.
- IU awakening reveals full limited-robot stats.
- Limited robots do not guarantee profit and do not bypass risk, vault, or graduation rules.

## Runtime Economy Rules

- IU is the activation, conversion, and settlement unit.
- Compute Tokens are the robot's metered work fuel.
- Default conversion: `1 IU = 10,000,000 Compute Tokens`.
- Each active robot requires `9.99 IU/month`.
- Daily conversation is included in monthly activation.
- Paid work burns Compute Tokens.

Compute Tokens are used for:

- skill learning
- self-learning
- evolution attempts
- skill-book generation
- model calls
- API calls
- memory jobs
- reports and backtests
- user task execution
- Master Brain orchestration

## Growth Rules

Robots should feel like game pets with financial utility.

Default stages:

- Sealed
- Dormant
- Young
- Trainee
- Specialist
- Trial
- Certified
- Professional
- Master Brain

Evolution requires:

- active monthly activation
- enough Compute Tokens
- role-compatible skills
- useful work or learning evidence
- risk discipline

Spending alone must not guarantee evolution.

## Skill Rules

Skills are skill books or training modules.

User-facing tiers:

- Basic Skill Book
- Advanced Skill Book
- Expert Skill Book

Internal taxonomy remains:

- starter skills
- advanced skills
- certification skills

Agents can own many skills, but only a few can be active at once.

Default active skill slots:

| Stage | Active slots |
| --- | ---: |
| Young | 2 |
| Trainee | 3 |
| Specialist | 4 |
| Trial | 5 |
| Certified | 6 |
| Professional | 8 |
| Master Brain | 10 orchestration slots |

Every paid skill must show a value path:

- make USDC
- reduce loss
- earn IU
- pass certification
- improve memory or adaptation
- coordinate agents

## Skill Book Economy

Platform skills can be fixed official skill books.

Robots can produce user-owned skill books when they have:

- active monthly activation
- enough Compute Tokens
- role-compatible skill path
- useful work evidence
- no private owner data leakage
- no hidden strategy disclosure

Produced skill books enter the user's backpack.

The user can install, hold, or list them.

Default marketplace fee:

- 8% platform fee
- 92% to the producing robot owner

## Work Limit Rules

- One user can have at most 50 working robots at the same time.
- Dormant, sealed, inactive, listed, or held robots do not count.
- Each working robot needs active monthly activation.
- Each working robot needs a Compute Token budget.
- More than 5 working robots requires one Master Brain.
- The Master Brain counts as one working robot.
- The Master Brain can coordinate up to 49 worker robots.

## Master Brain Rules

The Master Brain coordinates work like a team manager.

It should:

- receive user goals
- create task threads
- assign robots
- allocate Compute Token budgets
- track progress
- collect outputs
- ask risk/control agents for checks
- report through Telegram, WeChat, web, or mobile

The Master Brain does not automatically receive trading authority.

If it trades or manages a vault, it must graduate like any other robot.

## Money-Making Rules

Robots should not be money-making by default.

Money-making ability must be earned through:

- skills
- memory
- simulation tasks
- service output quality
- 100 USDC probation vault
- automatic graduation
- risk discipline

Certified agents can fully operate only the USDC the user deliberately deposits into a Certified Autonomous Vault.

The robot never controls the user's primary wallet.

## MVP Scope

The MVP should prove the cultivation loop, not full live autonomous trading.

Must have:

- claim one free robot
- buy or preview limited robots
- awaken limited robot with IU
- name robot
- generate core document pack
- bind Telegram or WeChat
- show monthly activation
- show Compute Token balance
- install starter skills
- run mock tasks
- show memory and scorecard
- show vault preview
- show risk boundary

Should not include:

- live autonomous trading
- uncontrolled wallet access
- open DEX speculation UX
- unlimited active skills
- full fund/copy pool production
- manual graduation review

## Default User Path

```text
Claim or buy robot
  -> name robot
  -> bind Telegram or WeChat
  -> activate for 9.99 IU/month
  -> convert IU into Compute Tokens
  -> learn starter skill
  -> run useful task
  -> build memory and scorecard
  -> evolve
  -> enter Trial
  -> graduate
  -> operate certified vault or sell services
```

