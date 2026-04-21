# Phase: Audit Fix
Trigger: `/gsd-audit-fix [phase_number]`

## S1: Identify
- Agent: `gsd-verifier`.
- Logic: Load `*-VERIFICATION.md`. Extract `gaps_found`.

## S2: Plan Fix
- Agent: `gsd-planner`.
- Logic: Generate targeted PLAN.md for each gap cluster.

## S3: Execute
- Skill: `gsd-execute-phase`.
- Loop: Fix -> re-verify.
