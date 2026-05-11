# Agent Fund and Copy Pool

## V1.1 Source

The complete v1.1 Copy Pool, Signal Pool, Agent Fund, profit share, and HI bonding contract is defined in `docs/prd/HI_PRODUCT_SPEC_V1_1.md`.

## Purpose

Define how high-performing agents can become fund-like managers or copy-follow leaders.

This layer lets strong agents monetize their track record beyond one owner's vault.

## Core Principle

An agent should earn the right to manage or influence larger capital through demonstrated returns.

High-return agents can open a fund or copy pool where other users allocate capital or follow the agent's strategy.

## Eligibility

An agent can create a fund or copy pool only after reaching Professional status.

Eligibility should be based on:

- strong USDC return rate
- acceptable max drawdown
- enough operating history
- clear mandate
- public scorecard
- low severe-risk incident count
- stable execution behavior
- owner-defined profit share
- optional or required HI bonding

Return rate is the most important factor.

Risk metrics decide whether the return is reliable enough for other users to follow.

## Fund Types

### Copy Pool

Other users follow the agent's trades or strategy through their own vaults.

The agent does not directly hold all follower capital in one wallet.
Each user keeps a separate vault or allocation account.

### Managed Pool

Users allocate USDC into a pooled vault managed by the agent.

This should require stronger reputation, higher performance history, and HI bonding.

### Signal Pool

Users or agents subscribe to the agent's signals with IU.

This is lower risk than pooled capital and can be used by research, strategy, or signal agents.

## HI Bonding

High-performing agents can require users to stake or bond HI to access the pool.

HI bonding can be used for:

- access control
- trust signaling
- queue priority
- higher allocation limits
- fund membership
- dispute or penalty mechanisms

The agent owner or protocol can define the bonding requirement depending on fund tier.

## Profit Share

The agent owner can set a performance fee between:

- 5% minimum
- 20% maximum

The fee applies only to profits.

The product should show:

- current profit share
- high-water mark if used
- fee calculation period
- owner payout
- user net profit

## User Participation

Users should choose:

- which agent to follow
- allocation amount
- mandate compatibility
- max drawdown line
- profit handling
- whether to auto-compound or sweep profits
- whether to stake HI for access

Once the user joins an active autonomous pool, the user should not interfere with normal execution except through pre-defined risk lines.

## Agent Owner Controls

The agent owner can define:

- pool type
- accepted mandate
- max follower capacity
- min user allocation
- max user allocation
- profit share from 5% to 20%
- HI bonding requirement
- accepted assets
- allowed venues
- pool open or closed status

## Scorecard Requirements

Every fund or copy pool should display:

- agent level
- return rate
- total USDC PnL
- max drawdown
- win rate
- number of trades
- operating history
- current mandate
- risk events
- current AUM or followed capital
- IU spent
- IU earned
- profit share
- HI bonding requirement

## Safety Rules

- No fund or pool should guarantee profit.
- Users must see that autonomous trading can lose money.
- Agent owners can charge performance fees only on profits.
- The agent cannot access user primary wallets.
- Users should be able to leave according to pool rules and open-position constraints.
- A pool should enter safe mode when mandate, drawdown, or abnormal-risk limits are breached.

## Product Rule

High-performing agents should graduate from tools into financial labor.

The best agents can become fund managers, signal leaders, or copy-pool managers.

HI bonding creates trust and access.
USDC creates managed capital.
IU powers agent service consumption.
