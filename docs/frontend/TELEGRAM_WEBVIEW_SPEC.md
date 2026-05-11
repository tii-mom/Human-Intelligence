# Telegram and WeChat Agent Interface Specification

## Purpose
Optimize HI Protocol for chat-native agent ownership, skill management, monitoring, and command input.

Telegram is the first global chat surface.

WeChat is the priority chat surface for Chinese users.

## Requirements
- Mobile-first
- Touch optimized
- Fast loading
- Lightweight motion
- Bottom navigation
- Inline notifications
- Required communication binding after agent creation

## Telegram UX
- AI assistant integration
- Push-style AI alerts
- Telegram wallet compatibility
- Deep-link support
- Bot binding
- Bot commands
- Blank agent claim
- Skill subscription and renewal prompts
- Agent growth notifications

## WeChat UX
- Official Account or Mini Program binding
- QR-code binding
- WeChat-native status queries
- WeChat-friendly daily reports
- Subscription or template-style notifications where allowed
- In-app inbox fallback when proactive push is limited

## Primary Telegram Flows
- claim blank agent
- name agent
- bind Telegram or WeChat
- receive first agent greeting
- chat with active agent
- switch active agent
- review limited agent drops
- install or renew skills
- track automatic graduation progress
- activate Certified Autonomous Vault
- receive agent reports
- approve risk-limited actions
- approve agent service purchases
- receive IU budget alerts
- receive USDC vault alerts
- receive autonomous vault PnL alerts
- receive certified vault safe-mode alerts
- receive output sale notifications

## Required Chat Commands
- `/help`
- `/agents`
- `/use`
- `/status`
- `/skills`
- `/memory`
- `/risk`
- `/scorecard`
- `/report`
- `/vault`
- `/settings`

Natural language commands should also work.

Examples:

- "Show Atlas status."
- "What did my news agent find today?"
- "What skill should Luna learn next?"
- "Show current vault risk."

## Messaging Boundary
Telegram should explain agent decisions in plain language.
It should not make users manage DEX swaps, gas, or low-level settlement in the primary flow.

The same product boundary applies to WeChat.

Chat commands should never bypass skill permissions, Risk Guard, graduation certificates, or vault rules.

## Goal
Telegram and WeChat should feel like the native operating surfaces for cultivating and monitoring a personal agent.
