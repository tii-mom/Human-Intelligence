# Agent Role System

## V1.1 Source

The complete v1.1 role map, role type classification, and `hi` / `hi-core` integration contract are defined in `docs/prd/HI_PRODUCT_SPEC_V1_1.md`.

## Purpose

Define the complete financial role system for HI agents by mapping human financial institution jobs into specialized agent roles.

The role system turns a blank agent from a generic assistant into a professional financial worker.

## Core Principle

Human finance has jobs.
HI turns those jobs into trainable, ownable, composable agents.

An agent role defines:

- what the agent observes
- what skills it should learn
- what outputs it can produce
- what services it can buy
- what services it can sell
- what permissions it can request
- what risk boundaries apply

The detailed skill map for each role is defined in `docs/skills/ROLE_BASED_SKILL_TAXONOMY.md`.

## Role Families

HI agents should be organized into ten role families:

1. Intelligence and research
2. Alpha and strategy
3. Portfolio management
4. Trading and execution
5. Risk management
6. Compliance and control
7. Treasury and settlement
8. Operations and data
9. Client and reporting
10. Marketplace and governance

## Human Role Mapping

| Human financial role | HI agent role | Primary output | Default permission |
| --- | --- | --- | --- |
| Economist | Macro Research Agent | Macro regime brief | Observe |
| News analyst | News Intelligence Agent | News summary, event impact | Observe |
| Equity or protocol analyst | Asset Research Agent | Asset thesis, valuation note | Observe |
| On-chain analyst | On-chain Intelligence Agent | Wallet flow, protocol activity report | Observe |
| Sentiment analyst | Sentiment Agent | Social mood score, narrative map | Observe |
| Quant researcher | Quant Research Agent | Factor, backtest, model insight | Observe / Suggest |
| Strategist | Strategy Architect Agent | Strategy template, thesis | Suggest |
| Signal analyst | Signal Agent | Signal stream, alert score | Suggest |
| Portfolio manager | Portfolio Manager Agent | Allocation, rebalance plan | Suggest / Execution request |
| Investment committee | Consensus Agent | Multi-agent decision summary | Suggest |
| Trader | Trader Agent | Trade plan, order intent | Execution request |
| Execution trader | Execution Agent | Route, TWAP, slippage plan | Execution request |
| Market maker | Liquidity Agent | Spread, inventory, liquidity report | Execution request |
| Arbitrage trader | Arbitrage Agent | Cross-venue opportunity | Execution request |
| Risk manager | Risk Manager Agent | Risk score, veto, limit recommendation | Control |
| Credit or counterparty analyst | Counterparty Risk Agent | Venue, protocol, counterparty risk | Control |
| Compliance officer | Compliance Agent | Rule check, restriction status | Control |
| Internal auditor | Audit Agent | Audit log, anomaly report | Control |
| Treasury manager | Treasury Agent | Budget, liquidity, settlement plan | Suggest / Control |
| Operations analyst | Operations Agent | Reconciliation, status, task completion | Observe |
| Data engineer | Data Operations Agent | Clean data feed, normalization report | Service |
| Client advisor | Advisor Agent | User-facing explanation, education | Observe / Suggest |
| Performance analyst | Performance Attribution Agent | PnL attribution, skill impact | Observe |
| Product manager | Build Curator Agent | Build template, skill bundle | Service |
| Marketplace analyst | Reputation Analyst Agent | Provider score, service ranking | Observe / Service |
| Governance delegate | Governance Agent | Proposal summary, voting brief | Suggest |

## Role Family Details

### 1. Intelligence and Research Agents

These agents collect, interpret, and package information.
They do not execute trades by default.

Roles:

- Macro Research Agent
- News Intelligence Agent
- Asset Research Agent
- On-chain Intelligence Agent
- Sentiment Agent
- Event Analyst Agent
- Narrative Analyst Agent

Typical skills:

- news ingestion
- source ranking
- macro calendar interpretation
- on-chain flow detection
- social sentiment analysis
- asset thesis writing
- event impact scoring

Sellable outputs:

- daily news brief
- weekly market report
- macro regime report
- on-chain wallet flow alert
- narrative heatmap
- asset research memo

Default permissions:

- observe
- report
- sell outputs
- request data services

Research agents should not receive execution authority unless they evolve into another role.

### 2. Alpha and Strategy Agents

These agents transform information into tradeable ideas, models, and strategy templates.

Roles:

- Quant Research Agent
- Strategy Architect Agent
- Signal Agent
- Backtest Agent
- Factor Discovery Agent
- Scenario Simulation Agent

Typical skills:

- signal generation
- factor testing
- backtesting
- scenario simulation
- strategy scoring
- regime classification
- alpha decay detection

Sellable outputs:

- signal stream
- strategy template
- backtest report
- factor pack
- market scenario map
- trading thesis

Default permissions:

- observe
- suggest
- sell outputs
- request consensus

Alpha agents can recommend actions, but execution requires Trader, Portfolio, Execution, or user-approved permissions.

### 3. Portfolio Management Agents

These agents manage the relationship between user goals, risk budgets, and allocation decisions.

Roles:

- Portfolio Manager Agent
- Asset Allocation Agent
- Rebalance Agent
- Position Sizing Agent
- Performance Attribution Agent
- Mandate Manager Agent

Typical skills:

- allocation planning
- risk budgeting
- rebalance logic
- exposure tracking
- performance attribution
- mandate compliance
- drawdown analysis

Sellable outputs:

- model portfolio
- rebalance plan
- allocation template
- portfolio review
- skill impact report
- performance attribution report

Default permissions:

- suggest
- request execution
- manage approved vault capacity only when explicitly permitted

Portfolio agents should be the main user-facing investment operating role.
They coordinate research, signals, risk, and execution services.

### 4. Trading and Execution Agents

These agents convert approved decisions into executable order plans.

Roles:

- Trader Agent
- Execution Agent
- Liquidity Agent
- Market Making Agent
- Arbitrage Agent
- Routing Agent
- MEV Protection Agent

Typical skills:

- order staging
- route selection
- TWAP
- VWAP
- slippage control
- venue selection
- MEV protection
- execution quality analysis

Sellable outputs:

- execution route
- venue recommendation
- liquidity report
- slippage estimate
- arbitrage opportunity alert
- execution quality report

Default permissions:

- execution request
- limited execution only after user approval, vault capacity, and Risk Guard validation

Trading agents must never bypass portfolio limits, user permissions, or risk vetoes.

### 5. Risk Management Agents

These agents protect the system, the user, and other agents from unsafe decisions.

Roles:

- Risk Manager Agent
- Drawdown Guard Agent
- Leverage Control Agent
- Stress Test Agent
- Counterparty Risk Agent
- Protocol Risk Agent
- Liquidation Risk Agent
- Black Swan Agent

Typical skills:

- volatility modeling
- liquidation monitoring
- drawdown detection
- stress testing
- counterparty scoring
- protocol risk analysis
- leverage control
- emergency shutdown

Sellable outputs:

- risk score
- drawdown warning
- stress test report
- venue risk rating
- protocol risk rating
- liquidation risk map

Default permissions:

- control
- veto
- restrict
- require user approval

Risk agents should have higher authority than strategy, portfolio, and execution agents.

### 6. Compliance and Control Agents

These agents enforce rules, licenses, permissions, and product safety boundaries.

Roles:

- Compliance Agent
- Permission Agent
- License Control Agent
- Audit Agent
- Policy Agent
- Suitability Guard Agent

Typical skills:

- skill license validation
- permission checking
- audit log review
- user risk profile review
- jurisdiction rule tagging
- restricted action detection
- disclosure generation

Sellable outputs:

- compliance check
- license health report
- permission review
- audit report
- restricted action alert

Default permissions:

- control
- block
- audit
- require disclosure

Compliance agents protect the marketplace from hidden logic abuse, unauthorized skills, and unsafe execution flows.

### 7. Treasury and Settlement Agents

These agents manage budgets, runtime spending, and settlement accounting.

Roles:

- Treasury Agent
- Runtime Budget Agent
- Billing Agent
- Settlement Agent
- Revenue Split Agent
- Fee Accounting Agent

Typical skills:

- IU service budget planning
- Compute Token budget planning
- service cost estimation
- x402 billing monitoring
- marketplace fee calculation
- revenue split accounting
- owner settlement preparation
- budget anomaly detection

Sellable outputs:

- runtime cost report
- service budget recommendation
- settlement summary
- revenue split report
- subscription efficiency report

Default permissions:

- observe
- suggest
- control budget caps

Treasury agents cannot increase USDC trading capacity without explicit user approval.

### 8. Operations and Data Agents

These agents keep the system reliable by managing data quality, task execution, and infrastructure state.

Roles:

- Data Operations Agent
- Feed Quality Agent
- Reconciliation Agent
- Task Operations Agent
- Monitoring Agent
- Incident Response Agent

Typical skills:

- data normalization
- feed validation
- reconciliation
- anomaly detection
- task routing
- uptime monitoring
- incident reporting

Sellable outputs:

- normalized data feed
- feed quality score
- reconciliation report
- system incident report
- data freshness signal

Default permissions:

- observe
- service
- alert

Operations agents support other agents but should not make investment decisions by default.

### 9. Client and Reporting Agents

These agents translate complex agent activity into user-readable communication.

Roles:

- Advisor Agent
- Reporting Agent
- Education Agent
- Portfolio Explanation Agent
- Voice Briefing Agent
- Telegram Companion Agent

Typical skills:

- explanation generation
- report writing
- education
- risk translation
- multilingual localization
- voice reporting
- Telegram conversation

Sellable outputs:

- user briefing
- weekly portfolio report
- risk explanation
- education module
- voice market briefing

Default permissions:

- observe
- explain
- suggest

Client agents should never pressure the user to approve spending, increase vault capacity, or ignore risk.

### 10. Marketplace and Governance Agents

These agents support the agent economy, creator economy, and protocol governance.

Roles:

- Skill Curator Agent
- Build Curator Agent
- Reputation Analyst Agent
- Dispute Review Agent
- Governance Agent
- Agent Guild Coordinator

Typical skills:

- marketplace ranking
- skill curation
- build comparison
- reputation analysis
- dispute review
- governance proposal summarization
- guild coordination

Sellable outputs:

- marketplace ranking
- skill bundle recommendation
- build review
- provider reputation report
- dispute evidence summary
- governance voting brief

Default permissions:

- observe
- service
- suggest

Governance agents can help humans understand decisions, but humans remain the governance authority through HI.

## Role Permissions

Agent roles should map to permission classes:

| Permission class | Allowed by default | Example roles |
| --- | --- | --- |
| Observe | Read public data, produce reports | News, Macro, Reporting |
| Suggest | Recommend actions, request consensus | Strategy, Portfolio, Advisor |
| Service | Sell outputs to other agents | News, Memory, Risk, Data Ops |
| Control | Block, audit, veto, enforce policy | Risk, Compliance, Permission |
| Execution Request | Stage action for approval | Trader, Execution, Rebalance |
| Certified Vault Autonomy | Fully operate a user-funded certified vault | Portfolio, Trader, Execution |

No role should receive primary wallet authority.

Full autonomous execution is allowed only inside a Certified Autonomous Vault after graduation, user funding, certificate binding, skill compatibility, and Risk Guard monitoring.

## Agent-to-Agent Workflows

### Portfolio Workflow

1. News Agent sells a weekly market report.
2. Macro Agent sells a regime score.
3. Signal Agent sells an alert stream.
4. Risk Agent sells a risk score.
5. Portfolio Manager Agent buys these services with IU.
6. Portfolio Manager Agent proposes a rebalance.
7. Risk Manager Agent approves or vetoes.
8. Execution Agent stages an order route.
9. User permissions and vault limits decide whether execution can happen.

### Research Workflow

1. Data Operations Agent provides clean market data.
2. Quant Research Agent runs a factor test.
3. Backtest Agent validates historical behavior.
4. Strategy Architect Agent packages a strategy template.
5. Build Curator Agent turns the template into an agent build.
6. Other users can install or buy the build under license rules.

### Service Workflow

1. A specialized agent produces an output.
2. Another agent buys that output with IU.
3. The platform takes the defined fee.
4. The producing agent owner receives the economic benefit through official settlement.

Default marketplace split:

- 8% platform fee
- 92% to the producing agent owner

## Role Growth

A blank agent can specialize gradually:

- Level 0: blank agent
- Level 1: trainee analyst
- Level 2: specialist agent
- Level 3: service-producing agent
- Level 4: certified autonomous vault agent
- Level 5: professional agent with marketplace reputation, bonding, audits, and larger limits

Role growth should depend on:

- installed skills
- output quality
- memory depth
- risk discipline
- service buyer retention
- reputation
- audit status
- optional HI bonding

## Product Rules

- Every agent should have one primary role and optional secondary roles.
- Role determines default skill slots and service categories.
- Role determines the recommended skill path for earning USDC and IU.
- Role does not automatically grant execution authority.
- Graduation can grant certified vault autonomy for compatible roles.
- Role change should be recorded in agent memory and identity history.
- Limited agents can have role bias, but not permission bypass.
- Professional service agents should be discoverable by role in the marketplace.
- Users should understand roles in human terms, not protocol terms.
