# GSD Doc Conflict Engine

Logic for merging documentation streams.

## Objective
Detect overlap between legacy docs, code context, and new ingested docs. Resolve Drift.

## Rules
- **Rule 1: Timestamp Wins**. Most recent file edit takes priority.
- **Rule 2: Code over Prose**. If code shows X and doc says Y, update doc to match code.
- **Rule 3: User Manual Primal**. Do NOT overwrite sections marked `[MANUAL]`.

## Process
1. Run `gsd-doc-classifier`. Determine stream types.
2. Run `gsd-doc-synthesizer`. Buffer changes.
3. Show User `AskUserQuestion(header: "Drift", options: [Sync, Compare, Reject])`.
