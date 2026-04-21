<purpose>
Restore session state. Cleanup stale lockfiles. ID gap between ROADMAP and filesystem. Resume next planned phase.
</purpose>

<process>

S1: Cleanup
- Find `.continue-here*.md` (stale handoffs) -> Delete.
- Find `*-PLAN.md` with no `*-SUMMARY.md` -> Identify as "In-Progress Plans".

S2: State Check
- Read STATE.md.
- Verify Current Phase vs ROADMAP.md status.

S3: Phase Re-Index
- If ROADMAP shows incomplete phases, but phase dirs missing -> Warn + Offer Re-Initialize.
- If phase dirs exist but ROADMAP shows pending -> Suggest `/gsd-transition`.

S4: Config Guard
- Read `config.json`.
- Check Workflow switches (Research, Plan Check, Verifier).

S5: Resume logic
- If active worktree found -> Suggest switching.
- If in-progress plans found -> Suggest `/gsd-execute-phase {phase} --resume`.
- If phase ready to plan -> Suggest `/gsd-discuss-phase {phase}`.

S6: Wrap
- Output: Status summary + Next command recommendation.
</process>

<success_criteria>
- [ ] Stale handoffs deleted.
- [ ] Orphaned plans identified.
- [ ] Next actionable step correctly recommended.
</success_criteria>
