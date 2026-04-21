<purpose>
Audit TODOs/FIXMEs. Sync with ROADMAP. Find stale comments.
</purpose>

<process>

S1: Setup
- Scan: Git tracked files | Scope.

S2: Probe
- `grep -rn -E "TODO|FIXME|XXX"`.
- Results: File, Line, Content.

S3: Correlation
- Match TODO content against STATE.md active blockers.
- Status: Stale (not in state) | Active (mapped) | Orphan (debt).

S4: Report
- Display table: Todo, Status, Age (git blame).
- Suggest: `/gsd-add-todo` for orphan debt.
</process>
