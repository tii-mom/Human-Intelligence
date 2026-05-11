# Risk Engine UI

## Purpose
Protect users from catastrophic market conditions.

The risk engine is the visible face of the protocol's permission model.
It protects USDC vault capacity, IU runtime spending, skill behavior, certificate scope, and emergency shutdown.

## Core Systems
- Drawdown protection
- Leverage controls
- Black swan detection
- Emergency shutdown
- AI veto authority
- Skill-level risk limits
- Agent build risk summary

## Visible Risk Fields
- current agent mode
- allowed instruments
- max position size
- max daily loss
- max drawdown
- max leverage
- IU runtime budget cap
- USDC vault capacity
- graduation certificate scope
- autonomous vault mode
- blocked skills or expired licenses
- pending user approvals

## UX Principles
Risk visibility must always remain clear and understandable.

## Authority
Risk AI has the highest execution authority.

Risk AI can block execution, block service purchases, restrict skill usage, trigger safe mode, and require new user approval when a certified vault exceeds its mandate.

Risk AI should not interrupt normal autonomous operation when the graduated agent acts inside certificate scope.
