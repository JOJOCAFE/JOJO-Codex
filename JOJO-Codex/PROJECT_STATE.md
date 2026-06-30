# Project State

## Active Target

Bootstrap `JOJO-Codex` as a Codex-native agent organization for the projects in
`/home/jo/Codex`.

## Status

- Team roles defined: 8 agents.
- Shared and role skills scaffolded under `.codex/skills/`.
- Agent configs scaffolded under `.codex/agents/`.
- Shared memory and state docs created.
- Shared backlog, task list, and teamlog created.
- Per-person memory and task-list files created.
- All 10 skill folders passed `quick_validate.py`.
- All 8 agent JSON files passed `python3 -m json.tool`.
- Pushed to `git@github.com:JOJOCAFE/JOJO-Codex.git` on branch `master`.
- This folder is reviewable and portable; it is not installed globally.
- Codex runtime mapping documented: role configs are contracts; live spawned
  agents are generic `explorer`/`worker` agents given JOJO-Codex role prompts.

## Current Decisions

| Date | Decision |
|---|---|
| 2026-06-29 | Use `JOJOCAFE-Org` practice as template, not as a direct copy. |
| 2026-06-29 | Use Codex-oriented `.codex/skills` and `.codex/agents` paths. |
| 2026-06-29 | Map roles to real Codex jobs: C3 firmware, CPU hardware, tooling, source docs, verification, repo state. |
| 2026-06-29 | Keep non-author verification as the core quality gate. |
| 2026-06-29 | Adopt the team ethos: professional genius, excellent work, and making the world better through useful, verifiable projects. |
| 2026-06-29 | Make Pim the normal single command entry point; specialists may raise concerns directly to Pim or Jo. |
| 2026-06-29 | Keep JOJO-Codex portable in this repo for now; install or copy project-local versions only after user review. |
| 2026-06-30 | Treat `.codex/agents/*.json` as role contracts, not persistent daemons; spawn generic Codex `explorer`/`worker` agents only when Jo explicitly asks for agent/delegated/parallel work. |

## Next Actions

1. Forward-test the runtime mapping on one small delegated task when Jo asks
   for parallel agents.
2. Review the role map in `AGENTS.md` when the team model is next used.
3. If approved later, copy selected skills into a project or into `$CODEX_HOME/skills`.
4. For each active repo later, create a smaller project-local `PROJECT_STATE.md` and
   trim `TEAM_MEMORY.md` to that repo's facts.
5. Add first real defect reports only after real verifier findings exist.

## Known Limits

- The `.codex/agents/*.json` files are role contracts for humans/Codex; they do
  not by themselves create persistent running agents.
- The live sub-agent interface exposes generic agent types; JOJO-Codex role
  identity is supplied through the task prompt and done criteria.
- Some project facts are memory-derived and must be refreshed before risky work.
- Board and external-service actions still require current environment checks.
