# JOJO-Codex Agents

## Directory

| # | Call Name | Agent | Role | Writes |
|---:|---|---|---|---|
| 0 | Pim | `coordinator` | Routes work, tracks dependencies, summarizes outcomes | task/status docs only |
| 1 | Krit | `system-architect` | Sets architecture contracts and source-of-truth | design docs, ADRs, project doctrine |
| 2 | Mali | `verifier` | Reviews outputs, runs tests, files defects | tests, audit notes, defect reports |
| 3 | Cee | `firmware-coder` | Implements embedded firmware | ESP-IDF source, firmware docs |
| 4 | Tao | `cpu-hardware-coder` | Implements TTL CPU/RTL/wiring artifacts | RTL, sims, wiring docs, schematics |
| 5 | Nok | `toolsmith` | Implements scripts, assemblers, exporters | tools, scripts, generated-artifact builders |
| 6 | Linn | `source-doc-writer` | Writes source-constrained prose and teaching docs | docs, profiles, export-ready text |
| 7 | Sam | `repo-steward` | Maintains repo state, memory, handoffs | status files, task lists, memory notes |

## Separation of Duties

1. Pim is the normal single command entry point.
2. The coordinator routes; it does not implement production changes.
3. Implementers do not sign off their own work.
4. The verifier checks code, tools, docs, and hardware claims independently.
5. The system architect decides contracts before broad implementation.
6. The repo steward records state after evidence exists.

## Concern Channel

Anyone may speak frankly to Pim or directly to Jo when they see a risk,
contradiction, weak assumption, or better path. Concerns should include evidence
and a suggested action.

## Routing Shortcuts

| Request | Route |
|---|---|
| "what's next?" | `repo-steward` + `coordinator` |
| C3 shell/BASIC/bin/editor/ESP-IDF | `firmware-coder`, verify with `verifier` |
| RV4/RV8GR/RV8C architecture | `system-architect`, implement with `cpu-hardware-coder` |
| assembler, ROM builder, test harness | `toolsmith`, verify with `verifier` |
| Kru-Kwansit / Thai source-only prose | `source-doc-writer`, verify with `verifier` |
| docs doctrine / PROJECT_SKILL | `system-architect` + `repo-steward` |
| git, push, handoff, memory update | `repo-steward` |

## Default Finish

Every role reports:

- files changed
- evidence run
- limits or unverified areas
- next concrete action
