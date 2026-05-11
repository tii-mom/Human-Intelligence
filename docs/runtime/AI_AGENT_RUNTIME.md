# AI Agent Runtime

## Purpose
Define the lifecycle and operational runtime of user-owned AI agents.

## Core Systems
- Agent lifecycle
- Agent core document workspace
- Communication binding
- Blank agent activation
- Scheduling engine
- Consensus participation
- Skill loading
- Skill permission checks
- Memory persistence
- Risk authority
- Execution permissions
- IU activation and service settlement
- Compute Token runtime budget
- USDC vault capacity
- Agent output production
- Agent output consumption

## Goal
Agents must behave as user-owned autonomous entities that become capable through installed skills.

## Lifecycle
- Claimed
- Blank
- Named
- Core Documents Created
- Communication Channel Bound
- Configured
- Active
- Learning
- Producing Output
- Buying Services
- Listed
- Transferred

## Runtime Rule
The runtime should evaluate the agent's active skill loadout before any autonomous action.

Every agent must load from its core document workspace:

- identity
- soul
- mandate
- skills
- communication
- memory
- risk, when money or permissions are involved
- scorecard, when graduation, vault capacity, or marketplace reputation is involved

The user-facing creation flow should only ask for the agent name and simple choices.

The backend should create and maintain the underlying documents automatically.

An agent must bind Telegram or WeChat before active daily operation.

The communication channel is where the agent sends real-time information and receives user instructions.

## Budget Rule
The runtime must separate:
- IU spending for activation, skill access, service settlement, and agent-to-agent purchases
- Compute Token spending for model calls, API calls, memory jobs, tasks, self-learning, evolution, and skill generation
- USDC vault capacity for trading or portfolio actions

An agent can recommend higher budgets, but user approval and risk checks are required before increasing vault capacity or certificate scope.

After graduation and Certified Autonomous Vault activation, the agent can operate inside that approved scope without per-action approval.

## Memory Rule
The runtime must not place full conversation history into every model call.

It should assemble context from:

- core documents
- hot summary
- recent messages
- relevant semantic memories
- current task data
- risk and scorecard snapshots when needed

Raw conversations remain archived in long-term storage and are used for rebuilds, audits, and deep reviews.

## Command Rule
All Telegram, WeChat, and in-app messages should route through the Agent Chat Command Gateway.

The gateway must:

- verify the bound channel
- resolve the user and active agent
- classify the command
- check permission and risk level
- assemble safe context
- log command events
- archive messages into memory

Chat text is an instruction surface, not direct permission to bypass skill, vault, risk, or certificate rules.
