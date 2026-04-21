<purpose>
Drive milestone phases autonomously. Discuss -> Plan -> Execute loop. Pause for user decisions. Re-read roadmap after each phase.
</purpose>

<process>

S1: Initialize
- Parse Args: `--from N`, `--to N`, `--only N`, `--interactive`.
- `gsd-sdk query init.milestone-op`.
- REQ: ROADMAP.md + STATE.md.
- Banner: Milestone progress.

S2: Discover Phases
- `gsd-sdk query roadmap.analyze`.
- Filter: `disk_status != "complete"` OR `roadmap_complete === false`.
- Apply From/To/Only numeric filters. (Handles decimals).
- IF empty: EXIT ("All Clear").
- Sort: Ascending.

S3: Phase Loop
For each phase in list:

  S3a: Smart Discuss
  - Check `has_context` (via `init.phase-op`).
  - If exists: Skip.
  - If missing + `workflow.skip_discuss` is true: Create minimal CONTEXT.md from roadmap goal.
  - If missing + no skip:
    - DISPATCH: `Skill(gsd-discuss-phase ${phase_num})`.
    - If `INTERACTIVE`: Run inline (accumulate chat).
    - Else: Dispatch to agent.
    - REQ: Wait for CONTEXT.md creation.

  S3b: Plan Phase
  - Check `has_plan` + `plan_status`.
  - If complete: Skip.
  - Else:
    - DISPATCH: `Skill(gsd-plan-phase ${phase_num})`.
    - REQ: Wait for `PLAN.md` creation.

  S3c: Execute Phase
  - DISPATCH: `Skill(gsd-execute-phase ${phase_num})`.
  - Loop check: REQ `SUMMARY.md` + `VERIFICATION.md`.
  - Progress Banner: `Phase N/T: Name [████░░░░] P%`.
  - (Wait for phase completion signal/file).

  S3d: Sync Roadmap
  - Refresh phase list from ROADMAP.md (catch additions).
  - Update completion counts.

S4: Error Handling
- On sub-skill fail: Log error. REQ user input.
- Pause loop if user decision required.

S5: Completion
- Show summary of completed phases.
- Final: "AUTONOMOUS ▸ COMPLETE 🎉".
</process>

<success_criteria>
- [ ] Phases processed in numeric order.
- [ ] Discuss/Plan/Execute chain followed.
- [ ] Roadmap re-read between phases to catch dynamic insertions.
- [ ] User decisions respected (Grey area pauses).
- [ ] Progress banner UI matches spec.
</success_criteria>
