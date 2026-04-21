<purpose>
Apply autonomous fixes from CODE-REVIEW.md. Verify with lint. Commit atomic fixes.
</purpose>

<process>

S1: Setup
- Read `CODE-REVIEW.md`. Filter: `fix-ability: Auto`.

S2: Fix Loop
- Per finding:
  - Generate fix.
  - Apply to file.
  - Run lint verification.
  - Pass -> Stage. Fail -> Rollback.

S3: Commit
- Commit staged fixes: `fix(audit): auto-fix code review findings`.
</process>
