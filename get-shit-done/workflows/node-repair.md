<purpose>
Audit and repair node_modules / package.json locks. Missing deps | Version drift.
</purpose>

<process>

S1: Setup
- Read `package.json`.
- Detect manager: npm | yarn | pnpm | bun.

S2: Probe
- Integrity check: `npm audit` / `ls node_modules`.
- Missing deps: find imports in src with no entry in package.json.

S3: Repair
- Action: reinstall | sync lock | prune stale.
- `gsd-sdk query install.deps`.

S4: Verification
- Run: `npm test` / build check.
</process>

<success_criteria>
- [ ] node_modules synchronized with package.json.
- [ ] Unused deps pruned.
- [ ] Build passes.
</success_criteria>
