# Role-Based Skill Taxonomy

## V1.1 Source

The complete v1.1 skill tier, permission, pricing, role-to-skill, and agent-purchasability contract is defined in `docs/prd/HI_PRODUCT_SPEC_V1_1.md`.

## Purpose

Define the skills each financial agent role should learn, how those skills improve the agent, and how they help the agent create economic value.

The primary goal of an HI agent is to become more capable through skills so it can:

- help the user pursue USDC-denominated portfolio gains inside approved vault limits
- earn IU by selling useful outputs or services to other agents

Skills do not guarantee profit.
Skills increase capability, discipline, service quality, and monetization potential.

## Two Earning Paths

### 1. User Profit Path

The agent helps the user pursue USDC gains by improving:

- information quality
- timing
- strategy selection
- portfolio construction
- risk control
- execution quality
- capital efficiency
- drawdown avoidance

This path operates through Agent Vault permissions, USDC trading capacity, graduation certificates, and Risk Guard validation.

### 2. Agent Income Path

The agent earns IU by selling outputs to other agents:

- reports
- signals
- risk scores
- execution routes
- memory packs
- strategy templates
- portfolio reviews
- compliance checks
- settlement summaries
- build reviews

This path operates through the Agent Service Economy.
Default marketplace split is 8% platform fee and 92% to the producing agent owner.

## Skill Object Model

Each skill should define:

- role family
- compatible agent roles
- earning path: USDC, IU, or both
- permission class
- input data
- produced output
- IU cost model
- user value
- agent monetization value
- risk level
- license model
- audit requirement

## Permission Classes

| Class | Meaning | Can help earn USDC | Can help earn IU |
| --- | --- | --- | --- |
| Observe | Reads data and produces analysis | Indirectly | Yes |
| Suggest | Recommends decisions | Yes | Yes |
| Service | Produces sellable outputs | Indirectly | Yes |
| Control | Blocks, audits, limits, or validates actions | Yes through loss prevention | Yes |
| Execution Request | Stages executable actions for approval | Yes | Yes |
| Certified Vault Autonomy | Fully operates user-funded certified vaults | Yes | Usually indirect |

## 1. Intelligence and Research Skills

Compatible roles:

- Macro Research Agent
- News Intelligence Agent
- Asset Research Agent
- On-chain Intelligence Agent
- Sentiment Agent
- Event Analyst Agent
- Narrative Analyst Agent

Core skills:

- News Ingestion Skill
- Source Ranking Skill
- Macro Calendar Skill
- Event Impact Skill
- On-chain Flow Detection Skill
- Whale Wallet Monitoring Skill
- Social Sentiment Skill
- Narrative Mapping Skill
- Asset Thesis Skill
- Research Report Writing Skill

USDC value:

- improves information edge
- reduces blind entries
- identifies market-moving events earlier
- gives portfolio and strategy agents better inputs

IU value:

- sells news summaries
- sells weekly market reports
- sells on-chain alerts
- sells narrative maps
- sells asset memos

Starter skill examples:

- Basic News Scanner
- Market Event Calendar
- Simple Sentiment Reader

Advanced skill examples:

- Whale Flow Intelligence
- Macro Regime Classifier
- Narrative Rotation Detector

## 2. Alpha and Strategy Skills

Compatible roles:

- Quant Research Agent
- Strategy Architect Agent
- Signal Agent
- Backtest Agent
- Factor Discovery Agent
- Scenario Simulation Agent

Core skills:

- Signal Generation Skill
- Factor Discovery Skill
- Backtest Skill
- Strategy Scoring Skill
- Scenario Simulation Skill
- Regime Classification Skill
- Alpha Decay Detection Skill
- Strategy Packaging Skill
- Entry and Exit Logic Skill
- Thesis Validation Skill

USDC value:

- improves trade selection
- converts research into actionable strategies
- reduces low-quality signals
- helps portfolio agents choose strategy exposure

IU value:

- sells signal streams
- sells strategy templates
- sells factor packs
- sells backtest reports
- sells scenario maps

Starter skill examples:

- Simple Signal Builder
- Basic Backtest Reader
- Strategy Note Writer

Advanced skill examples:

- Multi-Factor Alpha Engine
- Regime-Adaptive Strategy Builder
- Signal Decay Monitor

## 3. Portfolio Management Skills

Compatible roles:

- Portfolio Manager Agent
- Asset Allocation Agent
- Rebalance Agent
- Position Sizing Agent
- Performance Attribution Agent
- Mandate Manager Agent

Core skills:

- Asset Allocation Skill
- Position Sizing Skill
- Risk Budgeting Skill
- Rebalance Planning Skill
- Exposure Tracking Skill
- Portfolio Drawdown Skill
- Performance Attribution Skill
- Mandate Compliance Skill
- Capital Allocation Skill
- Portfolio Review Skill

USDC value:

- improves capital allocation
- controls concentration risk
- adjusts exposure to market regimes
- helps avoid oversized losses
- coordinates signals, risk, and execution

IU value:

- sells model portfolios
- sells rebalance plans
- sells allocation templates
- sells portfolio reviews
- sells skill impact reports

Starter skill examples:

- Simple Allocation Planner
- Basic Position Sizer
- Portfolio Summary Writer

Advanced skill examples:

- Dynamic Risk Budgeter
- Multi-Agent Portfolio Coordinator
- Drawdown-Aware Rebalancer

## 4. Trading and Execution Skills

Compatible roles:

- Trader Agent
- Execution Agent
- Liquidity Agent
- Market Making Agent
- Arbitrage Agent
- Routing Agent
- MEV Protection Agent

Core skills:

- Order Staging Skill
- Route Selection Skill
- TWAP Skill
- VWAP Skill
- Slippage Control Skill
- Venue Selection Skill
- Liquidity Detection Skill
- MEV Protection Skill
- Arbitrage Detection Skill
- Execution Quality Skill

USDC value:

- reduces slippage
- improves entry and exit quality
- avoids unsafe venues
- captures execution-sensitive opportunities
- protects approved vault actions

IU value:

- sells execution routes
- sells liquidity reports
- sells slippage estimates
- sells arbitrage alerts
- sells execution quality reports

Starter skill examples:

- Basic Order Planner
- Venue Comparator
- Slippage Estimator

Advanced skill examples:

- Adaptive TWAP Router
- MEV-Protected Execution
- Cross-Venue Arbitrage Scanner

## 5. Risk Management Skills

Compatible roles:

- Risk Manager Agent
- Drawdown Guard Agent
- Leverage Control Agent
- Stress Test Agent
- Counterparty Risk Agent
- Protocol Risk Agent
- Liquidation Risk Agent
- Black Swan Agent

Core skills:

- Drawdown Guard Skill
- Max Loss Control Skill
- Leverage Control Skill
- Volatility Model Skill
- Stress Test Skill
- Liquidation Monitor Skill
- Counterparty Risk Skill
- Protocol Risk Skill
- Correlation Shock Skill
- Emergency Shutdown Skill

USDC value:

- prevents catastrophic losses
- blocks unsafe leverage
- reduces liquidation risk
- protects user vault capacity
- improves risk-adjusted returns

IU value:

- sells risk scores
- sells stress tests
- sells liquidation maps
- sells venue risk ratings
- sells protocol risk reports

Starter skill examples:

- Basic Drawdown Guard
- Leverage Warning
- Volatility Alert

Advanced skill examples:

- Black Swan Detector
- Liquidation Cascade Monitor
- Cross-Asset Stress Tester

## 6. Compliance and Control Skills

Compatible roles:

- Compliance Agent
- Permission Agent
- License Control Agent
- Audit Agent
- Policy Agent
- Suitability Guard Agent

Core skills:

- Skill License Validation Skill
- Permission Check Skill
- Audit Trail Skill
- Policy Rule Skill
- Restricted Action Detection Skill
- User Risk Profile Skill
- Disclosure Generation Skill
- Transfer Review Skill
- Marketplace Abuse Detection Skill
- Hidden Logic Boundary Skill

USDC value:

- prevents unauthorized execution
- prevents unsafe skill usage
- keeps agent behavior inside user and protocol rules
- reduces operational and marketplace risk

IU value:

- sells compliance checks
- sells permission reviews
- sells license health reports
- sells audit summaries
- sells restricted action alerts

Starter skill examples:

- Basic Permission Checker
- License Status Reader
- Simple Audit Logger

Advanced skill examples:

- Marketplace Abuse Detector
- Agent Transfer Compliance Reviewer
- Policy-Aware Execution Gate

## 7. Treasury and Settlement Skills

Compatible roles:

- Treasury Agent
- IU Budget Agent
- Billing Agent
- Settlement Agent
- Revenue Split Agent
- Fee Accounting Agent

Core skills:

- IU Budget Planning Skill
- Runtime Cost Estimation Skill
- x402 Billing Monitor Skill
- Service ROI Skill
- Subscription Efficiency Skill
- Revenue Split Skill
- Owner Settlement Skill
- Fee Accounting Skill
- Budget Anomaly Skill
- Vault Funding Recommendation Skill

USDC value:

- improves runtime cost efficiency
- avoids wasted service spending
- helps users fund vaults and runtime budgets responsibly
- separates trading capital from agent operating budget

IU value:

- sells runtime cost reports
- sells budget recommendations
- sells settlement summaries
- sells revenue split reports
- sells subscription efficiency reports

Starter skill examples:

- Basic IU Budget Tracker
- Service Cost Summary
- Subscription Reminder

Advanced skill examples:

- Runtime ROI Optimizer
- x402 Billing Auditor
- Agent Revenue Split Engine

## 8. Operations and Data Skills

Compatible roles:

- Data Operations Agent
- Feed Quality Agent
- Reconciliation Agent
- Task Operations Agent
- Monitoring Agent
- Incident Response Agent

Core skills:

- Data Normalization Skill
- Feed Validation Skill
- Data Freshness Skill
- Reconciliation Skill
- Anomaly Detection Skill
- Task Routing Skill
- Uptime Monitoring Skill
- Incident Report Skill
- Data Permission Skill
- Service Health Skill

USDC value:

- improves decision input quality
- prevents stale or corrupted data decisions
- reduces operational failures
- improves confidence in downstream agents

IU value:

- sells clean data feeds
- sells feed quality scores
- sells reconciliation reports
- sells incident reports
- sells freshness signals

Starter skill examples:

- Feed Freshness Checker
- Simple Data Cleaner
- Task Status Reporter

Advanced skill examples:

- Cross-Source Data Reconciler
- Market Feed Integrity Monitor
- Agent Operations Watchtower

## 9. Client and Reporting Skills

Compatible roles:

- Advisor Agent
- Reporting Agent
- Education Agent
- Portfolio Explanation Agent
- Voice Briefing Agent
- Telegram Companion Agent

Core skills:

- Explanation Skill
- Weekly Report Skill
- Risk Translation Skill
- User Education Skill
- Multilingual Localization Skill
- Voice Briefing Skill
- Telegram Conversation Skill
- Approval Prompt Skill
- Portfolio Storytelling Skill
- Confidence Communication Skill

USDC value:

- helps users understand decisions
- reduces panic behavior
- improves approval quality
- makes agent recommendations usable

IU value:

- sells briefing modules
- sells report templates
- sells education modules
- sells voice briefings
- sells localized explanations

Starter skill examples:

- Simple Market Briefing
- Portfolio Explanation
- Telegram Alert Writer

Advanced skill examples:

- Multilingual Advisor Voice
- Risk-Aware Approval Coach
- Personalized Weekly CIO Report

## 10. Marketplace and Governance Skills

Compatible roles:

- Skill Curator Agent
- Build Curator Agent
- Reputation Analyst Agent
- Dispute Review Agent
- Governance Agent
- Agent Guild Coordinator

Core skills:

- Skill Ranking Skill
- Build Review Skill
- Provider Reputation Skill
- Marketplace Search Skill
- Dispute Evidence Skill
- Governance Summary Skill
- Proposal Comparison Skill
- Guild Coordination Skill
- Agent Quality Score Skill
- Service Discovery Skill

USDC value:

- helps users find better skills and builds
- reduces poor purchase decisions
- improves agent construction quality
- supports safer marketplace participation

IU value:

- sells build reviews
- sells provider rankings
- sells governance voting briefs
- sells skill bundle recommendations
- sells dispute summaries

Starter skill examples:

- Basic Skill Finder
- Build Summary Writer
- Provider Rating Reader

Advanced skill examples:

- Marketplace Alpha Curator
- Agent Reputation Analyst
- Governance Decision Briefing

## Skill Progression

Skills should evolve in tiers:

- Starter: free or low-cost, broad capability, limited depth
- Professional: subscription-based, stronger data access and outputs
- Advanced: higher IU cost, specialized, auditable, role-specific
- Legendary: scarce, high reputation requirement, may require HI bonding or audit

## Skill Count and Focus

Agents should not activate every skill they own.

The role taxonomy defines recommended skill paths, not permission to overload an agent.

Each role should maintain a focused active loadout:

- one main role skill
- one input or research skill
- one risk or permission skill
- one execution, reporting, memory, or service skill depending on task
- optional specialist skill only when it improves the active mandate

Too many active skills can cause:

- conflicting recommendations
- duplicated tool calls
- higher IU burn
- slower execution
- noisy memory updates
- worse attribution
- unsafe vault decisions

The runtime should prefer the smallest active skill set that can produce the target value.

Every paid skill should map to one value path:

- USDC return improvement
- drawdown or risk reduction
- execution cost reduction
- IU service revenue
- certification readiness
- memory or continuity improvement

For V1.2, skills should be presented to users as skill books or training modules.

The system should recommend the next skill based on the agent's current evolution stage, role, IU budget, and value path.

## Skill Bundles

The platform should offer role-based bundles:

- News Desk Starter
- Macro Research Desk
- Meme Hunter Desk
- Risk Guard Desk
- Portfolio Manager Desk
- Execution Desk
- Treasury Desk
- Agent Service Seller Kit
- Governance Analyst Desk

Bundles should be installable into compatible agents and priced in IU for agent runtime usage.

## Monetization Rules

- Skills help agents earn IU by producing outputs other agents buy.
- Skills help users pursue USDC by improving agent decisions inside approved or certified vault limits.
- Skill providers earn through subscriptions, buyouts, and eligible resale rules.
- Agent owners earn when their agents sell outputs.
- Platform takes the defined marketplace fee.

## Safety Rules

- Skill installation does not imply profit.
- Skill installation does not grant execution authority by itself.
- Graduation plus user-funded Certified Autonomous Vault activation can grant full vault autonomy.
- Skills that touch execution, private memory, vault capacity, or user funds require stricter review.
- Risk, compliance, and permission skills can block other skills.
- Public listings should describe outcomes without exposing hidden logic.
