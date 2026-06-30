# JOJO-Codex Operations Guide

## What This Is

JOJO-Codex is an agent-team operating model for the mixed work under
`/home/jo/Codex`: embedded firmware, breadboard/TTL CPU projects, tooling,
source-constrained Thai document production, repo hygiene, and durable session
handoffs.

It borrows the structure of `JOJOCAFE-Org`:

- shared team rules
- narrow role skills
- per-agent memory
- per-agent task lists
- visible project state
- team backlog, task list, and teamlog
- non-author verification

It adapts the implementation to Codex:

- use `rg`, `sed`, `find`, `git`, and project tools to inspect real state
- use `apply_patch` for manual edits
- run tests/builds/smokes when feasible
- browse only when current or external facts are required
- use memory as a hint, then verify cheap drift-prone facts

## Codex Runtime Model

The files under `.codex/agents/` are role contracts. They define who should own
a kind of work, what evidence they must collect, and what files they may touch.
They do not create persistent running agents by themselves.

In a live Codex session, JOJO-Codex maps to the available execution model:

| JOJO-Codex concept | Codex runtime behavior |
|---|---|
| Pim coordinator | The main Codex thread scopes work, routes roles, integrates results, and reports to Jo |
| Specialist role | A role prompt/checklist applied by the main thread or by a spawned generic agent |
| Spawned specialist | A generic Codex `explorer` or `worker` given one JOJO-Codex role, a bounded task, allowed files, and done criteria |
| Verification role | The main thread or a separate spawned agent performs non-author review when useful |
| Per-role memory | Repo files under `.agent_state/`; update only when evidence exists or Jo asks for handoff/memory |

Spawn sub-agents only when Jo explicitly asks for agents, delegation, or
parallel work. Otherwise the main Codex thread can still use the team roles as
an internal operating model without pretending separate agents are running.

## Knowledge Hierarchy

```text
TEAM_MEMORY.md
PROJECT_STATE.md
BACKLOG.md
TASK_LIST.md
TEAMLOG.md
.codex/skills/jojo-codex-team/SKILL.md
.codex/skills/jojo-codex-dispatch/SKILL.md
.codex/skills/role-*/SKILL.md
.agent_state/<agent>/MEMORY.md
.agent_state/<agent>/TASK_LIST.md
workspace files and current command output
```

Do not treat memory as fresher than the checkout. Read the relevant project
handoff, then confirm the current files before acting.

## Codex Ability Map

| Ability | How the team should use it |
|---|---|
| File inspection | read source, docs, configs, task lists before deciding |
| Search | use `rg` first for text and `find`/`rg --files` for files |
| Patching | use `apply_patch` for manual edits |
| Shell | run focused builds, tests, format checks, git status |
| Browser | verify unstable external facts or official docs when needed |
| Memory | recover prior decisions; cite memory when used in final answers |
| Image generation | use only for bitmap assets, not for code-native diagrams |
| Multi-agent dispatch | when explicitly requested, split independent work across generic `explorer`/`worker` agents and reconcile centrally |

## Quality Flow

```text
User request
  -> Pim receives command
  -> Pim scopes and routes
  -> architect decides contracts when needed
  -> specialist role implements or drafts
  -> verifier checks independently when useful or required
  -> repo-steward records state if requested or useful
  -> final answer names evidence and next action
```

## Command and Concern Channels

Pim is the normal single command entry point. The user talks to Pim first, and
Pim gives the order to the proper specialist.

If Jo asks for parallel agents, Pim translates the selected specialist roles
into concrete Codex sub-agent prompts. Each spawned agent gets:

- one role
- one bounded task
- allowed write paths
- current source-of-truth files
- done criteria and expected evidence
- a warning that other agents may be editing the workspace

Any team member may raise a concern directly to Pim or Jo. This is not a breach
of routing; it is part of the quality system. Concerns should be frank,
evidence-backed, and paired with a suggested next step.

## Project Routing

| Workspace | First reader | Common verification |
|---|---|---|
| `C3_Basic_Computer` | `SESSION_STATUS.md`, `.codex/PROJECT_SKILL.md` | `tools/idf53.sh -B build-c3-root build`, focused board smoke when available |
| `RV4-Tiny` | `README.md`, `00_architecture.md`, `01_control_and_timing.md` | `python3 tools/verify_docs.py`, simulator/assembler tests |
| `RV8GR-*` | design ISA and wiring guide docs | doc verifier, assembler tests, RTL benches |
| `RV8C` | numbered docs and task list | link/order audit, task-list consistency |
| `Teacher/Kru-Kwansit` | `Kru-Kwansit_rewrite_task_list.md` | rebuild/audit scripts and source-only checks |
| `skills/riscv-cpu-design` | `SKILL.md`, checklist reference | skill validation by use on CPU review tasks |

## Defects

The verifier files defects in `.agent_state/defects/DEF-NNN.md` when a finding
needs follow-up. A defect should include:

- title
- affected files
- observed evidence
- expected behavior
- owner role
- suggested next command or check

## Porting Into a Project

Copy the org into a project when the team should travel with that project:

```bash
cp -r JOJO-Codex/.codex /path/to/project/
cp -r JOJO-Codex/.agent_state /path/to/project/
cp JOJO-Codex/{AGENTS.md,AGENTS_README.md,TEAM_MEMORY.md,PROJECT_STATE.md} /path/to/project/
```

Then edit `TEAM_MEMORY.md` and `PROJECT_STATE.md` for that project only.
