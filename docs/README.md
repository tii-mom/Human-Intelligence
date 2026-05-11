# HI Documentation Index

## Latest Product Source

The current source of truth is `docs/prd/HI_PRODUCT_SPEC_V1_1.md`.

Use it first when updating product, frontend, backend, agent, skill, vault, memory, or integration behavior.

V1.1 defines:

- Agent Role System v1.1
- Skill Taxonomy v1.1
- Agent Attribute System v1.1
- Graduation and Certification v1.1
- Vault, Fund, and Copy Pool v1.1
- Memory and Backend Config v1.1
- Integration Contract for `hi` and `hi-core`

## Product Specs

- `docs/prd/HI_PRODUCT_SPEC_V1_1.md` - current product and integration source
- `docs/prd/HI_PROTOCOL_PRD.md` - module-level PRD
- `MVP_PRODUCT_SPEC.md` - MVP scope and non-live trading boundary
- `docs/vision/HI_PROTOCOL_VISION.md` - product vision
- `docs/roadmap/HI_ROADMAP.md` - phased roadmap

## Agent System

- `docs/agents/HI_AGENT_SYSTEM.md` - agent system overview
- `docs/agents/BLANK_AGENT_PRODUCT_LOOP.md` - blank agent lifecycle
- `docs/agents/BLANK_AGENT_OWNERSHIP.md` - ownership and transfer rules
- `docs/agents/AGENT_ROLE_SYSTEM.md` - human finance role mapping
- `docs/agents/AGENT_ATTRIBUTE_SYSTEM.md` - rarity, attributes, and FOMO rules
- `docs/agents/AGENT_GRADUATION_CERTIFICATE.md` - automatic graduation and certification
- `docs/agents/LIMITED_AGENT_SYSTEM.md` - limited agent product rules
- `docs/agents/LIMITED_AGENT_DROP_MECHANISM.md` - drop, reveal, and guarantee mechanism

## Skills and Economy

- `docs/skills/ROLE_BASED_SKILL_TAXONOMY.md` - role-based skill map
- `docs/skills/HI_SKILL_ECONOMY.md` - skill economy overview
- `docs/skills/SKILL_AND_SERVICE_MARKETPLACE.md` - skill and output marketplace
- `docs/skills/SKILL_LICENSING_AND_DISCLOSURE.md` - licensing and disclosure rules
- `docs/economy/SKILL_RUNTIME_SYSTEM.md` - skill runtime behavior
- `docs/economy/AGENT_SERVICE_ECONOMY.md` - agent-to-agent output economy
- `docs/economy/AGENT_FUND_AND_COPY_POOL.md` - copy pool, signal pool, and agent fund rules
- `docs/economy/SOCIAL_FINANCIAL_LAYER.md` - social discovery and reputation layer
- `docs/economy/TOKEN_ECONOMY_V2.md` - economic model

## Runtime and Backend

- `docs/architecture/HI_PROTOCOL_ARCHITECTURE.md` - architecture overview
- `docs/runtime/AGENT_CORE_DOCUMENTS.md` - per-agent core document package
- `docs/runtime/AGENT_BACKEND_CONFIGURATION.md` - Cloudflare backend configuration
- `docs/runtime/AGENT_MEMORY_COMPRESSION_PIPELINE.md` - memory compression pipeline
- `docs/runtime/AI_MEMORY_ARCHITECTURE.md` - memory architecture overview
- `docs/runtime/AI_AGENT_RUNTIME.md` - agent runtime
- `docs/runtime/AI_PERMISSION_SYSTEM.md` - permission system
- `docs/runtime/EXECUTION_ENGINE.md` - execution engine
- `docs/runtime/AGENT_VAULT_AND_PERMISSION_MODEL.md` - vault permissions
- `docs/runtime/CERTIFIED_AUTONOMOUS_VAULT.md` - certified autonomous vault
- `docs/runtime/IU_SETTLEMENT_ARCHITECTURE.md` - IU settlement architecture
- `docs/runtime/WALLET_SECURITY_SYSTEM.md` - wallet and vault security
- `docs/runtime/AGENT_COMMUNICATION_BINDING.md` - Telegram and WeChat binding
- `docs/runtime/AGENT_CHAT_COMMAND_GATEWAY.md` - chat command routing

## Frontend

- `docs/frontend/FRONTEND_SYSTEM.md` - frontend product shell
- `docs/frontend/DESIGN_SYSTEM.md` - visual system
- `docs/frontend/AI_TERMINAL_SPEC.md` - agent terminal
- `docs/frontend/TELEGRAM_WEBVIEW_SPEC.md` - Telegram webview
- `docs/frontend/MOBILE_EXPERIENCE_SPEC.md` - mobile experience
- `docs/frontend/AGENT_BUILD_MARKETPLACE.md` - build marketplace
- `docs/frontend/SKILL_VISUALIZATION.md` - skill visualization
- `docs/frontend/RISK_ENGINE_UI.md` - risk UI
- `docs/frontend/PORTFOLIO_INTELLIGENCE_SPEC.md` - portfolio intelligence
- `docs/frontend/AI_MEMORY_SYSTEM.md` - memory UI
- `docs/frontend/AI_NOTIFICATION_SYSTEM.md` - notifications
- `docs/frontend/AI_TIMELINE_SYSTEM.md` - timeline
- `docs/frontend/AI_CONSENSUS_UI.md` - consensus UI
- `docs/frontend/AGENT_PERSONALITY_SYSTEM.md` - personality UI
- `docs/frontend/AGENT_REPUTATION_SYSTEM.md` - reputation UI
- `docs/frontend/VOICE_AGENT_SYSTEM.md` - voice agent
- `docs/frontend/AMBIENT_INTELLIGENCE_SYSTEM.md` - ambient intelligence
- `docs/frontend/MOTION_SYSTEM.md` - motion
- `docs/frontend/MULTILINGUAL_SYSTEM_SPEC.md` - multilingual rules

## Data, Governance, Tokenomics, Security

- `docs/data/AI_MARKET_DATA_LAYER.md` - market data layer
- `docs/governance/ONCHAIN_AGENT_IDENTITY.md` - on-chain identity
- `docs/governance/AGENT_GUILD_SYSTEM.md` - guilds
- `docs/governance/CONSENSUS_MINING.md` - consensus mining
- `docs/governance/AI_ETHICS_AND_SAFETY.md` - safety principles
- `docs/tokenomics/HI_TOKENOMICS.md` - HI tokenomics
- `docs/tokenomics/IU_RUNTIME_CREDIT_MODEL.md` - IU runtime credit model
- `docs/security/HI_SECURITY.md` - security model

## Maintenance Rules

- Update `docs/prd/HI_PRODUCT_SPEC_V1_1.md` first when requirements change.
- Keep subsystem docs consistent with the V1.1 source spec.
- Do not describe HI as a generic copy-trading dashboard.
- Do not imply agents control user primary wallets.
- Describe autonomous trading as scoped Certified Autonomous Vault operation.
- Keep raw memory archives as source of truth; summaries and vectors are derived indexes.

