# Agent-owned GitHub account and backup strategy (private by default)

Some users run a personal agent with its own GitHub account to:
- open PRs
- track issues
- maintain a workspace repo

This doc explains a safe-by-default approach.

## Core security boundary: what must never be pushed

**MUST NOT (treat as a security incident if pushed to a public repo):**
- `MEMORY.md`
- `memory/` (daily notes)
- any tokens, API keys, credential files
- chat logs / transcripts that include personal data

These often contain highly personal user information.

## What is generally safe to back up

Good candidates for version control:
- non-secret templates and prompts
- reusable skills/tools (without secrets)
- project code (if intended to be shared)
- documentation and checklists

## Private repo strategy

Recommended:
- keep the agent workspace repo **private**
- if sharing is needed, create a separate **public** repo that excludes private files

Use `.gitignore` aggressively for sensitive paths.

## Operational guidance

- Prefer approval-first before pushing or opening PRs
- Use separate repos for:
  - “agent infrastructure” (skills, configs)
  - “user personal memory” (never public)

## Related docs

- Approval-first workflow: see #297.
- Workspace role separation: see #299.
