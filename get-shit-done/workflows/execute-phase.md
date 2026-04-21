# Phase: Execute
Trigger: `/gsd-execute-phase [phase_number]`

## S1: Setup
- Agent: `gsd-executor`.
- Load planning state: `gsd-sdk query state.load`.
- Check: PLAN.md exists. Context budget okay.

## S2: Implement
- Multi-Agent Cycle:
  1. `gsd-executor`: Run task. Code + Verify.
  2. `gsd-code-reviewer`: (Optional) Review diffs.
  3. `gsd-ui-auditor`: (Optional) 6-pillar visual audit.
  4. `gsd-security-auditor`: Verify threat mitigations.
- Guard: Fail on BLOCKER. Fix before next task.

## S3: Finalize
- Write: SUMMARY.md.
- State: `gsd-sdk query state.save`.
- Record: Learning extraction.
---
# Phase: Verify
Trigger: `/gsd-verify-phase [phase_number]`

## S1: Goal-Backward Audit
- Agent: `gsd-verifier`.
- Logic: Falsify SUMMARY. Ensure must-haves met.
- Stance: Evidence only. Reject documentation.

## S2: Quality Audit
- Agent: `gsd-eval-auditor`.
- Scope: Coverage against rubrics.
- Scoring: COVERED | PARTIAL | MISSING.

## S3: Gaps
- If gaps: Generate fix plans via `gsd-verifier`.
- Process: Order by dependency. Fix missing -> fix wiring.

## S4: Report
- Output: `{PHASE}-VERIFICATION.md`.
- Status: passed | gaps_found | human_needed.
---
# Workflow: Health
Trigger: `/gsd-health [--repair] [--backfill]`

## S1: Scan
- Logic: `gsd-sdk query validate.health $REPAIR_FLAG $BACKFILL_FLAG`.
- Check: config, PROJECT, ROADMAP, STATE.

## S2: Repair
- If `--repair`: createConfig, resetConfig, regenerateState.
- If `--backfill`: backfill milestones.

## S3: Report
- Status: healthy | degraded | broken.
- List: Errors [E-XX], Warnings [W-XX].
