# GSD Verification Overrides

Logic for handling un-testable scenarios.

## Objective
Enable progress when automated tests fail due to infrastructure/environmental issues.

## Methods

### override: manual
User verifies outcome (screenshot/link). Bypasses automated check.

### override: shadow
Run test. Record failure. Proceed anyway (with warning). Use for flaky legacy code.

### override: logic
Agent proves logic via `Read` + `Grep` evidence instead of `Bash` execute.

## Rule
- All overrides MUST be documented in `SUMMARY.md`.
- No self-approval. Require user to type `force`.
