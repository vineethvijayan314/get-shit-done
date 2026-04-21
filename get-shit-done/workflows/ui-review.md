<purpose>
Audit implemented frontend code via 6-pillar visual review. Produce scored UI-REVIEW.md.
</purpose>

<process>

S0: Init
- `INIT=$(gsd-sdk query init.phase-op "${PHASE}")`.
- Resolve `gsd-ui-auditor`.

S1: Detect State
- SUMMARY check: REQ SUMMARY.md exists.
- UI-REVIEW check: If exists -> Re-audit | View.

S2: Context Gathering
- Inputs: SUMMARY (execution), PLAN (intent), UI-SPEC (baseline), CONTEXT (decisions).

S3: Auditor Spawn
- Task(gsd-ui-auditor).
- Action: 6-pillar audit (Copy, Visuals, Color, Typography, Spacing, Experience).
- Baseline: UI-SPEC.md (if found) | Abstract standards.

S4: Automated verification (Optional)
- Trigger: Playwright-MCP available.
- Actions: Navigate -> Screenshot -> Auto-compare against spec dimensions/palette.
- Report: Append findings. Tag `needs_human_review`.

S5: Report Generation
- Path: `${PHASE_DIR}/${PADDED_PHASE}-UI-REVIEW.md`.
- Summary: Score / 24.
- Table: Per-pillar scores. Actionable fixes.

S6: Wrap
- `git commit`: `docs(${padded_phase}): UI audit review`.
- Next: `/gsd-verify-work {N}` | `/gsd-plan-phase {N+1}`.
</process>

<success_criteria>
- [ ] 6-pillar status report generated.
- [ ] Playwright-MCP detection functional.
- [ ] UI-SPEC.md used as truth baseline.
- [ ] Score / 24 calculated.
</success_criteria>
