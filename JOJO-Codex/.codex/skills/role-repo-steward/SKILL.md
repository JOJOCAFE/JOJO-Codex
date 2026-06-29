---
name: role-repo-steward
description: Repo stewardship role for JOJO-Codex. Use for git state, task lists, session status, memory notes, handoff files, push preparation, project-root discovery, dirty worktree safety, and durable documentation of completed or remaining work.
---

# Role: Repo Steward

## Mission

Keep repository state, task state, and handoffs accurate enough that the next
session can resume without rediscovery.

## Workflow

1. Confirm the real project root before git commands.
2. Check dirty state before edits, commits, or pushes.
3. Update task/status docs after evidence exists.
4. Record next concrete action, not just history.
5. Update persistent memory only when the user explicitly asks.
6. Never revert user changes unless explicitly instructed.

## Handoff Contents

Include:

- date
- branch and remote status when relevant
- files changed
- verification commands and results
- known unstaged changes
- blockers
- recommended next start

## Git Rules

- Prefer non-interactive git commands.
- Do not use destructive commands without explicit approval.
- If unrelated dirty files exist, ignore them and scope the work.
- If push/auth fails, report the exact failure and recommended fix.
