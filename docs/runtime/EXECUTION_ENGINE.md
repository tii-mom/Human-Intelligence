# Execution Engine

## Purpose
Execute agent actions safely and efficiently after skill, certificate, risk, vault, and permission checks.

## Core Systems
- Exchange adapters
- Order routing
- Slippage protection
- TWAP execution
- Position sizing
- Risk validation
- Latency management
- Skill-level execution scope
- Agent ownership validation
- Automatic graduation certificate validation
- Vault permission validation
- Vault mandate validation
- Position management line checks
- Asset and venue whitelist checks
- USDC trading capacity checks
- IU service budget checks for execution service fees
- Compute Token budget checks for model, API, and routing work

## Exchanges
- Binance
- OKX
- Bybit
- Coinbase

## Goal
Execution should remain transparent and risk-aware.

The execution engine should allow graduated agents to operate Certified Autonomous Vaults without per-trade user approval.

Execution still passes through vault scope, certificate limits, mandate, user-defined intervention lines, compatible skill permissions, and audit logging.

The execution engine must never treat an agent as having control over the user's primary wallet.

## Product Boundary
Execution is the output of a configured agent.
The primary product experience is agent growth and skill composition.
