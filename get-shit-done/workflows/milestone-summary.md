<purpose>
Onboarding summary from milestone artifacts. Human-friendly overview. Git stats.
</purpose>

<process>

S1: Setup
- Resolve version: `v{VERSION}`. Check STATE.md | milestones/ | ROADMAP.md.

S2: Discover
- Source A: Archived (milestones/vN-*) | Current (.planning/*).
- Phase docs: SUMMARY, VERIFICATION, CONTEXT, RESEARCH.

S3: Git Stats
- Boundary: tag `v{VERSION}` OR `since="{started_at}"` OR earliest `.planning/phases/` commit.
- Stats: Commits, LOC (+/-), Timeline, Contributors.

S4: Generate
- File: `.planning/reports/MILESTONE_SUMMARY-v${VERSION}.md`.
- Content: Vision (PROJECT), Tech Arch (CONTEXT), Delivered (Table), Requirements (Traceability), Tech Debt (VERIFICATION/RETRO).

S5: Wrap
- Commit: `docs(v{VERSION}): generate milestone summary`.
- Show inline. Ask interactive followup questions.
</process>
