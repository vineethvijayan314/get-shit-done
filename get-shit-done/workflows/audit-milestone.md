<purpose>
Verify milestone closure. Aggregate phase verifications, check integration, and trace requirements.
</purpose>

<process>

S0: Init
- `gsd-sdk query init.milestone-op`.
- Resolve `gsd-integration-checker`.

S1: Scope
- List phase dirs.
- Read ROADMAP.md (Milestone DoD).
- Read REQUIREMENTS.md (Traceability map).

S2: Aggregation
- Read all phase `VERIFICATION.md` files.
- Catch: missing files -> BLOCK.
- Extract: debt, gaps, anti-patterns.

S3: Integration Check
- Task(gsd-integration-checker).
- Action: ID integration gaps (API routes, E2E flows).
- Map to REQ-IDs.

S4: 3-Source Requirements Matrix
- Trace REQ-ID:
  1. REQUIREMENTS.md (Traceability map `[x]`).
  2. Phase VERIFICATION.md (Requirement table).
  3. SUMMARY.md (YAML frontmatter).
- Logic: satisfied = (Pass in VERIFICATION AND Listed in SUMMARY AND [x] in Traceability).
- Fail gate: unsatisfied REQ -> `gaps_found`.

S5: Nyquist Scan
- Trace COMPLIANT | PARTIAL | MISSING phases.

S6: Aggregate Report
- Path: `.planning/v{version}-MILESTONE-AUDIT.md`.
- Contents: Scores (Integration, Flows, REQs) + Gap Object (REQ failures + evidence).

S7: Wrap
- Output: Audit path + scores.
- Next: `/gsd-complete-milestone` (Success) | `/gsd-plan-milestone-gaps` (Fail).
</process>

<success_criteria>
- [ ] 3-source cross-ref complete.
- [ ] Orphaned REQs identified.
- [ ] Audit file written with gap objects.
</success_criteria>
