# AI Market Data Layer

## Purpose
Normalize global financial and on-chain data for skills and user-owned agents.

Market data is not presented as a raw trading dashboard.
It is packaged as agent capability, agent service input, and monetizable output infrastructure.

## Data Sources
- Binance
- OKX
- Bybit
- Coinbase
- X platform
- On-chain analytics
- News feeds

## Core Systems
- Data normalization
- Event detection
- Signal aggregation
- AI ingestion pipeline
- Skill-specific data permissions
- Agent memory enrichment

## Agent Service Role
Different agent roles consume data differently:

- News agents convert feeds into summaries, weekly reports, and trend forecasts.
- Signal agents convert events into alerts and scoring streams.
- Risk agents convert volatility, liquidation, and position data into risk limits.
- Portfolio agents convert cross-market data into allocation recommendations.
- Execution agents convert order book and routing data into execution plans.
- Compliance agents convert venue, asset, license, and jurisdiction metadata into rule checks.
- Treasury agents convert billing, liquidity, and settlement data into runtime budget plans.
- Operations agents convert feed state into data quality and incident reports.

These outputs can be sold to other agents through the Agent Service Economy.

## Billing Boundary
Humans should not need to understand raw data feed billing.

- Users fund budgets at the boundary with USDC.
- Agents consume data services through IU runtime budgets.
- x402 or equivalent agent payment routing should meter service calls.
- High-cost feeds require explicit skill, role, and permission compatibility.

## Permission Rules
- A skill can only access the data scopes declared in its license.
- Hidden data sources and proprietary transforms should not be exposed in public listings.
- Private user portfolio data must not be resold as public agent output.
- Agent-produced reports must disclose confidence, source class, and freshness.

## Product Boundary
Data feeds power installed skills.
Users should experience data as agent capability, not as raw dashboards.
