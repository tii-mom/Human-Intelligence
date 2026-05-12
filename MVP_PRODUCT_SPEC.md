# HI / IU Agent MVP Product Spec

## Purpose

This MVP turns HI into a claim, name, bind, chat, train, and monitor product for user-owned AI trading agents.

The MVP is not a live autonomous trading launch.

The MVP proves the product loop:

1. User claims one free Blank Agent or buys a limited agent with HI.
2. User gives the agent a name.
3. System generates the agent core document workspace.
4. User binds Telegram or WeChat.
5. User activates the agent with 9.99 IU/month or previews activation.
6. User converts IU into Compute Tokens for paid work.
7. Agent sends its first greeting.
8. User chats with the agent and sends commands.
9. Agent installs starter skills, builds memory, and shows a scorecard.
10. User sees risk and vault previews before any real capital authority exists.

## MVP User Flow

### Free Blank Agent

1. User enters HI.
2. User claims one free Blank Agent.
3. User names the agent.
4. System generates the core document pack.
5. User binds Telegram or WeChat.
6. Agent greets the user in the bound channel.
7. Agent starts at Level 0 with starter skills.
8. User can ask for status, skills, memory, risk, report, and vault preview.

### Limited Agent

1. User buys a limited agent with HI.
2. The limited agent starts sealed or dormant.
3. User spends IU to awaken it.
4. Awakening reveals rarity, edition number, personality archetype, role bias, starter advantages, attributes, and Growth Potential.
5. User names the agent.
6. System generates the same core document pack.
7. User binds Telegram or WeChat.
8. Agent greets the user with its limited personality.
9. Limited agents do not bypass graduation, Risk Guard, or Certified Autonomous Vault requirements.

## Required Lifecycle

Every MVP agent should move through this state machine:

```text
claimed
  -> named
  -> documents_created
  -> channel_bound
  -> monthly_activation_ready
  -> compute_tokens_allocated
  -> active
  -> learning
  -> certified
  -> fund_ready
  -> listed
  -> transferred
```

MVP required states:

- `claimed`
- `named`
- `documents_created`
- `channel_bound`
- `monthly_activation_ready`
- `compute_tokens_allocated`
- `active`
- `learning`

Future states:

- `certified`
- `fund_ready`
- `listed`
- `transferred`

## Agent MVP Read Model

The frontend and backend should agree on this minimum shape:

```json
{
  "agentId": "agt_...",
  "displayName": "Atlas",
  "agentType": "free_blank",
  "rarity": "Common",
  "attributes": {
    "alpha": 42,
    "risk": 55,
    "execution": 38,
    "research": 61,
    "memory": 46,
    "charisma": 52,
    "growthPotential": 68
  },
  "primaryRole": "News Intelligence Agent",
  "lifecycleStatus": "active",
  "growthStage": "young",
  "runtime": {
    "state": "preview",
    "monthlyActivationIu": 9.99,
    "monthlyActivationStatus": "inactive",
    "computeTokenBalance": 0,
    "dailyComputeTokenLimit": 0
  },
  "boundChannels": ["telegram"],
  "activeChannel": "telegram",
  "installedSkills": ["Basic News Scanner", "Market Event Calendar", "Risk Guard Lite"],
  "memoryStatus": {
    "hotSummary": "The agent remembers the user's risk preference and current BTC/ETH focus.",
    "lastCompression": "2026-05-11T08:00:00Z",
    "nextCompression": "2026-05-11T16:00:00Z"
  },
  "scorecard": {
    "level": 0,
    "returnRate": "simulation only",
    "maxDrawdown": "not live",
    "winRate": "not live",
    "computeTokensSpent": 0,
    "iuSpent": 0,
    "iuEarned": 0,
    "usdcPnl": 0
  },
  "vaultPreview": {
    "mode": "probation_preview",
    "startingCapacityUsdc": 100,
    "riskGuard": "preview only"
  },
  "certificateStatus": "not_certified"
}
```

## Chat Command Model

All Telegram, WeChat, and web chat messages route through one command gateway.

```json
{
  "commandClass": "status",
  "riskLevel": "low",
  "confirmationRequired": false,
  "channel": "telegram"
}
```

Command classes:

- `status`
- `report`
- `skill`
- `instruction`
- `vault`
- `marketplace`

Risk levels:

- `low`
- `medium`
- `high`
- `critical`

MVP supported commands:

```text
/status
/skills
/memory
/risk
/report
/vault
```

## Core Document Pack

Every named agent receives:

- `IDENTITY.md`
- `SOUL.md`
- `COMMUNICATION.md`
- `MANDATE.md`
- `SKILLS.md`
- `MEMORY.md`
- `RISK.md`
- `SCORECARD.md`
- `SERVICES.md`

MVP stores these as product-visible mock documents and backend docs.

Production should store them through the Cloudflare-backed document workspace described in `docs/runtime/AGENT_CORE_DOCUMENTS.md`.

## Communication Binding

At least one channel is required before active operation:

- Telegram: global first channel
- WeChat: priority channel for Chinese users

Binding is mocked in MVP.

Production binding must verify:

- user ownership
- channel account
- one-time nonce
- active session
- non-conflicting channel identity

## MVP Skill v1

The first skill set should be small and role-based:

| Skill | Role family | Permission | MVP value |
| --- | --- | --- | --- |
| Basic News Scanner | News | Observe | Finds market-moving headlines |
| Market Event Calendar | Research | Observe | Tracks CPI, FOMC, unlocks, exchange events |
| Simple Sentiment Reader | Signal | Observe | Reads social/market mood |
| Risk Guard Lite | Risk | Control | Explains max loss and drawdown boundaries |
| Portfolio Note Writer | Portfolio | Suggest | Creates allocation notes without execution |
| Execution Preview | Execution | Execution Request | Shows a non-live order plan |
| Hot Memory Keeper | Memory | Service | Maintains compact user preference memory |
| Daily Report Writer | Reporting | Service | Produces a daily digest |

Skills can improve:

- user decision quality
- future USDC performance readiness
- agent service output quality
- future IU earning potential

Skills do not guarantee profit.

## Memory MVP

MVP memory should show:

- hot memory summary
- daily summary placeholder
- archived conversation count
- last compression time
- next compression time

Compression policy:

- after 32 chat turns
- after about 12,000 hot tokens
- every 8 active hours
- on important events such as skill install, role change, vault preview, report generation, IU income, or risk warning

MVP does not need real Vectorize retrieval.

It should make the architecture visible without pretending production memory is live.

## Risk and Vault MVP

MVP shows a preview only:

- 100 USDC probation vault capacity
- no real execution
- no primary wallet control
- Risk Guard preview
- certificate status
- safe-mode explanation

Production rule:

An agent can fully operate only the USDC deliberately placed into a Certified Autonomous Vault after graduation and permission binding.

The agent never controls the user's primary wallet.

## IU / HI MVP Boundary

HI:

- human-facing ownership
- limited agent purchase
- premium access
- future bonding
- governance

IU:

- agent runtime settlement
- limited agent awakening
- robot monthly activation
- compute-token conversion
- skill usage
- API access
- service billing
- memory rental
- signal subscription
- execution/risk service purchase

Compute Tokens:

- 1 IU = 10,000,000 Compute Tokens
- robots spend Compute Tokens on model calls, API calls, memory jobs, reports, training, task execution, evolution, and skill-book generation
- daily conversation is included in active monthly activation

MVP may show activation and compute-token budget previews.

MVP must not present IU as a retail speculative asset.

MVP should describe IU simply as the robot activation and settlement unit, and Compute Tokens as the robot's work fuel.

## Not In MVP

- no live autonomous trading
- no real Cloudflare deployment
- no real Telegram or WeChat production app connection
- no live x402 payment settlement
- no open IU DEX speculation
- no agent access to user primary wallet
- no official manual graduation exam
- no full raw conversation prompt stuffing

## Acceptance Criteria

The MVP is acceptable when:

- user can understand the claim/name/bind/train loop
- agent has a visible identity, lifecycle, skills, memory, scorecard, and vault preview
- chat commands return useful mock status
- Telegram and WeChat binding are represented as required activation steps
- frontend remains preview-only where backend is not live
- docs and code agree on HI, IU, agent autonomy, and wallet boundaries
