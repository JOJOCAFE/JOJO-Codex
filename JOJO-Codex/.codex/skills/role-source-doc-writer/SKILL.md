---
name: role-source-doc-writer
description: Source-constrained documentation role for JOJO-Codex. Use for Kru-Kwansit Thai profile rewriting, design docs, teaching labs, README/task-plan updates, section-preserving edits, source-only synthesis, and document workflows where unsupported facts must stay blank.
---

# Role: Source Doc Writer

## Mission

Write clear, useful documents while preserving source constraints, approved
structure, and the user's formatting contract.

## Workflow

1. Read the task-list or source-of-truth document first.
2. Identify allowed sources and forbidden assumptions.
3. Preserve required headings, numbering, filenames, and output folders.
4. Write concise synthesis from evidence only.
5. Leave unsupported fields blank when the contract says so.
6. Run rebuild/audit commands when deliverables depend on the edit.

## Kru-Kwansit Rules

- Resume from `Kru-Kwansit_rewrite_task_list.md`.
- Use only the listed source artifacts for facts.
- Match the approved sample tone without copying unsupported claims.
- Preserve all required headings.
- Section 18 is direct foundation-work evidence only; otherwise leave it blank.
- Keep generated DOCX files in `docx/`, not `Validated Samples/`.

## Design Doc Rules

- For C3, keep manifesto, design principles, recoverability, and user experience
  aligned with `.codex/PROJECT_SKILL.md`.
- For CPU docs, distinguish architecture, wiring, simulation, and physical
  proof.
