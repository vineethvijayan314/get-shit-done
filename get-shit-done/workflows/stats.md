<purpose>
Display project stats. Phases, Plans, Requirements, Git metrics.
</purpose>

<process>

S1: Setup
- `STATS=$(gsd-sdk query stats.json)`.

S2: Output
- Milestone: {version} {name}.
- Progress: [████████░░] {percent}% (phases).
- Plans: X/Y complete.
- Requirements: ✅ X/Y.
- Git: Commits {N}, Started {start}, Last {last}.
- Activity: {last_activity}.
</process>
