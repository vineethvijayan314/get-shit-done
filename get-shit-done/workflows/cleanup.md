<purpose>
Archive phase directories from completed milestones into `.planning/milestones/v*-phases/`.
</purpose>

<process>

S1: ID Completed Milestones
- Read `.planning/MILESTONES.md`. Filter by version (v1.0, etc.).
- List `.planning/milestones/v*-phases`.
- REQ: Only process milestones LACKING archive dir.
- If all archived: EXIT ("Nothing to clean up").

S2: Map Phases
For each milestone to clean:
- Read `.planning/milestones/v{X.Y}-ROADMAP.md`.
- Extract phases.
- Cross-check: `ls -d .planning/phases/*/`.
- Match existing dirs to milestone membership.

S3: Dry-Run
Show Summary per milestone:
- Version + Name.
- Phases to archive.
- Destination: `.planning/milestones/v{X.Y}-phases/`.
- Confirm: `AskUserQuestion`. Proceed | Cancel.

S4: Archive
For each approved milestone:
- `mkdir -p .planning/milestones/v{X.Y}-phases`.
- `mv` matching dirs from `.planning/phases/`.

S5: Commit & Report
- `gsd-sdk query commit "chore: archive milestone phases"`.
- Output: Milestone + Phase count archived.
</process>

<success_criteria>
- [ ] Milestone membership verified via ROADMAP snapshots.
- [ ] User approval for list of dirs.
- [ ] Dirs moved to versioned archive paths.
- [ ] Git commit successful.
</success_criteria>
