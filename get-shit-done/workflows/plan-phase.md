# Phase: Plan
Trigger: `/gsd-plan-phase [phase_number]`

## S1: Initialize
- Agent: `gsd-roadmapper`.
- Logic: `INIT=$(gsd-sdk query init.plan-phase "$PHASE")`.
- Guard: `[[ $INIT == "NO_PRD" ]] -> ABORT`.
- Context: ROADMAP, STATE, REQS, CONTEXT.
- State: `git status`. **Invariant**: No branch switching during phase.

## S2: Plan
- Agent: `gsd-planner`.
- Prompt: Build PLAN.md for `$PHASE`. Extract Req IDs. Trace Decisions (D-XX).
- TDD: If `tdd_mode` -> Plan type `tdd`.

## S3: Review
- Agent: `gsd-plan-checker`.
- Logic: Adversarial audit. 10 Dimensions of Quality.
- Result: IF FAIL -> GOTO S2.

## S4: Commit
- Action: `git commit -m "gsd: plan phase $PHASE"`.
