# Phase: Complete Milestone
Trigger: `/gsd-complete-milestone`

## S1: Sync
- Action: Final `gsd-health --repair`.
- Check: All phases `passed`. No open `BLOCKER`.

## S2: Summarize
- Agent: `gsd-roadmapper`.
- Output: `MILESTONE-SUMMARY.md`. Final score 1-10.

## S3: Snapshot
- Action: `git tag -a vX.Y -m "milestone complete"`.
- Archival: Move `.planning/` to `archive/` (optional).
