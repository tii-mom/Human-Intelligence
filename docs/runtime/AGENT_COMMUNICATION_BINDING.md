# Agent Communication Binding

## Purpose

Every claimed or purchased HI agent must bind at least one communication channel before becoming active.

The required channels are:

- Telegram
- WeChat

The user can bind either one.

The user can bind both and choose one primary channel.

## Product Rule

Wallet or account login proves ownership.

Telegram or WeChat provides the daily agent relationship.

After the user creates or claims an agent:

1. User names the agent.
2. Backend creates the agent core documents.
3. User binds Telegram or WeChat.
4. Agent sends a first greeting in the bound channel.
5. Agent becomes active.

An unbound agent can exist as a claimed asset, but it should not enter active daily operation, scheduled reporting, or command mode.

## Why Binding Is Required

HI agents are not passive dashboard cards.

They need a persistent conversation surface for:

- real-time market updates
- agent status
- skill learning reports
- risk warnings
- IU budget alerts
- USDC vault updates
- graduation progress
- service income
- user instructions
- daily conversation

The chat channel is the agent's living interface.

## Communication Document

Each agent should include `COMMUNICATION.md` in its core document workspace.

This file stores communication policy, not raw private messages.

Required fields:

```yaml
communication_required: true
primary_channel: telegram | wechat | none
bound_channels:
  telegram:
    enabled: false
    external_user_ref: null
    chat_ref: null
    verified_at: null
  wechat:
    enabled: false
    openid_ref: null
    unionid_ref: null
    verified_at: null
notification_level: normal
quiet_hours: null
command_mode: enabled
allowed_command_classes:
  - status
  - report
  - instruction
  - skill
  - risk
  - vault_status
```

Sensitive external identifiers should be stored as encrypted values or references.

Do not expose raw Telegram ids, WeChat OpenIDs, UnionIDs, or webhook secrets in public agent documents.

## Binding Flow

### Step 1 - Create Binding Session

Backend creates:

```json
{
  "bindingSessionId": "bind_...",
  "agentId": "agt_...",
  "ownerId": "usr_...",
  "channel": "telegram",
  "nonce": "one_time_nonce",
  "expiresAt": "ISO-8601"
}
```

The nonce should expire quickly.

Recommended TTL: 10 minutes.

### Step 2 - User Opens Channel Link

Telegram:

- show a deep link to the HI bot
- pass the binding nonce in the start payload
- receive the user's Telegram id and chat id through the bot webhook

WeChat:

- show a QR code or Mini Program link
- user follows the Official Account or opens the Mini Program
- backend receives OpenID and UnionID where available
- backend maps the binding nonce to the HI account

### Step 3 - Verify Account Match

The backend must verify:

- binding session is valid
- nonce is unused
- channel account is not already bound to a conflicting HI user
- requester owns the agent
- user has an active login session

### Step 4 - Write Binding

On success:

- update `COMMUNICATION.md`
- update `STATE.json`
- update the Agent Durable Object state
- update D1 communication indexes
- send first agent greeting
- activate chat command mode

## First Greeting

The first greeting should be short and useful.

It should include:

- agent name
- current role
- current level
- starter skills
- next recommended action
- how to ask for status

Example:

```text
I am Atlas, your blank agent. I am currently Level 0 with starter research skills.
Ask me "status" to see my current state, or "next skill" to see what I should learn first.
```

## Multi-Agent Users

A user can own multiple agents.

The chat interface must support:

- active agent selection
- switching agent by name
- listing all agents
- routing commands to the correct agent
- preventing accidental commands to the wrong agent

Recommended commands:

```text
/agents
/use Atlas
/status
/report
/next_skill
```

Natural language should also work:

```text
Switch to Atlas.
Show me Luna's risk report.
What did my news agent find today?
```

## Telegram Channel

Telegram should support:

- bot deep-link binding
- webhook message ingestion
- inline buttons for safe confirmations
- slash commands
- natural language commands
- agent reports
- urgent risk alerts
- IU budget alerts
- USDC vault status alerts

Telegram is the best first channel for fast global MVP delivery.

## WeChat Channel

WeChat should support:

- Official Account binding
- Mini Program binding
- QR code binding
- plain-language chat commands
- report delivery
- risk and vault notifications within platform rules

WeChat should be treated as a high-priority channel for Chinese users.

Product caveat:

WeChat push and proactive messaging must follow WeChat platform rules.

When push restrictions apply, the product should use:

- WeChat Official Account conversation
- Mini Program subscription messages
- in-app inbox
- daily report digest
- user-pulled status commands

## Notification Levels

Users should choose:

```yaml
quiet:
  - daily digest
  - risk critical only

normal:
  - daily digest
  - important skill events
  - risk warnings
  - vault changes

active:
  - market alerts
  - agent reasoning updates
  - skill learning progress
  - service purchases
  - IU budget events
  - vault events
```

## Security Rules

- Only bound channel accounts can send commands to an agent.
- High-risk commands must pass the permission system.
- Commands that change vault capacity require explicit app or wallet confirmation.
- Commands that affect HI purchases, limited agents, or resale require account confirmation.
- Commands that spend IU above the daily cap require confirmation.
- Chat messages must be archived and compressed under the memory pipeline.
- Channel binding changes must create timeline events.
- Unbinding the primary channel should pause daily operation until another channel is active.

## Autonomy Boundary

Once a Certified Autonomous Vault is active, the user should not interrupt normal trading through chat.

Allowed chat actions during active certified execution:

- ask for status
- ask for explanation
- change future mandate after current cycle
- adjust pre-approved risk lines where supported
- trigger safe mode if the user-defined emergency condition is reached

Disallowed chat actions:

- force an arbitrary trade outside certificate scope
- bypass Risk Guard
- override the graduation certificate
- withdraw from the agent's control without following vault rules

## MVP Requirement

MVP must include:

1. Telegram binding.
2. WeChat binding placeholder or QR-code waitlist if full WeChat approval is not ready.
3. `COMMUNICATION.md`.
4. Bound-channel command verification.
5. `/status`, `/report`, `/skills`, `/risk`, `/memory`, `/help`.
6. Agent first greeting.
7. Notification preference selection.
