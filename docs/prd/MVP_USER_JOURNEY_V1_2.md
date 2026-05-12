# MVP User Journey v1.2

## Purpose

Define the first usable product journey for a normal user.

The MVP should feel like cultivating a financial robot, not configuring an enterprise trading system.

## First 5 Minutes

### 1. Enter HI

The user sees the product promise:

```text
Claim, train, and own your AI trading robot.
```

The first action is not a trading chart.

The first action is:

```text
Claim your free robot
```

### 2. Claim One Free Robot

The user can claim only one free Blank Robot.

The product reveals:

- robot name placeholder
- starter stage: Young
- rarity
- top two attributes
- Growth Potential
- two active skill slots

The product should explain:

```text
This robot is yours. It is not ready to make money yet. Train it first.
```

### 3. Name The Robot

The user gives the robot a name.

The backend creates the core document pack:

- `IDENTITY.md`
- `SOUL.md`
- `COMMUNICATION.md`
- `MANDATE.md`
- `SKILLS.md`
- `MEMORY.md`
- `RISK.md`
- `SCORECARD.md`
- `SERVICES.md`
- `RUNTIME.md`

The user should see this as:

```text
Robot profile created
```

not as raw prompt files.

### 4. Bind Telegram Or WeChat

At least one channel is required before active operation.

The user chooses:

- Telegram
- WeChat

The robot sends the first greeting through the bound channel.

The greeting should include:

- who the robot is
- what it can do now
- what it needs next
- current activation state
- current Compute Token balance

### 5. Activate The Robot

The product shows:

```text
Monthly activation: 9.99 IU/month
Daily chat included
```

If the user does not activate:

- the robot remains owned
- basic preview is available
- paid work, self-learning, and evolution remain paused

If the user activates:

- the robot can chat normally
- the robot can learn starter skills
- paid tasks can start when Compute Tokens are available

### 6. Convert IU Into Compute Tokens

The product shows:

```text
1 IU = 10,000,000 Compute Tokens
```

The user chooses a simple amount:

- small starter amount
- recommended amount
- custom amount

The UI should show:

- current Compute Token balance
- estimated days of normal work
- current daily cap
- low-balance auto-pause rule

### 7. Learn First Skill

The user sees three simple recommendations:

- Basic News Scanner
- Risk Guard Lite
- Daily Report Writer

Each skill card should show:

- what it helps with
- expected value path
- permission level
- whether it burns Compute Tokens
- whether outputs can later earn IU

The user should not see a giant marketplace first.

### 8. Send First Useful Task

The user chooses a starter task:

```text
Give me today's BTC and ETH market brief.
```

Before running, the robot shows:

- estimated Compute Token cost
- expected output
- risk level
- whether user confirmation is required

After running, the robot returns:

- short report
- sources or source classes
- confidence
- what it learned
- next recommended skill

### 9. Show Growth

The robot updates:

- scorecard
- memory summary
- skill usage
- current level
- next evolution requirement

The product should make the user feel:

```text
My robot learned something useful.
```

not:

```text
I paid for an opaque AI response.
```

### 10. Show Money Path

The MVP should be honest:

```text
This robot is not certified for live autonomous trading yet.
```

Then show the path:

```text
Learn money/service skill
  -> run simulations
  -> produce useful reports
  -> enter Trial
  -> prove with 100 USDC probation vault or service income
  -> pass automatic graduation
  -> activate Certified Autonomous Vault or sell services
```

## Main MVP Screens

### My Robots

Shows:

- owned robots
- free robot status
- limited robot status
- monthly activation state
- Compute Token balance
- current job
- next evolution

### Train

Shows:

- recommended skill path
- Basic, Advanced, Expert skill books
- active skill slots
- next evolution requirement
- training history

### Workroom

Shows:

- active task
- task estimate
- progress
- result
- memory update
- Master Brain view when needed

### Earnings And Review

Shows:

- simulated PnL
- service income
- IU earned
- Compute Tokens spent
- risk events
- scorecard
- graduation progress

### Market

Shows:

- limited robots
- skill books
- agent outputs
- builds
- user backpack

## MVP Success Criteria

The MVP is successful when a new user understands:

- why they claimed a robot
- why activation costs 9.99 IU/month
- why Compute Tokens are needed
- how a skill makes the robot more useful
- how the robot can eventually create value
- why live money-making requires proof and certification

The MVP fails if the user thinks:

- this is just another chatbot
- IU is only a fee with no value path
- skills are random upgrades
- robots magically guarantee profit
- the system is too complex to operate

