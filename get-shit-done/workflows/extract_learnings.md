# Phase: Extract Learnings
Trigger: Post-verify cleanup

## S1: Analyze
- Agent: `gsd-doc-classifier`.
- Logic: Load PLAN, SUMMARY, VERIFICATION.
- Categories: Decisions, Lessons, Patterns, Surprises.

## S2: Capture
- Skill: `capture_thought` (if available).
- Route: Extracted items to memory/index.

## S3: Write
- Output: `${PHASE}-LEARNINGS.md`.
- State: Update `Last Activity` in STATE.md.
