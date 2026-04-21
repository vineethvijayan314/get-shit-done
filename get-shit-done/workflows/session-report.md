<purpose>
Log work + estimated tokens. Outcomes + decisions + git activity.
</purpose>

<process>

S1: Intake
- Sources: STATE.md (progress/blockers), Git log (recent commits), summaries written.

S2: Estimate
- Heuristic: 1 commit ≈ 5k-10k context tokens. 1 summary ≈ 2k generated.
- Note: Observable signals only. No direct API metering.

S3: Generate
- File: `.planning/reports/$(date +%Y%m%d)-session-report.md`.
- Content: Duration, Plans executed, Outcomes (files/features), Decisions, Blockers, Usage table.

S4: Show
- Progress % + commit count + file count.
</process>
