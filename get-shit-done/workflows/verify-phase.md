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
