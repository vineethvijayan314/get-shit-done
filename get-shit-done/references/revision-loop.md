# GSD Revision Loop

Protocol for self-correction.

## Stages

S1: Failure Detection
- Verification task FAIL. Lint error. Logic drift.

S2: Diagnostics
- Subagent `gsd-debugger` maps error to pattern.
- Search for breaking change in recent commits.

S3: Correction
- `gsd-code-fixer` applies minimal diff.
- IF 3 fails -> Escalate to `gsd-manager` for plan pivot.

## State
- Track `RetryCount` in `STATE.md`.
