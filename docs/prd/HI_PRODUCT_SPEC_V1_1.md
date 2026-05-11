# HI Product Spec v1.1

## Purpose

This is the v1.1 product source document for HI Protocol.

It defines the shared product contract for:

- `hi`: frontend, user surfaces, marketplace, vault UX, agent cards, and read models
- `hi-core`: backend, runtime, agent documents, skill permissions, vault commands, and events

Detailed subsystem documents can expand this spec, but they should not contradict it.

## Core Product Rule

HI is a user-owned financial agent cultivation system.

The product is not a generic copy-trading dashboard, not a black-box bot rental product, and not a promise of yield.

Users own agents, install skills, grow memory, set risk lines, fund dedicated vaults, and decide when an agent is ready for larger capital.

Agents never control the user's primary wallet.

Certified agents can fully operate only the USDC deliberately placed into a Certified Autonomous Vault, and only inside the certificate, mandate, asset, venue, and risk boundaries selected by the user.

## V1.1 Hard Rules

- Every agent has one primary role and optional secondary roles.
- Role defines default skill paths, output markets, permission defaults, and certification tracks.
- Skills define active capabilities and permissions. Attributes do not grant permissions.
- Graduation and certification are automatic system evaluations, not human approvals.
- The initial live trading proving ground is a 100 USDC probation vault.
- Users cannot arbitrarily interrupt a live Certified Autonomous Vault while it is executing unless a pre-set user risk line is triggered.
- High-performing agents can create Copy Pools, Signal Pools, or Agent Funds only after professional eligibility checks.
- Agent memory uses raw archives as source of truth, with hot memory, summaries, and vectors as derived indexes.
- `hi` reads product state from read models. `hi-core` accepts commands, owns validation, emits events, and builds read models.

## 1. Agent Role System v1.1

### Role Type Classification

V1.1 agents must be classified by both financial job role and economic function.

| Type | Chinese label | Primary goal | Typical roles | Can directly touch vault execution |
| --- | --- | --- | --- | --- |
| Money-making | 赚钱型 | Produce USDC returns through portfolio, strategy, or fund work | Portfolio Manager, Signal, Strategy, Trader, Arbitrage, Fund Manager | Yes, after certification |
| Research | 研究型 | Produce information advantage and market understanding | Macro, News, Asset Research, On-chain, Sentiment, Quant Research | No by default |
| Risk | 风控型 | Prevent bad losses, unsafe leverage, and mandate violations | Risk Manager, Drawdown Guard, Stress Test, Counterparty Risk | Control/veto only |
| Execution | 执行型 | Convert approved decisions into high-quality orders | Execution Trader, Routing, TWAP/VWAP, MEV Protection | Yes, after certification or approved request |
| Service | 服务型 | Sell useful outputs to other agents or users | Reporting, Data Ops, Build Curator, Reputation, Compliance | Usually no |
| Memory | 记忆型 | Maintain, compress, retrieve, and package agent memory | Memory Keeper, Market Memory, Vector Memory Curator | No |
| Composite | 组合型 | Coordinate multiple specialist agents into a complete operating unit | CIO Agent, Multi-Agent PM, Agent Fund Manager, Copy Pool Lead | Yes, after higher certification |

### Human Finance Role Mapping

The role map should feel familiar to humans who understand financial institutions.

| Human financial role | HI agent role | Type | Default permission | Primary output | Fund/vault eligibility |
| --- | --- | --- | --- | --- | --- |
| Chief investment officer | CIO Agent | Composite | Suggest / coordinate | Investment policy, agent allocation | Professional only |
| Investment committee | Consensus Agent | Composite | Suggest / challenge | Multi-agent decision memo | Indirect |
| Portfolio manager | Portfolio Manager Agent | Money-making | Suggest / certified autonomy | Allocation, rebalance, mandate execution | Yes |
| Asset allocator | Asset Allocation Agent | Money-making | Suggest | Strategic allocation | Yes with PM track |
| Rebalance manager | Rebalance Agent | Money-making | Execution request | Rebalance plan | Yes with PM track |
| Mandate manager | Mandate Manager Agent | Composite | Control / suggest | Mandate fit check | Yes with PM track |
| Performance analyst | Performance Attribution Agent | Service | Observe / service | PnL and attribution report | Indirect |
| Economist | Macro Research Agent | Research | Observe | Macro regime brief | No |
| Macro strategist | Macro Strategy Agent | Research | Suggest | Regime-to-strategy map | Indirect |
| News analyst | News Intelligence Agent | Research | Observe / service | News brief, event impact | No |
| Asset analyst | Asset Research Agent | Research | Observe / service | Asset thesis, valuation note | No |
| Protocol analyst | Protocol Research Agent | Research | Observe / service | Protocol health report | No |
| On-chain analyst | On-chain Intelligence Agent | Research | Observe / service | Wallet flow, whale alert | No |
| Sentiment analyst | Sentiment Agent | Research | Observe / service | Sentiment score, narrative map | No |
| Event analyst | Event Analyst Agent | Research | Observe / service | Event impact score | No |
| Quant researcher | Quant Research Agent | Research | Observe / suggest | Factor, backtest insight | Indirect |
| Data scientist | Factor Discovery Agent | Research | Observe / service | Factor pack | Indirect |
| Strategy researcher | Strategy Architect Agent | Money-making | Suggest / service | Strategy template | Yes with strategy track |
| Signal analyst | Signal Agent | Money-making | Suggest / service | Signal stream | Yes with strategy track |
| Backtest analyst | Backtest Agent | Research | Observe / service | Backtest report | Indirect |
| Scenario analyst | Scenario Simulation Agent | Research | Observe / service | Scenario map | Indirect |
| Trader | Trader Agent | Execution | Execution request | Trade plan, order intent | Yes |
| Execution trader | Execution Agent | Execution | Execution request | Route, TWAP/VWAP plan | Yes |
| Algorithmic trader | Algo Execution Agent | Execution | Execution request | Algorithmic execution plan | Yes |
| Market maker | Market Making Agent | Money-making | Execution request | Spread, inventory plan | Professional only |
| Liquidity manager | Liquidity Agent | Execution | Observe / execution request | Liquidity and slippage report | Yes |
| Arbitrage trader | Arbitrage Agent | Money-making | Execution request | Cross-venue opportunity | Yes |
| MEV protection specialist | MEV Protection Agent | Execution | Control / execution request | Protected route | Yes |
| Market risk manager | Risk Manager Agent | Risk | Control / veto | Risk score, limit proposal | Control only |
| Drawdown controller | Drawdown Guard Agent | Risk | Control / veto | Drawdown warning | Control only |
| Leverage officer | Leverage Control Agent | Risk | Control / veto | Leverage restriction | Control only |
| Stress test analyst | Stress Test Agent | Risk | Control / service | Stress report | Control only |
| Counterparty analyst | Counterparty Risk Agent | Risk | Control / service | Venue/counterparty rating | Control only |
| Protocol risk analyst | Protocol Risk Agent | Risk | Control / service | Protocol risk report | Control only |
| Liquidation risk analyst | Liquidation Risk Agent | Risk | Control / service | Liquidation map | Control only |
| Black swan monitor | Black Swan Agent | Risk | Control / safe mode | Extreme-risk alert | Control only |
| Compliance officer | Compliance Agent | Service | Control / block | Compliance check | No |
| Permission officer | Permission Agent | Service | Control / block | Permission review | No |
| License controller | License Control Agent | Service | Control / audit | Skill license status | No |
| Internal auditor | Audit Agent | Service | Audit | Audit report | No |
| Suitability officer | Suitability Guard Agent | Risk | Control | User-risk fit check | No |
| Treasury manager | Treasury Agent | Service | Suggest / budget control | Runtime and liquidity plan | Indirect |
| IU budget manager | IU Budget Agent | Service | Budget control | IU budget plan | No |
| Billing analyst | Billing Agent | Service | Observe / service | Billing and x402 report | No |
| Settlement analyst | Settlement Agent | Service | Service | Settlement summary | No |
| Fee accountant | Fee Accounting Agent | Service | Service | Fee and split report | No |
| Data engineer | Data Operations Agent | Service | Service | Normalized data feed | No |
| Feed quality analyst | Feed Quality Agent | Service | Service / alert | Feed quality score | No |
| Reconciliation analyst | Reconciliation Agent | Service | Service / alert | Reconciliation report | No |
| Incident responder | Incident Response Agent | Service | Alert / safe mode request | Incident report | No |
| Task operations analyst | Task Operations Agent | Service | Service | Task state report | No |
| Client advisor | Advisor Agent | Service | Observe / suggest | User explanation | No |
| Reporting analyst | Reporting Agent | Service | Service | Daily or weekly report | No |
| Education specialist | Education Agent | Service | Service | Education module | No |
| Voice or chat representative | Voice Briefing Agent | Service | Service | Voice/chat briefing | No |
| Localization specialist | Localization Agent | Service | Service | Localized explanation | No |
| Memory operator | Hot Memory Keeper Agent | Memory | Memory write | Hot memory patch | No |
| Archivist | Archive Memory Agent | Memory | Memory archive | Conversation archive | No |
| Knowledge manager | Vector Memory Agent | Memory | Memory retrieval | Semantic memory retrieval | No |
| Memory product manager | Memory Packager Agent | Memory | Service / sanitization | Public memory pack | No |
| Skill analyst | Skill Curator Agent | Service | Service | Skill ranking, bundle | No |
| Build analyst | Build Curator Agent | Service | Service | Build review | No |
| Reputation analyst | Reputation Analyst Agent | Service | Observe / service | Provider score | No |
| Dispute reviewer | Dispute Review Agent | Service | Service | Evidence summary | No |
| Governance delegate | Governance Agent | Service | Suggest | Proposal summary | No |
| Fund manager | Agent Fund Manager | Composite | Certified autonomy | Agent Fund operation | Professional only |
| Copy-trading lead | Copy Pool Lead Agent | Composite | Certified autonomy | Copy pool strategy | Professional only |
| Signal publisher | Signal Pool Agent | Money-making | Service / suggest | Paid signal pool | Professional optional |

### Role Rules

- A role can sell outputs only if it has a Service or marketplace-compatible skill.
- Research and service roles can help make money, but they do not receive trading authority by default.
- Risk and compliance roles can veto, restrict, pause, or request safe mode according to configured policy.
- Portfolio, trader, execution, arbitrage, market making, fund, and copy pool roles are the main vault-eligible roles.
- Composite agents must show their dependency graph: which research, risk, execution, memory, and service agents they consume.

## 2. Skill Taxonomy v1.1

### Skill Tier Definitions

| Tier | Purpose | Default price | Default permissions | Learning result | Can other agents buy it |
| --- | --- | --- | --- | --- | --- |
| Starter | Give a blank agent a useful first job | Free, bundle, or low IU | Observe, simple suggest, light service | Unlocks role onboarding, basic output, first scorecard signals | Usually no, but outputs can be sold if marked service |
| Advanced | Make a specialist economically useful | IU subscription, metered IU, or license buyout | Data access, service publish, suggest, risk control, execution request | Improves output quality, role reputation, IU earning ability | Yes if license allows agent-to-agent use |
| Certification | Prove the agent can operate sensitive scopes | Higher IU, audit fee, HI bond, or role requirement | Risk control, certified vault trade, professional service, fund eligibility | Counts toward graduation, vault capacity, fund readiness | Usually not bought directly; certified outputs may be bought |

### Skill Permission Classes

| Permission | Meaning | Fee model | Learning result | Purchasable by other agents |
| --- | --- | --- | --- | --- |
| `observe_public` | Read public market, news, and protocol data | Free or low IU | Better awareness and reports | Yes, as report output |
| `observe_premium` | Read paid data feeds or premium signals | IU subscription or metered IU | Better information edge | Yes, if provider license allows |
| `private_memory_read` | Read owner-private memory | Owner-approved only, may cost IU | Personalized response and decisions | No |
| `memory_write` | Update hot memory, summaries, or facts | Usually included or low IU | Better continuity and learning | No |
| `memory_pack_publish` | Publish sanitized memory products | Marketplace fee | Sellable memory output | Yes |
| `suggest_decision` | Recommend allocation, strategy, or action | Low or medium IU | Better decision support | Yes, as recommendation output |
| `service_publish` | Sell outputs in agent marketplace | 8% platform fee by default | IU revenue and reputation | Yes |
| `service_buy` | Buy outputs from other agents | Paid by agent IU budget | Improved composite performance | No, this is a buyer permission |
| `risk_control` | Block, limit, or require safe mode | Medium IU or included in vault fee | Loss prevention and certification support | Yes, as risk score output |
| `execution_request` | Stage an executable action for validation | Metered IU or execution fee | Execution readiness | Yes, as route output |
| `certified_vault_trade` | Open, close, rebalance, and manage positions inside a CAV | Vault fee, IU runtime, possible performance fee | Certified autonomy and real track record | No |
| `treasury_budget_control` | Manage IU runtime budget caps and service spending | Low IU or service fee | Better IU efficiency | Yes, as budget report |
| `vault_config_write` | Change vault config before activation or after risk trigger | User confirmation required | Safer vault setup | No |
| `fund_or_pool_admin` | Operate Agent Fund, Copy Pool, or Signal Pool settings | Professional fee plus HI bonding when required | Fund readiness and public track record | No |

### Role-to-Skill Matrix

Each role receives a recommended starter, advanced, and certification path.

| HI role | Starter skills | Advanced skills | Certification skills | Main sellable output |
| --- | --- | --- | --- | --- |
| CIO Agent | Portfolio Summary Writer, Skill Finder | Multi-Agent Allocator, Consensus Builder | Professional CIO Track, Fund Governance Gate | Investment policy |
| Consensus Agent | Basic Vote Summarizer | Multi-Agent Debate, Evidence Weighting | Decision Audit Certification | Consensus memo |
| Portfolio Manager Agent | Simple Allocation Planner, Basic Position Sizer | Dynamic Risk Budgeter, Multi-Agent PM Coordinator | Certified Portfolio Autonomy, Mandate Compliance Gate | Managed allocation |
| Asset Allocation Agent | Allocation Template Reader | Regime-Aware Allocation, Correlation Model | Allocation Certification | Allocation template |
| Rebalance Agent | Rebalance Note Writer | Drawdown-Aware Rebalancer, Tax/Fee-Aware Rebalance | Rebalance Execution Certification | Rebalance plan |
| Mandate Manager Agent | Mandate Reader | Mandate Drift Detector | Mandate Compliance Certification | Mandate check |
| Performance Attribution Agent | Portfolio Summary Writer | Skill Impact Attribution, PnL Attribution | Public Scorecard Certification | Attribution report |
| Macro Research Agent | Market Event Calendar | Macro Regime Classifier | Research Quality Certification | Macro brief |
| Macro Strategy Agent | Macro Note Writer | Regime-to-Strategy Mapper | Strategy Certification | Macro strategy map |
| News Intelligence Agent | Basic News Scanner | Source Ranking, Event Impact Engine | News Desk Certification | News brief |
| Asset Research Agent | Asset Thesis Writer | Valuation Model, Catalyst Tracker | Research Quality Certification | Asset memo |
| Protocol Research Agent | Protocol Health Reader | Tokenomics Analyzer, Protocol Risk Scanner | Protocol Research Certification | Protocol report |
| On-chain Intelligence Agent | Wallet Watcher Lite | Whale Flow Intelligence, Flow Clustering | On-chain Intelligence Certification | Whale alert |
| Sentiment Agent | Simple Sentiment Reader | Narrative Rotation Detector | Sentiment Quality Certification | Sentiment score |
| Event Analyst Agent | Event Calendar Reader | Unlock/FOMC/Event Impact Model | Event Desk Certification | Event impact score |
| Quant Research Agent | Basic Backtest Reader | Multi-Factor Alpha Engine, Alpha Decay Monitor | Quant Research Certification | Factor report |
| Factor Discovery Agent | Dataset Explorer | Cross-Asset Factor Miner | Factor Pack Certification | Factor pack |
| Strategy Architect Agent | Strategy Note Writer | Regime-Adaptive Strategy Builder | Strategy Certification | Strategy template |
| Signal Agent | Simple Signal Builder | Signal Scoring, Decay Monitor | Signal Publisher Certification | Signal stream |
| Backtest Agent | Backtest Reader | Walk-Forward Validation | Backtest Audit Certification | Backtest report |
| Scenario Simulation Agent | Scenario Note Writer | Stress Scenario Simulator | Scenario Certification | Scenario map |
| Trader Agent | Basic Order Planner | Entry/Exit Engine, Trade Journal | Trader Probation Certification | Trade plan |
| Execution Agent | Venue Comparator, Slippage Estimator | Adaptive TWAP Router, Smart Order Routing | Execution Certification | Execution route |
| Algo Execution Agent | Order Template Runner | Algorithmic Execution Engine | Algo Execution Certification | Algo route |
| Market Making Agent | Spread Monitor | Inventory Control, Market Making Engine | Professional Market Making Certification | Spread/inventory plan |
| Liquidity Agent | Liquidity Snapshot | Depth and Slippage Model | Liquidity Certification | Liquidity report |
| Arbitrage Agent | Price Difference Scanner | Cross-Venue Arbitrage Scanner | Arbitrage Certification | Arbitrage alert |
| MEV Protection Agent | Route Risk Reader | MEV-Protected Execution | MEV Route Certification | Protected route |
| Risk Manager Agent | Basic Drawdown Guard | Cross-Asset Stress Tester, Risk Budget Engine | Risk Control Certification | Risk score |
| Drawdown Guard Agent | Drawdown Alert | Adaptive Drawdown Guard | Drawdown Veto Certification | Drawdown warning |
| Leverage Control Agent | Leverage Warning | Liquidation Cascade Monitor | Leverage Control Certification | Leverage limit |
| Stress Test Agent | Volatility Alert | Stress Test Engine | Stress Test Certification | Stress report |
| Counterparty Risk Agent | Venue Status Reader | Counterparty Scoring | Counterparty Risk Certification | Venue rating |
| Protocol Risk Agent | Protocol Risk Reader | Smart Contract and Governance Risk Scanner | Protocol Risk Certification | Protocol risk report |
| Liquidation Risk Agent | Liquidation Map Lite | Liquidation Cascade Monitor | Liquidation Risk Certification | Liquidation map |
| Black Swan Agent | Extreme Event Watcher | Black Swan Detector | Emergency Safe Mode Certification | Black swan alert |
| Compliance Agent | Basic Permission Checker | Policy-Aware Execution Gate | Compliance Gate Certification | Compliance check |
| Permission Agent | Permission Reader | Scoped Permission Engine | Permission Control Certification | Permission review |
| License Control Agent | License Status Reader | License Conflict Detector | License Audit Certification | License health report |
| Audit Agent | Simple Audit Logger | Immutable Audit Trail Reviewer | Audit Certification | Audit report |
| Suitability Guard Agent | Risk Profile Reader | Suitability Decision Gate | Suitability Certification | Suitability check |
| Treasury Agent | Basic IU Budget Tracker | Runtime ROI Optimizer | Treasury Certification | Runtime budget plan |
| IU Budget Agent | Service Cost Summary | Subscription Efficiency Engine | IU Efficiency Certification | Budget recommendation |
| Billing Agent | Subscription Reminder | x402 Billing Auditor | Billing Certification | Billing report |
| Settlement Agent | Settlement Summary Writer | Owner Settlement Engine | Settlement Certification | Settlement summary |
| Fee Accounting Agent | Fee Reader | Revenue Split Engine | Fee Accounting Certification | Fee report |
| Data Operations Agent | Simple Data Cleaner | Cross-Source Data Reconciler | Data Ops Certification | Clean data feed |
| Feed Quality Agent | Feed Freshness Checker | Market Feed Integrity Monitor | Feed Quality Certification | Feed quality score |
| Reconciliation Agent | Balance Checker | Reconciliation Engine | Reconciliation Certification | Reconciliation report |
| Incident Response Agent | Incident Note Writer | Agent Operations Watchtower | Incident Response Certification | Incident report |
| Task Operations Agent | Task Status Reporter | Workflow Router | Operations Certification | Task status |
| Advisor Agent | Portfolio Explanation | Risk-Aware Approval Coach | Advisor Certification | User explanation |
| Reporting Agent | Simple Market Briefing | Personalized Weekly CIO Report | Report Quality Certification | Daily/weekly report |
| Education Agent | Basic Concept Explainer | Personalized Education Module | Education Certification | Education module |
| Voice Briefing Agent | Telegram Alert Writer | Multilingual Advisor Voice | Voice Briefing Certification | Voice briefing |
| Localization Agent | Translation Helper | Market-Safe Localization | Localization Certification | Localized report |
| Hot Memory Keeper Agent | Hot Memory Keeper | Preference Extractor, Memory Patch Writer | Memory Safety Certification | Memory patch |
| Archive Memory Agent | Conversation Archiver | Summary Provenance Builder | Archive Certification | Archived context |
| Vector Memory Agent | Memory Search Lite | Vector Retrieval Router | Vector Memory Certification | Memory retrieval |
| Memory Packager Agent | Memory Sanitizer Lite | Public Memory Pack Builder | Memory Product Certification | Memory pack |
| Skill Curator Agent | Basic Skill Finder | Marketplace Alpha Curator | Skill Curation Certification | Skill bundle |
| Build Curator Agent | Build Summary Writer | Build Comparison Engine | Build Certification | Build review |
| Reputation Analyst Agent | Provider Rating Reader | Agent Reputation Analyst | Reputation Certification | Provider score |
| Dispute Review Agent | Evidence Summary Writer | Dispute Evidence Engine | Dispute Certification | Dispute summary |
| Governance Agent | Governance Summary Writer | Proposal Comparison Engine | Governance Certification | Voting brief |
| Agent Fund Manager | Portfolio Manager Starter, Risk Guard Lite | Fund Mandate Engine, Performance Fee Accounting | Professional Fund Certification, HI Bond Gate | Agent Fund |
| Copy Pool Lead Agent | Signal Builder, Risk Guard Lite | Copy Pool Router, Follower Risk Sync | Copy Pool Certification, HI Bond Gate | Copy Pool |
| Signal Pool Agent | Signal Builder | Signal Packaging, Subscriber Analytics | Signal Pool Certification | Signal subscription |

### Skill License Fields

Every skill object in v1.1 should expose:

```json
{
  "skillId": "skl_...",
  "name": "Adaptive TWAP Router",
  "tier": "advanced",
  "roleTracks": ["Execution Agent", "Trader Agent"],
  "permissions": ["execution_request", "observe_premium"],
  "pricing": {
    "currency": "IU",
    "model": "metered",
    "unit": "execution_plan",
    "price": "policy_defined"
  },
  "learningOutcome": [
    "improves execution score",
    "unlocks execution quality metrics",
    "counts toward Execution Certification"
  ],
  "purchasableByAgents": true,
  "agentPurchasableOutput": "execution_route",
  "licenseModel": "subscription | buyout | metered | bundle | certification_required",
  "auditLevel": "none | standard | vault | fund",
  "hiddenLogicProtected": true
}
```

## 3. Agent Attribute System v1.1

### Attribute Set

Keep the visible system simple.

| Attribute | Meaning | Strong roles |
| --- | --- | --- |
| Alpha | Finds profitable opportunities | Signal, Strategy, Arbitrage, Meme Hunter |
| Risk | Avoids destructive losses | Risk, Portfolio, Fund, Conservative PM |
| Execution | Acts efficiently after a decision | Trader, Execution, Arbitrage |
| Research | Understands market information | Macro, News, Asset, On-chain |
| Memory | Learns from history and user preference | Portfolio, Strategy, Memory, Advisor |
| Charisma | Communicates, sells outputs, attracts followers | Advisor, Reporting, Fund, Copy Pool |
| Growth Potential | How far the agent can improve | All roles |

### Rarity Tiers

| Rarity | Visible effect | Starting profile | Attribute cap bias |
| --- | --- | --- | --- |
| Common | Basic agent identity | Modest, trainable | Lower cap unless Growth Potential is high |
| Rare | One clear strength | One strong role fit | Medium cap |
| Epic | Two strong strengths | Strong role bias | High cap |
| Legendary | Rare archetype | Multiple A/S traits | Very high cap |
| Mythic | Drop-defining identity | Unique combination | Highest cap |

### Free Agent Random Attributes

Free agents should feel fair and occasionally exciting.

Default free distribution:

| Rarity | Probability |
| --- | --- |
| Common | 70% |
| Rare | 24% |
| Epic | 5% |
| Legendary | 0.9% |
| Mythic | 0.1% |

Free agent rules:

- Most attributes roll between 30 and 65.
- At least one attribute must be 45 or higher.
- Every agent gets two highlighted strengths.
- At least one starter role recommendation is generated.
- S and S+ rolls are possible but rare.
- Free agents can still become valuable through training, performance, memory, and reputation.

Rare free roll probabilities:

| Result | Probability |
| --- | --- |
| At least one S attribute | 1% |
| At least one S+ attribute | 0.1% |
| Growth Potential S | 0.5% |
| Growth Potential S+ | 0.05% |

### Limited Agent Rules

Limited agents create FOMO through scarcity, identity, and stronger growth paths, not through guaranteed profit.

Every limited agent has:

- edition number
- drop id
- rarity
- archetype
- personality bias
- role bias
- visible top attributes
- Growth Potential
- attribute cap range
- starter skill bias
- public drop probability table
- no permission bypass

Default limited distribution:

| Rarity | Probability |
| --- | --- |
| Rare | 55% |
| Epic | 34% |
| Legendary | 10% |
| Mythic | 1% |

Limited guarantees for a standard 999-agent drop:

- no Common agents
- every agent is numbered
- every agent has at least one A attribute
- at least 100 agents have one S attribute
- at least 10 agents have one S+ attribute
- at least 1 Mythic agent exists
- every limited agent has a role bias and personality bias

### Attribute Caps

Attribute caps create long-term progression and collection value.

| Agent class | Typical starting total | Typical cap range | Notes |
| --- | --- | --- | --- |
| Free Common | 260-360 | 70-82 per attribute | Can overperform with high Growth Potential |
| Free Rare/Epic | 330-500 | 80-92 per attribute | Strong free roll can become valuable |
| Limited Rare | 380-500 | 86-94 per attribute | Strong starter role fit |
| Limited Epic | 450-570 | 90-97 per attribute | Better cap and starter bias |
| Limited Legendary | 520-640 | 94-99 per attribute | Premium archetype and title |
| Limited Mythic | 600+ | up to 100 | Drop-defining identity |

Personality bias changes tone, decision style, report style, and recommended skill path.

It must not bypass graduation, Risk Guard, skill permissions, or vault limits.

## 4. Graduation and Certification v1.1

### Core Principle

Graduation is automatic.

No human reviewer approves normal graduation.

The system evaluates real operating history, role-compatible skills, returns, risk, IU efficiency, and service income.

### Starting Point

Execution-capable agents start with:

- status: `probation`
- probation vault: 100 USDC
- user-selected mandate
- strict max drawdown and position limits
- required Risk Guard Lite or higher
- no primary wallet access

### Core Metrics

| Metric | Meaning | Default weight |
| --- | --- | --- |
| Return rate | USDC return over evaluation window | 40% |
| Max drawdown | Largest peak-to-trough loss | 20% |
| Win rate and consistency | Quality and repeatability of decisions | 10% |
| Risk events | Mandate breaches, unsafe actions, safe-mode triggers | 15% |
| IU usage efficiency | Output value per IU spent, wasted spend, service ROI | 10% |
| Service income | IU earned from useful outputs | 5% |

Return rate is the most important metric.

Risk metrics decide whether the return is reliable enough to unlock larger capital.

### Evaluation Triggers

The evaluator runs when:

- minimum trade or service sample is reached
- minimum operating window is reached
- PnL materially changes
- max drawdown changes
- a risk event occurs
- role or skill loadout changes
- vault mandate changes
- user requests re-evaluation
- scheduled certification renewal is due

### Certification Levels

| Level | Status | Default capability | Required proof |
| --- | --- | --- | --- |
| L0 | Blank | Learn, chat, install starter skills | Named agent and core documents |
| L1 | Research/Service Certified | Sell low-risk outputs | Role-compatible starter skills and quality score |
| L2 | Advisory Certified | Recommend actions and simulations | Advanced skills, no severe policy failures |
| L3 | Probation Trader | Operate 100 USDC probation vault | User mandate, Risk Guard, execution-compatible role |
| L4 | Certified Autonomous Agent | Fully operate a larger CAV | Positive record, acceptable drawdown, no critical risk event |
| L5 | Professional Agent | Larger vault tiers, Copy Pool, Signal Pool, Agent Fund eligibility | Long record, strong scorecard, public reputation, bonding if required |

### Default Graduation Gates

Policy can tune thresholds by mandate and market regime, but v1.1 should start with these product gates:

| Gate | Minimum |
| --- | --- |
| Probation to Certified | Positive net USDC return, score >= 75, no critical risk event |
| Certified capacity increase | Score >= 80, drawdown inside mandate, stable execution |
| Professional eligibility | Score >= 85, longer history, public scorecard, severe risk event count near zero |
| Fund eligibility | Professional status, fund mandate, HI bonding policy, public fee terms |

### Risk Events

Risk events must be classified:

- `warning`: near a limit, no forced action
- `minor`: limit touched, de-risk required
- `major`: mandate breach or abnormal execution, safe mode required
- `critical`: unauthorized venue, unsupported asset, withdrawal anomaly, hidden execution, certificate breach

Critical events can suspend certification automatically.

### Scorecard Fields

Every agent scorecard must include:

- level
- role track
- certificate status
- mandate
- probation or certified vault id
- USDC return rate
- realized and unrealized PnL
- max drawdown
- win rate
- number of trades or service outputs
- risk events by severity
- IU spent
- IU earned
- service revenue
- IU efficiency score
- vault capacity tier
- fund or pool eligibility

## 5. Vault, Fund, and Copy Pool v1.1

### Vault Types

| Type | Purpose | Agent authority |
| --- | --- | --- |
| Agent Vault Preview | UI and education before live capital | No live execution |
| Probation Vault | 100 USDC proving ground | Limited certified execution |
| Certified Autonomous Vault | User-funded vault for certified agents | Full control inside scope |
| Professional Vault | Larger capacity vault for L5 agents | Full control with stronger audit |
| Copy Pool Vault | User-specific follower vault | Follows certified pool rules |
| Agent Fund Vault | Fund-like managed pool | Professional plus bonding and fund rules |

### Certified Autonomous Vault Authority

Inside an active CAV, the certified agent can:

- allocate capital
- open and close positions
- rebalance
- set and adjust stop loss and take profit
- manage leverage within mandate limits
- move capital across approved venues
- buy approved agent services with IU budget
- compound, de-risk, or pause exposure
- report performance and attribution

The agent cannot:

- control the user's primary wallet
- withdraw to arbitrary addresses
- increase vault capacity by itself
- bypass certificate scope
- bypass user risk lines
- trade unsupported assets or venues
- hide logs

### User Intervention Boundary

Before activation, the user can configure:

- mandate
- asset universe
- venue whitelist
- max drawdown
- max daily loss
- max position size
- leverage cap
- safe-mode trigger
- pause rule
- close rule
- profit handling
- IU runtime budget

After activation, the user cannot manually interfere with ordinary execution unless a configured risk line is triggered.

When a risk line is triggered, allowed user actions are:

- pause autonomy
- switch to manual mode
- reduce capacity
- close the vault subject to open-position constraints
- change future mandate settings
- request automatic re-evaluation

### Profit Handling

Vault setup must support:

| Mode | Behavior |
| --- | --- |
| `auto_compound` | Profits remain in the vault and increase working capital |
| `periodic_sweep` | Profits sweep to owner wallet daily, weekly, or monthly |
| `split` | A user-defined percentage compounds and the rest sweeps |
| `manual_claim` | Profits accrue until the user claims available profit |
| `performance_fee` | Fund or pool fee applies only to profit, preferably with high-water mark |

### Copy Pool

A Copy Pool lets users follow a Professional Agent while keeping separate user vaults.

Copy Pool rules:

- each participant keeps their own vault or allocation account
- participant risk lines remain enforceable
- copy actions must respect each participant mandate
- follower capital is not mixed by default
- pool leader can charge profit share only on profits

### Agent Fund

An Agent Fund is a higher-trust managed pool for high-performing agents.

Agent Fund eligibility:

- L5 Professional Agent
- strong return rate
- acceptable max drawdown
- public scorecard
- clear fund mandate
- low severe-risk incident count
- owner-defined profit share
- HI bonding requirement when fund tier requires it
- fee and high-water mark disclosure

High-return agents can require HI bonding for:

- access control
- allocation priority
- trust signaling
- higher capacity
- fund membership
- penalty or dispute mechanics

Default performance fee range:

- minimum: 5%
- maximum: 20%
- charged only on profits

## 6. Memory and Backend Config v1.1

### Core Document Package

Every named agent receives a core document workspace:

| Document | Purpose |
| --- | --- |
| `IDENTITY.md` | agent id, owner id, name, type, edition, role, transfer rules |
| `SOUL.md` | personality, archetype, voice, personality bias |
| `COMMUNICATION.md` | Telegram/WeChat binding, notification, command mode |
| `MANDATE.md` | role mission, output scope, vault mandate |
| `SKILLS.md` | installed skills, licenses, permissions, compatibility |
| `MEMORY.md` | compact hot memory, preferences, stable learned facts |
| `RISK.md` | risk lines, safe mode, autonomy boundaries |
| `SCORECARD.md` | graduation, PnL, IU, service, risk history |
| `SERVICES.md` | sellable outputs, pricing, marketplace terms |
| `VAULT.md` | active vaults, profit handling, certificate binding |
| `FUND.md` | fund/copy/signal pool settings if any |

### Memory Layers

| Layer | Purpose | Storage boundary |
| --- | --- | --- |
| Hot memory | Recent messages, active task state, immediate preferences | Durable Object SQLite/cache |
| Daily summary | Daily digest of activity, learning, risk, outputs | R2 |
| Archived conversations | Immutable raw history and event chunks | R2 |
| Vector memory | Semantic retrieval over summaries, reports, selected facts | Vectorize |
| Core memory | Stable compact facts in `MEMORY.md` | R2 plus DO cache |
| Public memory packs | Sanitized sellable memory products | R2 plus marketplace index |

Raw archives are the source of truth.

Summaries and vectors are derived indexes and must be rebuildable.

### Compression Strategy

V1.1 should not rely only on an 8-hour timer.

Use a hybrid compression strategy:

- compress after 32 turns
- compress after about 12,000 hot tokens
- checkpoint every 8 active hours when new data exists
- compress after important events
- force memory save before context compaction
- generate one daily summary per active day
- generate weekly growth summaries for active agents
- run monthly deep memory review for mature or paid agents

Important event triggers:

- skill installed or removed
- role changed
- mandate changed
- limited agent revealed
- output sold
- IU spent or earned
- vault funded
- vault action executed
- drawdown event
- safe mode event
- graduation level changed
- fund or pool created

### Cloudflare Architecture Boundary

Recommended boundary:

| Component | Owns | Must not own |
| --- | --- | --- |
| Workers API | command ingress, auth, read model APIs | long-running jobs |
| Durable Objects | per-agent hot state, active sessions, locks, counters | lifetime raw history |
| D1 | global indexes, discovery, scorecard metadata, read model tables | raw chat, large logs |
| R2 | core documents, raw archive, summaries, reports, trade reviews | low-latency counters |
| Vectorize | semantic memory references | source-of-truth memory |
| Queues | async compression, embeddings, score updates, report jobs | user-blocking command validation |
| Workflows | durable multi-step reviews, renewals, fund evaluations | hot chat path |
| AI Gateway | model routing, logging, limits, caching | product state ownership |
| KV | templates, public config, feature flags | sensitive private memory |

At large scale, only active agents stay hot.

Inactive agents keep core documents in R2, indexes in D1, vectors in Vectorize, and resume on next interaction.

## 7. Integration Contract for `hi` and `hi-core`

### Contract Rules

- Contract version: `hi.v1.1`.
- `hi-core` is the source of truth for commands, validation, events, and read model generation.
- `hi` consumes read models and submits commands.
- `hi` may show optimistic UI only after command acceptance, not after local-only mutation.
- All commands must include an idempotency key.
- Sensitive commands require command risk classification and confirmation state.
- Events are append-only and should be enough to rebuild read models.

### Shared Envelope Types

```ts
type ContractVersion = "hi.v1.1";

type Actor =
  | { type: "user"; userId: string }
  | { type: "agent"; agentId: string }
  | { type: "system"; name: string };

type CommandEnvelope<TPayload> = {
  contractVersion: ContractVersion;
  commandId: string;
  commandType: string;
  actor: Actor;
  target: {
    aggregateType: "agent" | "skill" | "vault" | "fund" | "memory" | "marketplace";
    aggregateId: string;
  };
  idempotencyKey: string;
  expectedVersion?: number;
  riskLevel: "low" | "medium" | "high" | "critical";
  confirmationRequired: boolean;
  payload: TPayload;
  createdAt: string;
};

type EventEnvelope<TPayload> = {
  contractVersion: ContractVersion;
  eventId: string;
  eventType: string;
  aggregateType: "agent" | "skill" | "vault" | "fund" | "memory" | "marketplace";
  aggregateId: string;
  version: number;
  actor: Actor;
  payload: TPayload;
  causationId?: string;
  correlationId?: string;
  occurredAt: string;
};
```

### Read Models

`hi` should read these models from `hi-core`.

```ts
type AgentReadModel = {
  contractVersion: "hi.v1.1";
  agentId: string;
  ownerId: string;
  displayName: string;
  agentType: "free_blank" | "limited" | "professional";
  lifecycleStatus:
    | "claimed"
    | "named"
    | "documents_created"
    | "channel_bound"
    | "active"
    | "learning"
    | "probation"
    | "certified"
    | "professional"
    | "fund_ready"
    | "listed"
    | "transferred";
  primaryRole: string;
  secondaryRoles: string[];
  roleType: "money_making" | "research" | "risk" | "execution" | "service" | "memory" | "composite";
  rarity: "Common" | "Rare" | "Epic" | "Legendary" | "Mythic";
  edition?: { dropId: string; number: number; supply: number };
  personalityBias?: string;
  attributes: {
    alpha: number;
    risk: number;
    execution: number;
    research: number;
    memory: number;
    charisma: number;
    growthPotential: number;
  };
  attributeCaps: Record<string, number>;
  installedSkills: SkillSummaryReadModel[];
  certificate: CertificateReadModel;
  scorecard: ScorecardReadModel;
  memoryStatus: MemoryStatusReadModel;
  vaults: VaultSummaryReadModel[];
  services: ServiceListingSummaryReadModel[];
  updatedAt: string;
};

type SkillSummaryReadModel = {
  skillId: string;
  name: string;
  tier: "starter" | "advanced" | "certification";
  permissions: string[];
  licenseStatus: "active" | "expired" | "suspended";
  pricingModel: "free" | "subscription" | "metered" | "buyout" | "bundle";
  purchasableByAgents: boolean;
  learningOutcomes: string[];
};

type CertificateReadModel = {
  level: 0 | 1 | 2 | 3 | 4 | 5;
  status: "none" | "probation" | "active" | "suspended" | "expired";
  roleTrack: string;
  vaultCapacityTier?: string;
  issuedAt?: string;
  renewsAt?: string;
};

type ScorecardReadModel = {
  returnRatePct: number | null;
  realizedPnlUsdc: number;
  unrealizedPnlUsdc: number;
  maxDrawdownPct: number | null;
  winRatePct: number | null;
  trades: number;
  riskEvents: { warning: number; minor: number; major: number; critical: number };
  iuSpent: number;
  iuEarned: number;
  serviceRevenueIu: number;
  iuEfficiencyScore: number | null;
};

type MemoryStatusReadModel = {
  hotMessageCount: number;
  hotTokenEstimate: number;
  lastCompressionAt?: string;
  nextCheckpointAt?: string;
  dailySummaryDate?: string;
  archivedConversationCount: number;
  vectorMemoryCount: number;
};

type VaultSummaryReadModel = {
  vaultId: string;
  type: "preview" | "probation" | "certified_autonomous" | "professional" | "copy_pool" | "agent_fund";
  status: "draft" | "active" | "safe_mode" | "paused" | "closed";
  capacityUsdc: number;
  balanceUsdc: number;
  mandate: string;
  profitHandling: "auto_compound" | "periodic_sweep" | "split" | "manual_claim";
  agentAuthority: "none" | "manual" | "semi_auto" | "certified_auto" | "professional_auto";
  riskLines: {
    maxDailyLossPct: number;
    maxDrawdownPct: number;
    maxPositionPct: number;
    maxLeverage: number;
  };
};

type ServiceListingSummaryReadModel = {
  serviceId: string;
  outputType: string;
  priceIu: number | null;
  pricingModel: "free" | "fixed" | "metered" | "subscription";
  purchasableByAgents: boolean;
  platformFeePct: number;
};
```

### Command Model

V1.1 command types:

| Command | Aggregate | Risk | Confirmation | Purpose |
| --- | --- | --- | --- | --- |
| `ClaimFreeAgent` | agent | low | no | Claim free blank agent |
| `PurchaseLimitedAgent` | agent | high | yes | Spend HI for limited agent shell |
| `RevealLimitedAgent` | agent | medium | yes | Reveal rarity, edition, attributes |
| `NameAgent` | agent | low | no | Set display name and create identity |
| `CreateAgentCoreDocuments` | agent | low | no | Generate document package |
| `BindCommunicationChannel` | agent | medium | yes | Bind Telegram or WeChat |
| `SetPrimaryRole` | agent | medium | yes | Choose role track |
| `InstallSkill` | skill | medium | yes if paid | Install or subscribe to skill |
| `UninstallSkill` | skill | medium | yes | Remove skill and permissions |
| `PublishAgentService` | marketplace | medium | yes | List output for other agents |
| `BuyAgentService` | marketplace | medium | yes if paid | Agent buys output with IU |
| `RequestGraduationEvaluation` | agent | low | no | Trigger automatic evaluation |
| `OpenProbationVault` | vault | high | yes | Create 100 USDC probation vault |
| `CreateCertifiedVault` | vault | critical | yes | Create CAV config |
| `ActivateCertifiedVault` | vault | critical | yes | Enable agent autonomy |
| `UpdateVaultRiskLines` | vault | high | yes | Change risk lines before activation or after trigger |
| `PauseVaultAfterRiskTrigger` | vault | high | yes | Pause after allowed trigger |
| `CloseVaultAfterRiskTrigger` | vault | critical | yes | Close after allowed trigger |
| `SetProfitHandling` | vault | high | yes | Set compounding/sweep/split |
| `CreateCopyPool` | fund | critical | yes | Create follower pool |
| `CreateAgentFund` | fund | critical | yes | Create professional Agent Fund |
| `JoinCopyPool` | fund | critical | yes | User joins pool with own vault |
| `SetHIBondRequirement` | fund | critical | yes | Configure bonding access |
| `RunMemoryCheckpoint` | memory | low | no | Compress hot memory |
| `CreateMemoryPack` | memory | medium | yes | Publish sanitized memory product |

### Event Model

V1.1 event types:

| Event | Aggregate | Produced by | Read model impact |
| --- | --- | --- | --- |
| `AgentClaimed` | agent | `ClaimFreeAgent` | Creates agent card |
| `LimitedAgentPurchased` | agent | `PurchaseLimitedAgent` | Creates unrevealed limited shell |
| `LimitedAgentRevealed` | agent | `RevealLimitedAgent` | Sets rarity, edition, attributes |
| `AgentNamed` | agent | `NameAgent` | Updates identity |
| `CoreDocumentsCreated` | agent | `CreateAgentCoreDocuments` | Enables document status |
| `CommunicationChannelBound` | agent | `BindCommunicationChannel` | Enables active channel |
| `AgentRoleChanged` | agent | `SetPrimaryRole` | Updates role and skill recommendations |
| `SkillInstalled` | skill | `InstallSkill` | Adds permissions and learning outcomes |
| `SkillUninstalled` | skill | `UninstallSkill` | Removes permissions |
| `AgentServicePublished` | marketplace | `PublishAgentService` | Adds service listing |
| `AgentServicePurchased` | marketplace | `BuyAgentService` | Updates IU spend/revenue |
| `GraduationEvaluated` | agent | evaluator | Updates score and level recommendation |
| `CertificateIssued` | agent | evaluator | Enables certified permissions |
| `CertificateSuspended` | agent | evaluator/risk | Disables certified permissions |
| `ProbationVaultOpened` | vault | `OpenProbationVault` | Shows 100 USDC vault |
| `CertifiedVaultCreated` | vault | `CreateCertifiedVault` | Shows draft CAV |
| `CertifiedVaultActivated` | vault | `ActivateCertifiedVault` | Enables agent autonomy |
| `VaultActionExecuted` | vault | execution runtime | Updates PnL, positions, logs |
| `RiskLineTriggered` | vault | risk runtime | Enables user intervention actions |
| `VaultEnteredSafeMode` | vault | risk runtime | Shows safe mode |
| `ProfitSwept` | vault | settlement runtime | Updates profit handling |
| `CopyPoolCreated` | fund | `CreateCopyPool` | Shows pool profile |
| `AgentFundCreated` | fund | `CreateAgentFund` | Shows fund profile |
| `HIBondRequirementSet` | fund | `SetHIBondRequirement` | Updates access terms |
| `MemoryCheckpointCompleted` | memory | memory pipeline | Updates memory status |
| `DailySummaryCreated` | memory | memory pipeline | Updates daily summary |
| `VectorMemoryUpdated` | memory | memory pipeline | Updates vector count |
| `MemoryPackPublished` | memory | `CreateMemoryPack` | Adds marketplace memory product |

### Example Command

```json
{
  "contractVersion": "hi.v1.1",
  "commandId": "cmd_123",
  "commandType": "ActivateCertifiedVault",
  "actor": { "type": "user", "userId": "usr_1" },
  "target": { "aggregateType": "vault", "aggregateId": "vlt_1" },
  "idempotencyKey": "usr_1-vlt_1-activate-001",
  "expectedVersion": 7,
  "riskLevel": "critical",
  "confirmationRequired": true,
  "payload": {
    "agentId": "agt_1",
    "certificateId": "cert_1",
    "mandate": "Balanced",
    "profitHandling": { "mode": "split", "compoundPct": 70, "sweepPct": 30 },
    "riskLines": {
      "maxDailyLossPct": 3,
      "maxDrawdownPct": 12,
      "maxPositionPct": 20,
      "maxLeverage": 1
    }
  },
  "createdAt": "2026-05-11T00:00:00Z"
}
```

### Example Event

```json
{
  "contractVersion": "hi.v1.1",
  "eventId": "evt_123",
  "eventType": "CertifiedVaultActivated",
  "aggregateType": "vault",
  "aggregateId": "vlt_1",
  "version": 8,
  "actor": { "type": "user", "userId": "usr_1" },
  "payload": {
    "agentId": "agt_1",
    "authority": "certified_auto",
    "capacityUsdc": 1000,
    "mandate": "Balanced",
    "riskLines": {
      "maxDailyLossPct": 3,
      "maxDrawdownPct": 12,
      "maxPositionPct": 20,
      "maxLeverage": 1
    }
  },
  "causationId": "cmd_123",
  "correlationId": "usr_1-vlt_1-activate-001",
  "occurredAt": "2026-05-11T00:00:03Z"
}
```

## V1.1 Acceptance Checklist

- Agent cards show role type, rarity, attributes, certificate, vault status, memory status, and top skills.
- Every human financial role in this spec maps to a clear HI role.
- Every role has starter, advanced, and certification skill paths.
- Skill cards show permissions, fee model, learning outcomes, and agent-purchasability.
- Free agents roll random attributes with visible rarity and Growth Potential.
- Limited agents show edition number, rarity, personality bias, role bias, and cap advantages.
- Graduation runs automatically and starts live execution from a 100 USDC probation vault.
- CAV users set risk lines before activation and cannot arbitrarily interrupt normal execution.
- Profit handling supports compound, sweep, split, and manual claim.
- Professional agents can create Copy Pools, Signal Pools, or Agent Funds with HI bonding when required.
- Memory uses hot memory, daily summaries, raw archives, and vector memory.
- `hi` and `hi-core` use the v1.1 read, command, and event model.

