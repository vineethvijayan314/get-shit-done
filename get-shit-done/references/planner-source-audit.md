# GSD Planner Source Audit

Verify source code availability for planning.

## Objective
Ensure file paths in PLAN.md exist. Avoid planning on hallucinations.

## Rules
- Every file path cited in `objective/files` MUST be verified via `ls`.
- New files marked [NEW].
- Target logic must be present in cited file (check via `grep`).

## Process
1. `gsd-planner` scouts files.
2. `gsd-plan-checker` runs path validation.
3. IF path missing -> Flag Blocker.
