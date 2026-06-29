# JOJO-Codex Team Memory

Last reviewed: 2026-06-29.

This file records the shared workspace map for the agent team. It is a routing
aid, not a replacement for reading current files.

## Workspace Rules

- `/home/jo/Codex` is a container for several projects, not one clean project.
- Confirm the actual repo root before running git commands.
- Treat user or generated local changes as owned by the user unless this team
  made them in the current task.
- Prefer concrete evidence over broad claims.
- For "what's next", give the next action from current workspace state, not a
  history recap.
- For CPU/toolchain work, reject weak pass criteria, silent truncation, and
  unsupported pseudo-instructions.
- For source-constrained documents, do not invent. Unsupported fields stay
  blank.

## Active Workspaces

### C3_Basic_Computer

- Active implementation is the root tree under `source/`, not old legacy paths.
- `.codex/PROJECT_SKILL.md` carries the manifesto, design principles, source
  footer rule, recovery invariant, and sprint routing.
- Current handoff says Sprint 011 is complete and the next recommended work is
  Sprint 009 ASM nano mode: `ASM /asm/name.asm` with text validation first.
- ESP-IDF build path observed in project docs: `tools/idf53.sh -B build-c3-root build`.
- Board testing commonly uses `/dev/ttyACM0`, but live device presence must be
  checked before flash/smoke claims.

### CPU Projects

- `RV4-Tiny` is a frozen teaching CPU baseline unless the user explicitly
  reopens architecture. Move forward through simulator, assembler, docs, or
  schematic work.
- `RV8GR-*` work should treat ISA/control docs and wiring docs as authority,
  then verify assembler, ROMs, RTL, sims, and programmer assumptions together.
- `RV8C` uses numbered docs as the navigation/build-order contract.
- Existing local CPU skill: `skills/riscv-cpu-design/SKILL.md`.

### Teacher/Kru-Kwansit

- Resume from `Teacher/Kru-Kwansit/Kru-Kwansit_rewrite_task_list.md`.
- Use only approved source artifacts for factual claims.
- Keep generated `.docx` output in `docx/`, separate from validated samples.
- Preserve headings and blank unsupported sections.

### Other Embedded Work

- `ESP32-C3-BLE-Media-Macro-Pad`, `esp32-c3-oled`, and `openc6-bios` are
  embedded/reference surfaces. Verify each project's README and build system
  before borrowing assumptions into C3.

## Template Source

The source practice was studied from `/home/jo/kiro/RV8/JOJOCAFE-Org`:

- root coordination docs
- `.kiro/agents/*.json`
- `.kiro/skills/*/SKILL.md`
- `.agent_state/*/MEMORY.md`
- separation of duties with independent verification

JOJO-Codex keeps that practice but uses `.codex/` paths and Codex-specific
working rules.
