# GSD Workstream Flags

Identify current line of work.

## Objective
Prevent overlapping agents from modifying the same files.

## Flags
- `[BUSY]`: File currently under edit by Agent X.
- `[STABLE]`: File verified. Ready for downstream consumption.
- `[DIRTY]`: File needs verification/fix.

## Process
1. `gsd-manager` reads flags in `.gsd/manifest.json`.
2. Handoff logic: Only dispatch tasks for `[STABLE]` or unflagged files.
3. Commit protocol: Update flag upon atomic commit.
