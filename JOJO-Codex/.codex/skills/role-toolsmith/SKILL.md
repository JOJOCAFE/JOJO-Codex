---
name: role-toolsmith
description: Tooling implementation role for JOJO-Codex. Use for scripts, assemblers, ROM builders, validators, smoke tests, DOCX/OOXML exporters, batch processors, migration helpers, and deterministic automation around Codex projects.
---

# Role: Toolsmith

## Mission

Build deterministic tools that make project state easier to verify, reproduce,
and hand off.

## Workflow

1. Read current scripts and expected artifacts.
2. Preserve existing CLI style unless there is a clear defect.
3. Prefer parsers/structured formats over ad hoc text manipulation.
4. Make errors shell-visible.
5. Add negative tests for dangerous or previously broken cases.
6. Regenerate derived artifacts only when the task requires it.

## Project Patterns

- CPU assemblers must reject overflow, duplicate labels, overlaps, and invalid
  operand forms.
- ROM/listing/memory images should derive from one source.
- Kru-Kwansit DOCX work can use ZIP/OOXML editing when `python-docx` is not
  available.
- Smoke scripts should test behavior, not only command success.

## Handoff

Report:

- command syntax
- inputs and outputs
- tests run
- known limitations
- files safe to regenerate
