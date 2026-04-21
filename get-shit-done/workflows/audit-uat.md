<purpose>
Cross-phase verification audit. ID pending/stale items. Generate human test plan.
</purpose>

<process>

S1: Initialize
- `gsd-sdk query audit-uat --raw`.
- Gate: 0 findings -> "All Clear" -> Exit.

S2: Categorize
- **Testable Now**: `pending`, `human_uat`, `skipped`.
- **Blocked**: `server`, `device`, `build`, `third-party`.
- Verification check: Code scan for "Testable Now" items.
  - No code match -> `stale`.
  - Rewrite match -> `needs_update`.
  - Content match -> `active`.

S3: Report
- Table 1: Actions (Active/Stale).
- Table 2: Blocked items.
- Suggestion: Close stale | Retest blocked.

S4: Human Plan
- Group by feature (Auth, UI, Data).
- Items: Phase X -> Do -> Expected.
</process>

<success_criteria>
- [ ] Active/Stale items identified.
- [ ] Blocked items separated.
- [ ] Human plan structured by feature.
</success_criteria>
