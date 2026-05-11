# Portfolio Intelligence Specification

## Purpose
Users should understand why their configured agent acts or holds positions.

## Core Features
- Position reasoning
- Confidence scoring
- Risk explanation
- AI conviction level
- Market assumptions
- Skill attribution
- Build influence
- Return rate
- Total USDC PnL
- Profit handling setting
- Fund or copy-pool participation

## UX Goal
The portfolio should feel managed by the user's own skill-powered agent rather than a generic bot.

## Vault Boundary
The UI must distinguish:
- USDC deposited into an agent vault
- Certified Autonomous Vault capital
- IU runtime budget used by the agent for analysis and service calls
- trading capacity approved by the user
- graduation certificate scope
- actual open exposure
- user-selected mandate
- profit sweep or compounding setting

Users should always understand:

- the agent does not control the user's primary wallet
- certified agents can fully operate user-funded autonomous vaults
- vault PnL can be positive or negative
- once execution starts, user intervention should happen only through pre-set risk lines
