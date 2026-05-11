# Wallet Security System

## Architecture
- User wallet
- Agent ownership record
- Skill license records
- Trading sub-wallet
- Vault contract
- Execution account
- Permission manager
- Risk guard

## Security Features
- Permission isolation
- Withdrawal protection
- Session validation
- Emergency freeze
- Multi-layer authorization
- Skill license validation
- Agent transfer protection
- Budget caps
- Vault capacity limits

## Goal
Users retain ownership while enabling AI automation.

## Ownership Separation
Agent ownership, skill license rights, and execution permissions must remain separate.

Selling an agent should not transfer private wallet permissions or user funds.

## Agent Vault Model

Users deposit USDC into controlled agent vaults.

Agents can fully operate a dedicated vault only after graduation and user activation.

Certified vault operation stays within:
- user permissions
- vault limits
- graduation certificate scope
- skill permission classes
- risk guard constraints
- venue and asset whitelists

Agents should never receive direct control over the user's primary wallet.

## Certified Autonomous Vault

A Certified Autonomous Vault is a user-funded vault assigned to a graduated agent.

The agent can autonomously:

- open and close positions
- rebalance
- manage stops
- manage leverage within certificate scope
- route orders through approved venues

The agent cannot:

- withdraw to arbitrary wallets
- access the user's primary wallet
- increase vault capacity by itself
- change ownership
- bypass emergency shutdown

## Settlement Boundary

Humans use USDC for deposits and owner settlement.
Agents use IU for runtime services.

Agent-earned IU should be accounted by the protocol and claimable by the owner through an official USDC settlement path.
