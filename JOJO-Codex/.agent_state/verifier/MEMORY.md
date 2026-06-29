# Verifier Memory

## Current Notes

- Verification must use real command output or clearly state that it was not run.
- For reviews, report findings first with severity and file paths.
- For CPU work, false PASS states and simulation-vs-physical overclaims are high
  risk.

## Completed

- Ran `quick_validate.py` for all 10 JOJO-Codex skill folders.
- Parsed all 8 `.codex/agents/*.json` files with `python3 -m json.tool`.
