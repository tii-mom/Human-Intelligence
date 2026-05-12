# hi / hi-core Implementation Backlog v1.2

## Purpose

Translate V1.2 product rules into an implementation backlog for `hi` and `hi-core`.

This backlog is scoped to the MVP cultivation loop:

```text
claim robot
  -> name robot
  -> bind channel
  -> activate monthly
  -> convert IU into Compute Tokens
  -> learn starter skills
  -> run mock task
  -> update memory and scorecard
  -> show growth and money path
```

References:

- `docs/prd/HI_PRODUCT_RULES_V1_2.md`
- `docs/prd/MVP_USER_JOURNEY_V1_2.md`
- `MVP_PRODUCT_SPEC.md`
- `docs/prd/HI_PRODUCT_SPEC_V1_1.md`
- `docs/prd/HI_PRODUCT_SPEC_V1_2.md`

## Product Boundary

### In MVP

- one free Blank Robot claim
- limited robot preview and awakening mock
- robot naming
- core document pack creation
- Telegram or WeChat binding mock
- 9.99 IU monthly activation state
- IU to Compute Token conversion ledger
- Compute Token balance and daily cap
- starter skill install
- active skill slot display
- mock task execution
- mock report output
- memory summary update
- scorecard update
- vault preview
- certification progress preview

### Out Of MVP

- live autonomous trading
- real exchange execution
- real Certified Autonomous Vault activation
- real x402 settlement
- real on-chain IU settlement
- open DEX trading UX
- full fund or copy-pool production
- unlimited skill marketplace
- full Telegram or WeChat production app approval flow

## Ownership Boundary

`hi` owns user-facing experience:

- pages and navigation
- robot cards
- onboarding flow
- skill cards
- activation and Compute Token UI
- task and report UI
- wallet/channel binding UX
- optimistic pending states after command acceptance

`hi-core` owns source of truth:

- command validation
- idempotency
- event emission
- read model projection
- lifecycle state
- activation and Compute Token ledger
- core document generation
- memory jobs
- scorecard updates
- risk and permission checks
- task execution mock runtime

## Delivery Order

| Phase | Goal | User-visible outcome |
| --- | --- | --- |
| P0 | Contract and seed data | frontend can render robots from read models |
| P1 | Claim, name, and document pack | user owns a named robot |
| P2 | Channel binding mock | robot can become active through Telegram/WeChat placeholder |
| P3 | Activation and Compute Tokens | user sees 9.99 IU/month and runtime fuel |
| P4 | Starter skills | user can train the robot with a small path |
| P5 | Mock task execution | robot produces a useful report and spends Compute Tokens |
| P6 | Memory and scorecard | robot appears to learn and grow |
| P7 | Vault and graduation preview | user sees money path without live trading |
| P8 | Limited robot awakening | HI-purchased robot reveal flow is represented |
| P9 | Master Brain preview | multi-robot orchestration model is visible but mocked |

## Frontend Pages

### My Robots

Route:

```text
/robots
```

Responsibilities:

- show owned robots
- enforce one free robot claim CTA
- show limited robot shells
- show stage, level, rarity, top attributes, Growth Potential
- show monthly activation state
- show Compute Token balance
- show current job and next evolution
- show sealed, dormant, active, working, paused, or listed state

Read models:

- `RobotCardReadModel`
- `UserRuntimeWalletReadModel`

Commands:

- `ClaimFreeAgent`
- `NameAgent`
- `RevealLimitedAgent`
- `RenewRobotMonthlyActivation`

MVP mock:

- local seeded limited drops
- deterministic free robot attribute roll
- no real HI purchase

### Robot Detail

Route:

```text
/robots/:agentId
```

Responsibilities:

- show identity, attributes, stage, active skills, memory status, scorecard
- show current runtime state
- show bound communication channel
- show next recommended action
- expose tabs: Overview, Skills, Work, Memory, Risk, Vault Preview

Read models:

- `AgentReadModel`
- `AgentCoreDocumentStatusReadModel`
- `RuntimeReadModel`

Commands:

- `SetPrimaryRole`
- `ToggleSelfLearning`
- `SetComputeTokenBudget`

MVP mock:

- generated markdown document previews
- static role recommendations

### Claim And Name Flow

Route:

```text
/robots/claim
```

Responsibilities:

- claim one free Blank Robot
- name robot
- show starting attributes
- create core document pack
- send user to channel binding

Read models:

- `FreeClaimEligibilityReadModel`
- `AgentReadModel`

Commands:

- `ClaimFreeAgent`
- `NameAgent`
- `CreateAgentCoreDocuments`

MVP mock:

- wallet/account identity can be mocked
- duplicate free claim blocked in local/server state

### Channel Binding

Route:

```text
/robots/:agentId/bind
```

Responsibilities:

- show Telegram and WeChat options
- mock binding verification
- set primary channel
- show first robot greeting

Read models:

- `CommunicationBindingReadModel`

Commands:

- `BindCommunicationChannel`

MVP mock:

- no real Telegram bot required
- no real WeChat Official Account required
- show placeholder external account reference

### Train

Route:

```text
/train/:agentId
```

Responsibilities:

- show Basic, Advanced, Expert skill books
- show starter skill path
- show active skill slots
- explain value path for each skill
- install starter skills
- preview Compute Token cost

Read models:

- `SkillCatalogReadModel`
- `AgentSkillLoadoutReadModel`

Commands:

- `InstallSkill`
- `UninstallSkill`
- `SetComputeTokenBudget`

MVP mock:

- fixed catalog with 8 starter skills
- no real paid marketplace
- no hidden skill execution logic

### Runtime Wallet

Route:

```text
/runtime
```

Responsibilities:

- show IU balance
- show monthly activation cost
- show Compute Token conversion
- show Compute Token balance
- show daily cap and low-balance pause
- show conversion and spending history

Read models:

- `UserRuntimeWalletReadModel`
- `RuntimeLedgerReadModel`

Commands:

- `RenewRobotMonthlyActivation`
- `ConvertIUToComputeTokens`
- `SetComputeTokenBudget`

MVP mock:

- fake IU top-up
- no real on-chain settlement
- fixed conversion rate

### Workroom

Route:

```text
/workroom/:agentId
```

Responsibilities:

- start a mock task
- show estimated Compute Token cost
- show task progress
- show generated report
- update scorecard and memory preview
- show task history

Read models:

- `TaskThreadReadModel`
- `AgentReadModel`
- `RuntimeReadModel`

Commands:

- `CreateTaskThread`
- `RunMockAgentTask`
- `CancelTaskThread`

MVP mock:

- deterministic report templates
- simulated progress states
- Compute Token reserve/consume/release events

### Earnings And Review

Route:

```text
/earnings
```

Responsibilities:

- show simulated PnL
- show IU earned
- show Compute Tokens spent
- show service revenue placeholder
- show risk events
- show graduation progress

Read models:

- `ScorecardReadModel`
- `GraduationProgressReadModel`

Commands:

- `RequestGraduationEvaluation`

MVP mock:

- no real PnL
- simulation-only labels must be visible

### Market

Route:

```text
/market
```

Responsibilities:

- show limited robots
- show skill books
- show user backpack
- show agent outputs placeholder

Read models:

- `LimitedDropReadModel`
- `SkillBookReadModel`
- `BackpackReadModel`

Commands:

- `PurchaseLimitedAgent`
- `RevealLimitedAgent`
- `ListSkillBook`

MVP mock:

- limited robot purchase is preview or fake balance only
- skill-book sale does not settle real IU

### Master Brain Preview

Route:

```text
/master-brain
```

Responsibilities:

- explain why more than 5 working robots require a Master Brain
- show mock task routing
- show worker robots and task threads
- show total Compute Token budget

Read models:

- `MasterBrainReadModel`
- `TaskThreadReadModel`

Commands:

- `AssignMasterBrain`
- `CreateTaskThread`
- `SetComputeTokenBudget`

MVP mock:

- no real multi-agent autonomy
- only preview or simulated thread assignment

## Backend Tables

### users

```sql
users(
  user_id TEXT PRIMARY KEY,
  wallet_ref TEXT,
  free_agent_claimed BOOLEAN NOT NULL DEFAULT 0,
  created_at TEXT NOT NULL,
  updated_at TEXT NOT NULL
);
```

### agents

```sql
agents(
  agent_id TEXT PRIMARY KEY,
  owner_id TEXT NOT NULL,
  display_name TEXT,
  agent_type TEXT NOT NULL,
  acquisition_type TEXT NOT NULL,
  lifecycle_status TEXT NOT NULL,
  growth_stage TEXT NOT NULL,
  level INTEGER NOT NULL DEFAULT 0,
  rarity TEXT,
  primary_role TEXT,
  master_brain_id TEXT,
  active_work_status TEXT,
  created_at TEXT NOT NULL,
  updated_at TEXT NOT NULL
);
```

### agent_attributes

```sql
agent_attributes(
  agent_id TEXT PRIMARY KEY,
  alpha INTEGER NOT NULL,
  risk INTEGER NOT NULL,
  execution INTEGER NOT NULL,
  research INTEGER NOT NULL,
  memory INTEGER NOT NULL,
  charisma INTEGER NOT NULL,
  growth_potential INTEGER NOT NULL,
  caps_json TEXT NOT NULL,
  updated_at TEXT NOT NULL
);
```

### limited_agent_shells

```sql
limited_agent_shells(
  agent_id TEXT PRIMARY KEY,
  owner_id TEXT NOT NULL,
  drop_id TEXT NOT NULL,
  edition_number INTEGER NOT NULL,
  supply INTEGER NOT NULL,
  sealed_state TEXT NOT NULL,
  awakening_cost_iu REAL NOT NULL,
  reveal_payload_json TEXT,
  awakened_at TEXT,
  created_at TEXT NOT NULL
);
```

### agent_documents

```sql
agent_documents(
  agent_id TEXT NOT NULL,
  doc_type TEXT NOT NULL,
  r2_key TEXT NOT NULL,
  version INTEGER NOT NULL,
  status TEXT NOT NULL,
  updated_at TEXT NOT NULL,
  PRIMARY KEY(agent_id, doc_type)
);
```

### communication_bindings

```sql
communication_bindings(
  id TEXT PRIMARY KEY,
  agent_id TEXT NOT NULL,
  user_id TEXT NOT NULL,
  channel TEXT NOT NULL,
  external_user_ref TEXT,
  is_primary BOOLEAN NOT NULL DEFAULT 0,
  status TEXT NOT NULL,
  verified_at TEXT,
  created_at TEXT NOT NULL
);
```

### runtime_accounts

```sql
runtime_accounts(
  agent_id TEXT PRIMARY KEY,
  owner_id TEXT NOT NULL,
  monthly_activation_status TEXT NOT NULL,
  monthly_activation_iu REAL NOT NULL DEFAULT 9.99,
  monthly_activation_renews_at TEXT,
  compute_token_balance INTEGER NOT NULL DEFAULT 0,
  daily_compute_token_limit INTEGER NOT NULL DEFAULT 0,
  low_compute_threshold INTEGER NOT NULL DEFAULT 0,
  self_learning_enabled BOOLEAN NOT NULL DEFAULT 0,
  updated_at TEXT NOT NULL
);
```

### user_runtime_wallets

```sql
user_runtime_wallets(
  user_id TEXT PRIMARY KEY,
  iu_balance REAL NOT NULL DEFAULT 0,
  compute_token_balance INTEGER NOT NULL DEFAULT 0,
  conversion_rate INTEGER NOT NULL DEFAULT 10000000,
  updated_at TEXT NOT NULL
);
```

### runtime_ledger_entries

```sql
runtime_ledger_entries(
  entry_id TEXT PRIMARY KEY,
  user_id TEXT NOT NULL,
  agent_id TEXT,
  entry_type TEXT NOT NULL,
  iu_delta REAL NOT NULL DEFAULT 0,
  compute_token_delta INTEGER NOT NULL DEFAULT 0,
  reason TEXT NOT NULL,
  command_id TEXT,
  event_id TEXT,
  created_at TEXT NOT NULL
);
```

### skills

```sql
skills(
  skill_id TEXT PRIMARY KEY,
  name TEXT NOT NULL,
  user_tier TEXT NOT NULL,
  internal_tier TEXT NOT NULL,
  role_family TEXT NOT NULL,
  permission_scope TEXT NOT NULL,
  value_path TEXT NOT NULL,
  iu_price REAL,
  compute_token_estimate INTEGER,
  purchasable_by_agents BOOLEAN NOT NULL DEFAULT 0,
  active_slot_weight INTEGER NOT NULL DEFAULT 1,
  status TEXT NOT NULL
);
```

### agent_skills

```sql
agent_skills(
  agent_id TEXT NOT NULL,
  skill_id TEXT NOT NULL,
  state TEXT NOT NULL,
  slot_index INTEGER,
  installed_at TEXT NOT NULL,
  updated_at TEXT NOT NULL,
  PRIMARY KEY(agent_id, skill_id)
);
```

### task_threads

```sql
task_threads(
  task_id TEXT PRIMARY KEY,
  owner_id TEXT NOT NULL,
  agent_id TEXT NOT NULL,
  master_brain_id TEXT,
  objective TEXT NOT NULL,
  expected_output TEXT,
  estimate_compute_tokens INTEGER NOT NULL,
  reserved_compute_tokens INTEGER NOT NULL DEFAULT 0,
  consumed_compute_tokens INTEGER NOT NULL DEFAULT 0,
  status TEXT NOT NULL,
  result_ref TEXT,
  created_at TEXT NOT NULL,
  updated_at TEXT NOT NULL
);
```

### agent_scorecards

```sql
agent_scorecards(
  agent_id TEXT PRIMARY KEY,
  return_rate_pct REAL,
  realized_pnl_usdc REAL NOT NULL DEFAULT 0,
  max_drawdown_pct REAL,
  win_rate_pct REAL,
  trades INTEGER NOT NULL DEFAULT 0,
  iu_spent REAL NOT NULL DEFAULT 0,
  iu_earned REAL NOT NULL DEFAULT 0,
  compute_tokens_spent INTEGER NOT NULL DEFAULT 0,
  service_revenue_iu REAL NOT NULL DEFAULT 0,
  risk_events_json TEXT NOT NULL,
  updated_at TEXT NOT NULL
);
```

### memory_status

```sql
memory_status(
  agent_id TEXT PRIMARY KEY,
  hot_message_count INTEGER NOT NULL DEFAULT 0,
  hot_token_estimate INTEGER NOT NULL DEFAULT 0,
  last_compression_at TEXT,
  next_checkpoint_at TEXT,
  daily_summary_ref TEXT,
  archived_conversation_count INTEGER NOT NULL DEFAULT 0,
  vector_memory_count INTEGER NOT NULL DEFAULT 0,
  updated_at TEXT NOT NULL
);
```

### skill_books

```sql
skill_books(
  skill_book_id TEXT PRIMARY KEY,
  owner_id TEXT NOT NULL,
  produced_by_agent_id TEXT,
  source_task_id TEXT,
  name TEXT NOT NULL,
  user_tier TEXT NOT NULL,
  role_family TEXT NOT NULL,
  value_path TEXT NOT NULL,
  listing_status TEXT NOT NULL,
  price_iu REAL,
  created_at TEXT NOT NULL,
  updated_at TEXT NOT NULL
);
```

## Command Backlog

### P1 Identity Commands

| Command | Owner | MVP behavior |
| --- | --- | --- |
| `ClaimFreeAgent` | hi-core | Create free robot if user has no prior free claim |
| `NameAgent` | hi-core | Set display name |
| `CreateAgentCoreDocuments` | hi-core | Create mock R2 document refs and document previews |
| `BindCommunicationChannel` | hi-core | Save mock Telegram or WeChat binding |

### P2 Runtime Commands

| Command | Owner | MVP behavior |
| --- | --- | --- |
| `RenewRobotMonthlyActivation` | hi-core | Deduct mock IU and set active monthly state |
| `ConvertIUToComputeTokens` | hi-core | Convert mock IU at `1 IU = 10,000,000 Compute Tokens` |
| `SetComputeTokenBudget` | hi-core | Set daily cap and task cap |
| `ToggleSelfLearning` | hi-core | Enable or pause self-learning flag |

### P3 Skill Commands

| Command | Owner | MVP behavior |
| --- | --- | --- |
| `InstallSkill` | hi-core | Attach starter skill if slot is available |
| `UninstallSkill` | hi-core | Remove non-locked skill |
| `ProduceSkillBookMock` | hi-core | Create skill book after mock task evidence |
| `ListSkillBook` | hi-core | Mark skill book as listed without real settlement |

### P4 Task Commands

| Command | Owner | MVP behavior |
| --- | --- | --- |
| `CreateTaskThread` | hi-core | Create task with estimate and status |
| `RunMockAgentTask` | hi-core | Reserve tokens, simulate progress, create report, consume tokens |
| `CancelTaskThread` | hi-core | Release unconsumed reserved tokens |

### P5 Growth Commands

| Command | Owner | MVP behavior |
| --- | --- | --- |
| `RunMemoryCheckpoint` | hi-core | Update memory summary fields |
| `UpdateScorecardFromTask` | hi-core | Increment mock task counters and Compute Tokens spent |
| `RequestGraduationEvaluation` | hi-core | Return preview-only certification progress |

### P6 Limited And Master Brain Commands

| Command | Owner | MVP behavior |
| --- | --- | --- |
| `PurchaseLimitedAgent` | hi-core | Create limited shell with fake HI balance |
| `RevealLimitedAgent` | hi-core | Reveal deterministic attributes from seeded payload |
| `AssignMasterBrain` | hi-core | Set coordinator robot |
| `CreateMasterBrainTaskPlan` | hi-core | Create mock worker task threads |

## Event Backlog

Required event stream:

- `AgentClaimed`
- `AgentNamed`
- `CoreDocumentsCreated`
- `CommunicationChannelBound`
- `RobotMonthlyActivationRenewed`
- `IUConvertedToComputeTokens`
- `ComputeTokenBudgetUpdated`
- `SelfLearningToggled`
- `SkillInstalled`
- `SkillUninstalled`
- `TaskThreadCreated`
- `ComputeTokensReserved`
- `TaskThreadStarted`
- `TaskThreadProgressed`
- `MockAgentReportCreated`
- `ComputeTokensConsumed`
- `ComputeTokensReleased`
- `MemoryCheckpointCompleted`
- `ScorecardUpdated`
- `GraduationEvaluated`
- `LimitedAgentPurchased`
- `LimitedAgentRevealed`
- `SkillBookProduced`
- `SkillBookListed`
- `MasterBrainAssigned`
- `MasterBrainTaskPlanCreated`
- `LowComputeBalanceTriggered`

## Read Model Backlog

### RobotCardReadModel

Used by:

- My Robots
- Market
- Master Brain preview

Fields:

- `agentId`
- `displayName`
- `agentType`
- `lifecycleStatus`
- `growthStage`
- `level`
- `rarity`
- `edition`
- `topAttributes`
- `growthPotential`
- `monthlyActivationStatus`
- `computeTokenBalance`
- `activeWorkStatus`
- `nextEvolutionRequirement`

### AgentReadModel

Used by:

- Robot Detail
- Train
- Workroom

Fields:

- fields from `HI_PRODUCT_SPEC_V1_1`
- add `runtime`
- add `activeSkillSlots`
- add `nextRecommendedAction`

### RuntimeReadModel

Used by:

- Runtime Wallet
- Robot Detail
- Task confirmation

Fields:

- `monthlyActivationStatus`
- `monthlyActivationIu`
- `monthlyActivationRenewsAt`
- `iuBalanceAvailable`
- `computeTokenConversionRate`
- `computeTokenBalance`
- `dailyComputeTokenLimit`
- `lowComputeThreshold`
- `selfLearningEnabled`
- `currentTaskEstimateComputeTokens`

### UserRuntimeWalletReadModel

Used by:

- Runtime Wallet
- activation modal

Fields:

- `userId`
- `iuBalance`
- `computeTokenBalance`
- `conversionRate`
- `recentLedgerEntries`

### SkillCatalogReadModel

Used by:

- Train
- Market

Fields:

- `skillId`
- `name`
- `userTier`
- `internalTier`
- `roleFamily`
- `permissionScope`
- `valuePath`
- `iuPrice`
- `computeTokenEstimate`
- `purchasableByAgents`
- `activeSlotWeight`

### AgentSkillLoadoutReadModel

Used by:

- Train
- Robot Detail

Fields:

- `agentId`
- `activeSlotLimit`
- `usedSlots`
- `installedSkills`
- `activeSkills`
- `lockedSkills`
- `recommendedNextSkills`

### TaskThreadReadModel

Used by:

- Workroom
- Master Brain preview

Fields:

- `taskId`
- `agentId`
- `masterBrainId`
- `objective`
- `expectedOutput`
- `estimateComputeTokens`
- `reservedComputeTokens`
- `consumedComputeTokens`
- `status`
- `progress`
- `result`
- `riskNotes`
- `createdAt`
- `updatedAt`

### ScorecardReadModel

Used by:

- Earnings and Review
- Robot Detail

Fields:

- `level`
- `returnRatePct`
- `realizedPnlUsdc`
- `maxDrawdownPct`
- `winRatePct`
- `tasksCompleted`
- `iuSpent`
- `iuEarned`
- `computeTokensSpent`
- `serviceRevenueIu`
- `riskEvents`
- `graduationProgress`

### MemoryStatusReadModel

Used by:

- Robot Detail
- Workroom

Fields:

- `hotSummary`
- `hotMessageCount`
- `hotTokenEstimate`
- `lastCompressionAt`
- `nextCheckpointAt`
- `dailySummaryDate`
- `archivedConversationCount`
- `vectorMemoryCount`

### LimitedDropReadModel

Used by:

- Market

Fields:

- `dropId`
- `name`
- `supply`
- `remaining`
- `priceHi`
- `rarityTable`
- `previewShells`
- `awakeningCostIu`

### BackpackReadModel

Used by:

- Market
- Train

Fields:

- `skillBooks`
- `unrevealedLimitedRobots`
- `ownedBuilds`
- `listableItems`

### GraduationProgressReadModel

Used by:

- Earnings and Review
- Vault Preview

Fields:

- `agentId`
- `status`
- `roleTrack`
- `requiredSkills`
- `completedTasks`
- `riskEvents`
- `simulationScore`
- `probationVaultEligible`
- `nextRequirement`

### MasterBrainReadModel

Used by:

- Master Brain preview

Fields:

- `masterBrainId`
- `workerLimit`
- `activeWorkerCount`
- `taskThreads`
- `totalComputeTokenBudget`
- `progressSummary`
- `nextReportAt`

## MVP Mock Scope

### Mock In hi

- fake wallet connection state
- starter UI data before backend is ready
- animation and progress placeholders
- static educational copy
- frontend-only route guards during prototype

### Mock In hi-core

- deterministic free robot attribute generation
- fake HI and IU balances
- fixed Compute Token conversion rate
- mock Telegram and WeChat binding
- mock limited robot reveal payloads
- mock task progress
- mock report generation
- mock memory summary updates
- mock scorecard and graduation progress

### Must Be Real In hi-core

- one-free-robot rule
- idempotent commands
- lifecycle state transitions
- event log
- read model projection
- Compute Token ledger math
- active skill slot limits
- low Compute Token pause
- risk labels and confirmation requirements

## Acceptance Criteria

P0 is done when:

- `hi` can render seeded read models.
- `hi-core` exposes stable read model shapes.
- command envelope and event envelope are documented in code or schema.

P1 is done when:

- user can claim one free robot.
- second free claim is rejected.
- user can name the robot.
- document pack status appears in the UI.

P2 is done when:

- user can bind Telegram or WeChat in mock mode.
- robot can show a first greeting.
- unbound robots cannot enter active daily operation.

P3 is done when:

- user can activate robot at 9.99 IU/month in mock ledger.
- user can convert IU into Compute Tokens.
- UI shows Compute Token balance and daily cap.
- paid work pauses when balance is too low.

P4 is done when:

- user can install starter skills.
- active skill slots are enforced.
- each skill shows value path and permission scope.

P5 is done when:

- user can run one starter task.
- task reserves and consumes Compute Tokens.
- report output is stored.
- scorecard and memory status update.

P6 is done when:

- user sees growth, next evolution requirement, and graduation preview.
- UI clearly says live autonomous trading is not active.

P7 is done when:

- vault preview shows 100 USDC probation path.
- user understands Certified Autonomous Vault is future gated by graduation.

P8 is done when:

- limited robot shell can be created.
- IU awakening reveals deterministic attributes.
- limited robot still obeys normal activation and graduation rules.

P9 is done when:

- user sees why more than 5 active workers require a Master Brain.
- Master Brain can create mock task threads and total Compute Token budget.

## Suggested Issue Slices

1. Define shared TypeScript contracts for read models, command envelopes, and event envelopes.
2. Build `hi-core` event log and read model projection skeleton.
3. Build seeded `hi` app shell with My Robots, Train, Workroom, Earnings, Market.
4. Implement free robot claim and one-claim enforcement.
5. Implement name robot and core document pack creation.
6. Implement mock Telegram/WeChat binding.
7. Implement monthly activation and Compute Token ledger.
8. Implement starter skill catalog and skill slot enforcement.
9. Implement mock task execution with Compute Token reserve/consume/release.
10. Implement memory summary and scorecard projection.
11. Implement graduation and vault preview.
12. Implement limited robot shell and awakening reveal.
13. Implement skill book backpack and mock listing.
14. Implement Master Brain preview and task thread routing.

