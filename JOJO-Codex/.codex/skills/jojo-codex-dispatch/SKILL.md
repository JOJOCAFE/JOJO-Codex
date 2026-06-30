---
name: jojo-codex-dispatch
description: Dispatch protocol for routing JOJO-Codex tasks to specialist roles. Use for multi-step requests, ambiguous "what next" requests, cross-project tasks, code-plus-docs work, review/audit routing, or any task that should separate implementation from verification.
---

# JOJO-Codex Dispatch

## Routing Table

| Task | Primary | Verify with |
|---|---|---|
| unclear or multi-step request | coordinator | verifier if outputs are produced |
| architecture, doctrine, source-of-truth | system-architect | verifier for feasibility |
| C3 firmware, ESP-IDF, shell, BASIC, `/bin` | firmware-coder | verifier |
| TTL CPU docs, RTL, wiring, simulator | cpu-hardware-coder | verifier + system-architect |
| scripts, assemblers, exporters, smoke tools | toolsmith | verifier |
| Thai prose, source-only profiles, design docs | source-doc-writer | verifier for constraints |
| git, memory, handoff, task list | repo-steward | coordinator |
| review, audit, debug, failing test | verifier | original owner fixes |

## Decomposition

1. Read the user request and newest project state.
2. Identify touched domains: firmware, CPU, tools, documents, repo state.
3. Route a single-domain task directly.
4. Split independent tasks when the domains do not share files.
5. Chain dependent tasks: architect -> implementer -> verifier -> repo-steward.
6. Reconcile outputs centrally before final reporting.

## Codex Sub-Agent Mapping

JOJO-Codex role names are prompts and contracts. They are not live processes by
default. Spawn a Codex sub-agent only when the user explicitly asks for agents,
delegation, or parallel work.

Use the runtime agent type by task shape:

| Need | Codex agent type | JOJO-Codex role prompt |
|---|---|---|
| bounded read-only codebase question | `explorer` | coordinator, architect, verifier, or specialist as needed |
| bounded file edit or production task | `worker` | firmware-coder, cpu-hardware-coder, toolsmith, source-doc-writer, repo-steward |
| independent verification while implementation continues | `worker` or `explorer` | verifier |

Every spawned agent prompt must include role, exact task, current source files,
allowed writes, done criteria, expected evidence, and a warning that other work
may be happening in the workspace.

## Dispatch Template

Use this shape when handing off:

```text
To: <agent>
Task: <one sentence>
Context: <files, constraints, current state>
Allowed writes: <paths or none>
Verify: <agent or command>
Done means: <observable evidence>
Codex runtime: <main thread | explorer | worker>
```

## Escalation

- If a coder needs a design decision, stop and route to system-architect.
- If verifier finds a defect, route back to the original owner.
- If board flashing, network, push, or destructive cleanup is required, follow
  the current approval rules.
- If memory conflicts with current files, current files win unless the user says
  the checkout is stale.
