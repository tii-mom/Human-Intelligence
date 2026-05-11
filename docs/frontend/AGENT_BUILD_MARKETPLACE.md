# Agent Build Marketplace

## Purpose
Allow users to discover, buy, sell, and reuse agent builds.

## Core Features
- Build listings
- Mature agent listings
- Skill loadout previews
- Reputation rankings
- Risk visibility
- License availability checks
- Transferable agent ownership

## Build Definition
A build is a saved skill loadout, risk profile, and setup pattern for an agent.

Builds can be sold without exposing hidden skill mechanisms.

## Listing Types
- Blank-agent build template
- Limited-agent optimized build
- Limited drop listing
- Unrevealed limited agent listing
- Role-specific build
- Mature agent resale listing
- Service-producing agent listing
- Skill bundle listing
- Fund-eligible agent listing
- Copy-pool agent listing

## Required Listing Fields
- rarity
- edition number, if limited
- reveal status
- drop collection
- attribute profile
- Growth Potential
- top two attributes
- target agent role
- role family
- primary and secondary role compatibility
- required skills
- USDC value path
- IU income path
- license transfer status
- IU operating cost estimate
- required risk profile
- recommended vault capacity
- return rate
- max drawdown
- win rate
- profit share rate, if fund or copy-pool enabled
- HI bonding requirement, if any
- historical performance or output quality
- reputation and ownership history
- hidden logic disclosure boundary

## Limited Drop Fields

Limited agent listings should show:

- total supply
- remaining supply
- price in HI
- rarity table
- S and S+ guarantee
- reveal countdown
- resale eligibility
- edition range
- collection theme

## Marketplace Rule
Buying a build does not automatically grant unavailable, expired, or non-transferable skill licenses.

Buying a mature agent does not transfer private owner memory, private wallet permissions, or USDC vault funds unless explicitly supported by a separate permission flow.

## Economic Boundary
- Limited agents are purchased with HI.
- Skills, services, and agent outputs are consumed by agents with IU.
- Fund or copy-pool access can require HI bonding.
- High-performing agents can charge 5% to 20% performance fee on profits.
- Human owner settlement should happen through official protocol paths.

## UX Goal
The marketplace should feel like buying proven agent configurations, not renting a black-box trader.
