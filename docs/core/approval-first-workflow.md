# Approval-first workflow for personal agents

This document defines a simple default boundary for personal agents:

> **Read is free; changes require explicit approval.**

In other words:
- the agent may **read/inspect/analyze** without asking
- the agent must **ask first** before any action that changes state or has external side effects

## Why approval-first

Personal agents often have access to:
- private notes and accounts
- credentials (directly or indirectly)
- external APIs that can create irreversible changes

Approval-first reduces risk while keeping the agent useful.

## What counts as “read-only”

Usually safe without approval:
- reading local files
- listing directory structure
- fetching public documentation
- analyzing code or drafting text

Still use good judgment: “read-only” can still be sensitive if it reveals private data.

## What counts as “state-changing”

Require explicit approval before:
- editing/creating/deleting files
- running commands that change the machine state (installing packages, modifying config)
- sending messages (email, chat, GitHub comments)
- scheduling automations (cron jobs/reminders)
- pushing commits, opening PRs, commenting on issues

## Defaults vs user overrides

Different users have different tolerance for autonomy.

A good pattern:
- **Default**: approval-first for all state-changing actions
- **User override (USER.md)**: allow a limited set of auto-actions (e.g., “you may schedule read-only checks”)

Keep overrides explicit, narrow, and revocable.

## A practical workflow pattern

1. Agent gathers facts (read-only)
2. Agent proposes actions with options and trade-offs
3. User approves (or modifies) the plan
4. Agent executes exactly the approved actions
5. Agent reports what changed and where

## Example: chat approvals

In a chat-based setup (Telegram/Signal/etc.):
- the agent posts a short plan
- the user replies “approve” (or selects an option)
- the agent executes and posts the result

## Related docs

- Workspace role separation: see #299.
- Agent-owned GitHub repo / backups: see #298.
