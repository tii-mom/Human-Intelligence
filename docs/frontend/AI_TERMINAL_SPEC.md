# AI Terminal Specification

## Purpose
The AI Terminal is the operational view of the user's owned agent.

It should show the agent as a growing financial operator, not as a generic trading dashboard.

## Layout
LEFT:
- AI reasoning stream
- AI timeline
- agent growth feed

CENTER:
- active agent
- installed skill loadout
- consensus engine
- market state

RIGHT:
- risk engine
- AI memory
- execution layer
- license and permission status
- graduation certificate status
- IU activation and settlement state
- Compute Token runtime budget
- USDC vault capacity
- Certified Autonomous Vault status

## Core Experience
The terminal must feel alive even without user interaction.

The same operational state must be available through Telegram or WeChat after the user binds a channel.

For V1.2, the terminal should default to a simpler robot cultivation view.

Advanced trading and runtime details should be one level deeper.

## Live Systems
- AI reasoning
- consensus voting
- autonomous scanning
- confidence visualization
- memory recall
- skill activation status
- agent growth events

## Required Concepts
- active agent role
- bound communication channel
- active chat agent
- installed skills
- current mode: simulation, analysis, advisory, reporting, or execution-limited
- current autonomy mode: manual, semi-auto, certified auto, or professional auto
- service subscriptions bought by the agent
- outputs produced by the agent
- permission level
- Risk Guard state
- graduation certificate scope
- IU activation and settlement state
- USDC trading capacity
- Certified Autonomous Vault PnL
- growth stage
- Compute Token balance
- next evolution requirement
- active task thread, if any
- Master Brain assignment, if any

## Master Brain Workroom

When a user has more than 5 active working robots, the terminal should show a Master Brain workroom:

- user goal
- active task threads
- worker agents
- status per thread
- Compute Token budget usage
- blockers
- risk checks
- next report time

Worker agents should roll up status through the Master Brain by default.

## Chat Command Panel
The terminal should mirror the chat command center.

Users should be able to:

- view the bound Telegram or WeChat channel
- bind or rebind a channel
- switch active agent
- see recent chat commands
- see pending confirmations
- send a command from the web chat box
- open the same thread in Telegram or WeChat

High-risk actions should show the same confirmation state across web, Telegram, and WeChat.

## UX Boundary
The terminal should hide low-level chain complexity.

Users should understand:

- what their agent is doing
- what service it wants to buy
- what budget it will spend
- what risk limit applies
- what requires user approval
- whether the agent is fully operating a certified vault

Users should not be forced to learn DEX, gas, or settlement mechanics to operate the product.
