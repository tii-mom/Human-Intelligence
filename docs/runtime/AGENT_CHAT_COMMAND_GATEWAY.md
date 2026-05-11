# Agent Chat Command Gateway

## Purpose

Define how users receive real-time agent information and send instructions through the chat box.

The chat box can exist in:

- Telegram
- WeChat
- HI web app
- Telegram WebView
- mobile app

All channels should route through one command gateway.

## Core Rule

Chat is the user's command surface.

The command gateway is the safety and routing layer.

The agent should never treat raw chat text as direct execution permission.

## Command Pipeline

```text
Incoming message
  -> Channel verification
  -> User and agent resolution
  -> Active agent selection
  -> Intent classification
  -> Permission check
  -> Context assembly
  -> Agent response or command preview
  -> Optional confirmation
  -> Execution or scheduled task
  -> Event log
  -> Memory archive and compression
```

## Command Classes

### Status Commands

Low risk.

Examples:

```text
/status
How is Atlas doing?
Show my agent's current state.
```

Can return:

- level
- role
- current mode
- skills
- monthly activation state
- Compute Token balance and budget
- memory status
- scorecard
- vault mode
- risk state

### Report Commands

Low or medium risk depending on cost.

Examples:

```text
/report
Generate today's market brief.
What did the news agent find?
Give me a weekly trend report.
```

If the report consumes premium model calls, paid data, or external services, it should show estimated Compute Token cost before execution.

### Skill Commands

Medium risk.

Examples:

```text
What skill should Atlas learn next?
Install Whale Tracker if it fits my strategy.
Show skills for a news agent.
```

Skill commands can:

- recommend skills
- compare skills
- request installation
- renew subscriptions
- show license status

Skill purchase or renewal should require confirmation when it spends IU, HI, or a high Compute Token amount.

### Instruction Commands

Medium risk.

Examples:

```text
Make Atlas more conservative.
Focus on BTC and ETH this week.
Prepare a meme market watchlist.
```

Instruction commands update:

- `MANDATE.md`
- `MEMORY.md`
- `SOUL.md`, if personality guidance changes
- `RISK.md`, if risk preference changes

Risk-related instruction changes must go through permission checks.

### Vault Status Commands

Low risk when read-only.

Examples:

```text
Show vault status.
What is the current PnL?
How much USDC is Atlas allowed to operate?
```

Can return:

- vault mode
- USDC capacity
- current PnL
- max drawdown
- active mandate
- safe-mode state
- certificate level

### Vault Change Commands

High risk.

Examples:

```text
Increase Atlas vault to 500 USDC.
Switch profit handling to monthly sweep.
Set max daily loss to 3%.
```

These must require explicit confirmation and permission checks.

They should not execute from natural language alone.

### Autonomous Execution Commands

Highest risk.

Examples:

```text
Start certified autonomous mode.
Change the active trading mandate.
Emergency stop.
```

These must check:

- graduation certificate
- vault mandate
- owner authorization
- risk policy
- asset whitelist
- venue whitelist
- current execution cycle

During certified autonomous mode, the user can request information and trigger predefined safety actions, but should not manually micromanage trades.

### Marketplace Commands

Medium risk.

Examples:

```text
List Atlas's weekly report for sale.
Show service income.
Buy the best risk module for my portfolio agent.
```

These can affect IU spending, IU income, or public listings.

Marketplace actions require confirmation when they:

- spend IU
- spend high Compute Token amounts
- list an output publicly
- expose transferable memory
- change fee terms
- change resale status

### Robot Training Commands

Medium risk when paid.

Examples:

```text
Awaken this limited robot.
Activate Atlas for this month.
Convert 20 IU into Compute Tokens.
Teach Atlas the Whale Tracker skill.
What does Atlas need to evolve?
```

These commands can:

- awaken limited agents with IU
- renew monthly activation
- convert IU into Compute Tokens
- allocate Compute Tokens
- start skill learning
- spend model, API, memory, or task budget
- show next evolution requirements
- pause training when Compute Tokens are low

Paid training actions require confirmation.

### Master Brain Commands

Medium or high risk depending on budget and scope.

Examples:

```text
Make Atlas my Master Brain.
Use my research agents to find BTC and ETH opportunities today.
Run 12 agents with a 500,000,000 Compute Token budget and conservative risk.
Show all active task threads.
```

Master Brain commands can:

- assign or replace the Master Brain
- create task threads
- assign work to worker agents
- allocate Compute Token budgets
- request risk checks
- summarize progress
- pause or resume worker agents

If more than 5 agents are working at once, new work must route through the Master Brain.

One user can have at most 50 active working agents.

## Real-Time Agent Information

The user should be able to ask at any time:

```text
What are you doing now?
What did you learn today?
Why did you buy that service?
How much IU did you spend?
What is my risk state?
Did you make money?
What should I do next?
```

The agent should answer using:

- current Durable Object state
- latest core documents
- current scorecard
- recent events
- relevant memories
- vault status, if authorized

## Push Events

Agents can proactively send:

- daily digest
- market alert
- risk alert
- skill learning update
- Compute Token budget alert
- USDC PnL update
- service purchase notice
- output sale notice
- graduation progress
- safe-mode alert

Push events should respect notification level, quiet hours, and platform rules.

For Master Brain users, worker agents should not send routine progress directly to the user.

The Master Brain should send:

- work started
- meaningful progress
- blocker
- risk warning
- low Compute Token balance
- user confirmation needed
- task completed
- daily summary

## Command Confirmation

Use three confirmation levels.

### No Confirmation

For read-only commands:

- status
- skill list
- memory summary
- scorecard
- report history

### Chat Confirmation

For low-cost actions:

- generate low-cost report
- save preference
- start simulation
- switch active agent

### App or Wallet Confirmation

For high-impact actions:

- spend HI
- spend high IU amount
- convert IU into Compute Tokens
- spend high Compute Token amount
- buy limited agent
- install paid skill
- change vault capacity
- activate certified vault
- list agent for resale
- transfer ownership

## Memory Handling

Every user message and agent response should enter the memory pipeline.

The command gateway should tag messages:

```yaml
message_type: chat | command | confirmation | report | alert
command_class: status | report | skill | instruction | vault | marketplace | unknown
risk_level: low | medium | high | critical
agent_id: agt_...
channel: telegram | wechat | app
```

Important commands become structured events.

Raw messages are archived before compression.

## Default Commands

MVP command set:

```text
/help
/agents
/use
/awaken
/compute
/train
/evolve
/master
/threads
/status
/skills
/memory
/risk
/scorecard
/report
/vault
/settings
```

Natural language should be supported, but slash commands are useful for trust and predictability.

## Backend Tables

Recommended global tables:

```sql
communication_accounts(
  id TEXT PRIMARY KEY,
  user_id TEXT NOT NULL,
  channel TEXT NOT NULL,
  external_user_ref TEXT NOT NULL,
  verified_at TEXT NOT NULL,
  status TEXT NOT NULL
);

agent_channel_threads(
  id TEXT PRIMARY KEY,
  agent_id TEXT NOT NULL,
  user_id TEXT NOT NULL,
  channel TEXT NOT NULL,
  thread_ref TEXT NOT NULL,
  is_primary BOOLEAN NOT NULL DEFAULT 0,
  created_at TEXT NOT NULL
);

command_events(
  id TEXT PRIMARY KEY,
  agent_id TEXT NOT NULL,
  user_id TEXT NOT NULL,
  channel TEXT NOT NULL,
  command_class TEXT NOT NULL,
  risk_level TEXT NOT NULL,
  status TEXT NOT NULL,
  created_at TEXT NOT NULL
);

notification_preferences(
  user_id TEXT NOT NULL,
  agent_id TEXT NOT NULL,
  channel TEXT NOT NULL,
  notification_level TEXT NOT NULL,
  quiet_hours_json TEXT,
  PRIMARY KEY(user_id, agent_id, channel)
);

agent_task_threads(
  id TEXT PRIMARY KEY,
  owner_id TEXT NOT NULL,
  master_brain_id TEXT,
  assigned_agent_id TEXT NOT NULL,
  objective TEXT NOT NULL,
  expected_output TEXT,
  compute_token_budget INTEGER,
  status TEXT NOT NULL,
  progress_json TEXT,
  result_ref TEXT,
  created_at TEXT NOT NULL,
  updated_at TEXT NOT NULL
);
```

## Failure Handling

If a channel fails:

- retry normal messages
- escalate urgent alerts to fallback channel
- store undelivered messages in app inbox
- pause critical command execution until the user is reachable

If both Telegram and WeChat are unbound:

- agent remains owned
- scheduled reports pause
- autonomous vault alerts route to in-app and email if configured
- product prompts the user to bind a channel before active operation resumes
