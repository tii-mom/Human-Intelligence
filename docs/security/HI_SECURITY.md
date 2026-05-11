# HI Security

## AI Permissions

AI agents cannot:
- Withdraw funds to unauthorized destinations
- Transfer assets outside approved vault routes
- Change ownership permissions
- Transfer agent ownership without user approval
- Expose hidden skill logic
- Continue using expired skills
- Bypass agent vault limits
- Increase USDC trading capacity without approval
- Spend outside IU runtime budget caps

AI agents can:
- Open positions
- Close positions
- Manage stop loss
- Manage leverage within limits
- Fully operate funds inside a Certified Autonomous Vault after graduation
- Buy skills and service outputs within IU budget
- Produce outputs for other agents

## Risk Engine

The Risk AI has veto authority over unsafe actions, certificate violations, emergency conditions, unsupported venues, unsupported assets, and abnormal execution patterns.

Risk guardrails also control vault capacity, venue whitelist, asset whitelist, leverage, and emergency shutdown.

Risk should not block normal certified autonomous operation when the agent acts inside certificate scope.
Risk should enter safe mode only when the agent violates mandate scope, hits user-defined risk lines, encounters black swan conditions, or shows abnormal execution.

## Skill Safety

- Skill descriptions disclose outcomes, not mechanisms
- Subscription skills deactivate when unpaid
- Buyout licenses grant use rights, not source code ownership
- Resale must preserve provider attribution and license limits

## User Protection

- Position limits
- Drawdown controls
- User-defined position management lines
- User-selected vault mandate
- API encryption
- Session protection
- Agent ownership protection
- Skill license verification
- Agent vault isolation
- Certified Autonomous Vault scope
- IU budget caps
- USDC trading capacity limits
- Kill switch

## Black Swan Mode

Emergency market shutdown logic can reduce exposure automatically.

## Settlement Safety

Humans fund with USDC and settle through official protocol paths.
Agents spend IU internally for runtime services.

Agent-earned IU should not imply uncontrolled retail token trading.
