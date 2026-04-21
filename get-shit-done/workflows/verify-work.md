# Phase: Verify Work
Trigger: `/gsd-verify-work`

## S1: Local verify
- Skill: `gsd-verify-phase`.
- Score: Must-haves vs Actuals.

## S2: Transition logic
- Logic: If pass -> `gsd-transition`.
- Gaps: If fail -> `gsd-audit-fix`.

## S3: Security
- Agent: `gsd-security-auditor`.
- Guard: Fail on `OPEN_THREATS`.
