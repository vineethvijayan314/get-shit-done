<purpose>
Triage GitHub issues/PRs. Check templates. Gate enforcement. Action summary.
</purpose>

<process>

S1: Setup
- Check `gh` auth.
- Detect repo: `gh repo view --json nameWithOwner`.
- Flags: `--issues`, `--prs`, `--label`, `--close-incomplete`.

S2: Fetch
- Issues: `gh issue list --state open --json ...` (limit 100).
- PRs: `gh pr list --state open --json ...`.

S3: Review (Issues)
- Logic: Match vs template (Feature/Bug/Enhancement/Chore).
- Score: (fields_present / required) * 100.
- Labels: `needs-review`, `needs-triage`.

S4: Review (PRs)
- Checklist: Template used? Issue linked? Approved gate? CI passing?
- Gate Check: PR exists -> Linked Issue APPROVED? (BLOCKER).

S5: Report
- Generate `.planning/INBOX-TRIAGE.md`.
- Summary table + Gate violations + attention items + ready for merge.

S6: Action (Optional)
- `--label`: Auto-add recommended labels.
- `--close-incomplete`: Close <50% score OR gate violation with comment.
- Requires user confirmation.
</process>
