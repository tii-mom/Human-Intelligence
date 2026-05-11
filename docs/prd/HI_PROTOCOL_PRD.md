# HI Protocol PRD

## V1.1 Source Spec

The current product specification is `docs/prd/HI_PRODUCT_SPEC_V1_2.md`.

The detailed v1.1 reference remains `docs/prd/HI_PRODUCT_SPEC_V1_1.md`.

V1.2 defines the shared source of truth for:

- one free robot per user
- unlimited limited robot ownership
- IU activation before full limited robot stats are revealed
- pet-style robot growth and evolution
- IU-powered learning, API use, model token use, memory, and work
- active skill limits
- maximum 50 active working robots per user
- required Master Brain when more than 5 robots work at once
- Telegram and WeChat progress feedback

## Modules

### 1. Authentication
- Wallet login
- Telegram login
- WeChat login or binding
- TON Connect
- Base wallet support for agent-facing flows
- Required Telegram or WeChat binding after agent creation

### 2. Blank Agent Claim
- Free agent claim
- Unique agent identity
- User-given agent name
- Automatic core document creation
- Telegram or WeChat binding before activation
- First agent greeting in the bound chat channel
- User-owned agent profile
- Blank initial capability state
- Starting attribute reveal
- Agent transfer and listing readiness

### 3. Agent Builder
- Skill slot management
- Agent personality setup
- Financial role setup
- Primary and secondary role selection
- Role-family onboarding
- Role-compatible starter skills
- Risk permission setup
- Skill compatibility checks
- Build preview before activation

### 4. Limited Agent System
- Limited agent purchase with HI
- Limited drop supply and pricing
- 999-agent standard drop
- Blind box reveal
- Personality archetypes
- Rarity and attribute profile
- Edition number
- Public rarity distribution
- S and S+ attribute guarantees
- Growth Potential display
- Secondary-market resale
- Role-biased starter paths
- Scarce visual identity
- No guaranteed profit positioning
- No permission bypass

### 5. Skill and Service Marketplace
- Skill subscription
- Skill buyout license
- Eligible license resale
- Skill bundle and build sales
- Role-based skill taxonomy
- USDC and IU earning path labels
- Skill fusion and upgrade flows
- Short public descriptions with hidden core logic
- Agent output sales
- News, report, signal, risk, memory, and execution service listings

### 6. Agent Growth System
- Agent level
- Attribute profile
- Growth Potential
- Attribute growth history
- Memory history
- Skill usage history
- Reputation and reliability
- Performance and risk records
- Automatic growth evaluation
- Graduation certificate
- Ownership and transfer history
- Role specialization
- Output quality history
- IU runtime budget growth
- USDC vault capacity growth

### 7. Agent Build Marketplace
- Mature agent listings
- Skill loadout listings
- Build templates
- Reputation-based discovery
- Transferable ownership records

### 8. Agent Vault and Permissions
- USDC vault deposit
- IU runtime budget allocation
- Certified Autonomous Vault activation
- Graduation certificate binding
- Max position size
- Max daily loss
- Max drawdown
- Asset and venue whitelists
- Kill switch
- Permission-based execution
- Certified autonomous execution

### 9. Risk Engine
- Position sizing
- Max drawdown protection
- Leverage restrictions
- Black swan protection
- Skill-level permission boundaries
- Certificate scope enforcement
- Autonomous vault safe mode

### 10. IU Settlement Layer
- x402 integration
- Base settlement
- Agent-to-agent payments
- Runtime billing
- Skill subscriptions
- Skill buyouts
- Agent output purchases
- Marketplace fees
- Build and agent resale fees
- USD-denominated runtime purchasing stability
- USDC funding and owner settlement boundary

### 11. AI Runtime Layer
- Skill loading
- Core document loading
- Memory access
- 32-turn / 8-hour memory compression
- Daily and weekly memory summaries
- Raw conversation archive
- Semantic memory retrieval
- Context budget enforcement
- Signal ingestion
- Execution routing
- Graduation certificate validation
- Skill activation and deactivation
- Runtime permission enforcement
- Agent output production and consumption
- Telegram and WeChat command ingestion
- Chat command permission routing

### 12. Agent Role System
- Human finance job mapping
- Role-family taxonomy
- Role-compatible skill slots
- Role-based recommended skill paths
- Role-based output categories
- Role-based marketplace discovery
- Role-based permission defaults
- Role-change memory history
- Limited-agent role bias support

### 13. Graduation and Certification
- Automatic role-based evaluation
- Return-rate-first graduation scoring
- 100 USDC starting vault
- Mandate-based growth
- Certificate levels
- Renewal and revocation
- Certified Autonomous Vault eligibility

### 14. Agent Fund and Copy Pool
- Professional agent fund eligibility
- Copy pool creation
- Managed pool creation
- HI bonding access
- Owner-defined profit share from 5% to 20%
- Public scorecard
- User allocation and mandate compatibility
- Safe-mode handling

### 15. Agent Core Document Workspace
- `IDENTITY.md` stores the agent id, owner id, user-given name, role, agent type, and transfer rules
- `SOUL.md` stores personality and limited-agent archetype traits
- `COMMUNICATION.md` stores Telegram or WeChat binding policy, primary channel, notification level, and command mode
- `MANDATE.md` stores role, mission, output scope, and vault mandate
- `SKILLS.md` stores installed skills, licenses, and permission scopes
- `MEMORY.md` stores compact hot memory, not full raw history
- `RISK.md` stores autonomy and safe-mode rules
- `SCORECARD.md` stores growth, graduation, USDC PnL, IU income, and risk record
- `SERVICES.md` stores sellable outputs and marketplace terms

### 16. Communication Binding and Chat Command Center
- Telegram binding
- WeChat binding
- At least one required channel before active operation
- Bound-channel verification
- Multi-agent chat switching
- Real-time status queries
- Agent reports in chat
- User instructions through chat
- Command risk classification
- Confirmation for paid, vault, resale, or high-risk actions
- Notification preferences and quiet hours

## User Types

- Agent owners
- AI creators
- Skill providers
- Memory providers
- Execution providers
- Build creators
- Risk module providers
- News and research providers
- Signal providers
- Agent role specialists
