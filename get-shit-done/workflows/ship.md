<purpose>
Create PR from phase/milestone work. Generate body. push. mergable setup.
</purpose>

<process>

S1: Setup
- Resolve phase: `PHASE_ARG` -> ` padded_phase`.
- Load config: `branching_strategy`, `BASE_BRANCH`.
- Check auth: `gh auth status`.

S2: Preflight
- Verification passed? (status: passed/human_needed).
- Tree clean? (git status).
- Branch correct? (not on base).
- Remote exists? (origin).

S3: Push
- `git push origin ${BRANCH} --set-upstream`.

S4: PR Body
- Title: Phase {N}: {Name}.
- Goal: {ROADMAP goal}.
- Changes: {Summarized from SUMMARY.md files}.
- Verification: {Result from VERIFICATION.md}.
- Decisions: {Extracted from STATE.md}.

S5: Create PR
- `gh pr create --title ... --body ... --base ${BASE} [--draft]`.

S6: Review Call
- Check `config.workflow.code_review_command`.
- IF set -> run external reviewer (timeout 120s) -> show verdict.
- Ask user: Skip | Self-review | Request from team (`gh pr edit --add-reviewer`).

S7: Track
- Update STATE.md: "Phase {N} shipped — PR #{M}".
- Commit docs if enabled.
</process>
