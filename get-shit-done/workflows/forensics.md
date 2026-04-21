<purpose>
Post-mortem investigation. Scan git/artifacts/FS. Detect anomalies. hypothesis -> action.
</purpose>

<process>

S1: Intake
- Describe problem: Stuck, silent fail, high cost.

S2: Evidence Collection
- Git: log (last 30), timestamps, repeated file edits (`uniq -c`), status, stat.
- State: STATE.md (milestone/phase/blockers), ROADMAP.md.
- Artifacts: phases/* (PLAN/SUMMARY/VERIFICATION/CONTEXT/RESEARCH).
- System: `git worktree list`, `.planning/reports/SESSION_REPORT.md`.

S3: Detection Patterns
- Stuck Loop: 3+ consecutive commits on same file + similar message. Confidence: HIGH.
- Missing Artifact: Phase complete in roadmap/git but file missing.
- Abandoned: STATE shows active + last commit > 2h old + dirty FS.
- Crash: Dirty FS + active entry + orphaned worktrees.
- Drift: Touched files outside plan scope.
- Regression: Message contains "fix test", "revert", "broken".

S4: Forensic Report
- Generate: `report-$(date).md`.
- Sections: intake, git summary, artifact heatmap, anomaly list, root cause hypothesis.
- Recommended actions + recovery commands.

S5: Issues & repair
- Redaction: relative paths only, no keys/tokens.
- Action: Offer GitHub issue creation (`gh issue create`).

S6: Wrap
- `gsd-sdk query state.record-session`.
</process>

<success_criteria>
- [ ] Anomalies detected via git/state correlation.
- [ ] Hypothesis grounded in evidence.
- [ ] Redacted report saved + presented.
</success_criteria>
