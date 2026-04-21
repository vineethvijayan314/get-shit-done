<purpose>
Autonomous audit-to-fix pipeline. Classify findings -> Spawn executors -> Run tests -> Commit.
</purpose>

<process>

S1: Parse Args
- `--max N`: Fix limit (5).
- `--severity`: Threshold (medium).
- `--dry-run`: Classification only.

S2: Run Audit
- Invoke `gsd-sdk query audit-uat`.
- Inputs: `*-UAT.md`, `*-VERIFICATION.md`.

S3: Classification
- **auto-fixable**: Single file, specific line, clear fix (typo, missing export).
- **manual-only**: Ambiguous, architectural, multi-file.
- Logic: Uncertainty -> manual-only.

S4: Fix Loop
- Per **auto-fixable** finding (DESC severity, up to `--max`):
  1. Spawn `gsd-executor`. Fix specific ID. Minimal delta.
  2. Test: `npm test`.
  3. Pass: `git commit -m "fix({scope}): resolve {ID}"`.
  4. Fail: `git checkout -- {files}`. STOP.

S5: Report
- Output: Table (# | Status | Commit).
- Action: List remaining manual-only items.
</process>

<success_criteria>
- [ ] Atomic commits per fix.
- [ ] Rollback + Stop on test fail.
- [ ] IDs in commit messages.
</success_criteria>
