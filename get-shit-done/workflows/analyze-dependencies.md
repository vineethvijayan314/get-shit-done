<purpose>
Analyze ROADMAP.md for phase dependencies. Detect overlap/data-flow. Suggest roadmap updates.
</purpose>

<process>

S1: Load Roadmap
- Read `.planning/ROADMAP.md`.
- Extract maps: `#`, `Goal`, `Files`, `Depends on`.

S2: Infer File Mods
- Map logic:
  - DB -> Migrations/Models.
  - API -> Routes/Handlers.
  - UI -> Components/Pages.

S3: Detection
- Pairs (A, B) check:
  - Overlap: Shared files/domains.
  - Semantic: B uses what A builds.
  - Data Flow: A creates -> B consumes.

S4: Report
- Output: Phase N scope vs Suggested `Depends on`.
- Diff: Proposed roadmap updates.

S5: Confirm
- Choice: Apply | Skip Apply (Print only) | Edit.
- Apply: Update ROADMAP.md fields. Preserve order.

S6: Wrap
- Log: ROADMAP.md updated. Ready for `/gsd-manager`.
</process>

<success_criteria>
- [ ] Dependencies detected from Scope.
- [ ] Data-flow reasons provided.
- [ ] Roadmap updated safely.
</success_criteria>
