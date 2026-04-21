<purpose>
INTERNAL. Mark phase complete. Advance position. Evolve PROJECT.md. Execute handoff cleanup.
</purpose>

<process>

S1: Verify Completion
- Read current phase dir.
- Count PLANs vs SUMMARYs. Match -> Complete. Mismatch -> Incomplete.
- Safety: If incomplete, ALWAYS prompt user Choice (Continue | Skip/Finish | Review).

S2: Cleanup
- Delete `.continue-here*.md` stale handoffs.

S3: State Advancement
- `TRANSITION=$(gsd-sdk query phase.complete "${current_phase}")`.
- Actions: Checkbox `[x]`, Update plan count, Set Next Phase in STATE.md.
- Result: `is_last_phase`, `next_phase`.

S4: Project Evolution
- Read SUMMARYs from phase.
- Move shipped Active requirements -> Validated (Phase X).
- Move invalid requirements -> Out of Scope (Reason).
- Add discovered requirements -> Active.
- Log new Key Decisions.
- Update "Last updated" footer.

S5: Position Update
- Update PROGRESS bar in STATE.md.
- Set Status: "Ready to plan".
- Update Project Reference section.

S6: Routing
- Get `is_last_phase` from result.
- **Route A (phases remain)**:
  - If CONTEXT.md exists -> `/gsd-plan-phase {N+1}`.
  - Else -> `/gsd-discuss-phase {N+1}`.
- **Route B (milestone done)**:
  - Check for active workstreams.
  - No active workstreams -> `/gsd-complete-milestone`.
  - Collision check -> Block + suggest workstream completion.
</process>

<success_criteria>
- [ ] Phase summaries reviewed for requirement deltas.
- [ ] PROJECT.md evolves requirements + decisions.
- [ ] Next phase correctly identified and recommended.
- [ ] STALE handoffs purged.
</success_criteria>
