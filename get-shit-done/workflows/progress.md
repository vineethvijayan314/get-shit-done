<purpose>
Visual progress report. Situational awareness. Next action routing. Forensic audit.
</purpose>

<process>

S1: Setup
- Resolve: `roadmap_exists`, `state_exists`, `milestone_version`.
- Load snapshot: `gsd-sdk query roadmap.analyze`, `gsd-sdk query state-snapshot`.

S2: Report
- Visual: Progress bar + Profile + Discuss Mode.
- Content: Recent work (summaries), Position (phase/plan), Decisions (STATE), Blockers (STATE), Todos (count).

S3: Routing Logic
- IF UAT entries `diagnosed` -> Offer /gsd-plan-phase --gaps.
- IF UAT entries `partial` -> Offer /gsd-verify-work.
- IF plan_count > summary_count -> Offer /gsd-execute-phase.
- IF plans = 0 -> Offer /gsd-discuss-phase (or /gsd-ui-phase).
- IF current = highest -> Offer /gsd-complete-milestone.

S4: Forensic Audit (Optional `--forensic`)
1. **Consistency**: STATE vs Artifact count.
2. **Orphans**: Check HANDOFF.json / .continue-here.md.
3. **Drift**: Check ROADMAP vs deferred references in code.
4. **Memory**: Check MEMORY.md for unaddressed flags.
5. **Operational**: Check pending todos for BLOCKING keywords.
6. **Git**: Check uncommitted source code (excluding .planning/).

S5: Verdict
- CLEAN -> Procedural routing.
- INTEGRITY ISSUE -> Highlight flags + corrective actions.
</process>
