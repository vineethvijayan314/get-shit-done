<purpose>
Execute specific PLAN.md. Produce SUMMARY.md. Commit tasks atomically. Handle deviations/checkpoints.
</purpose>

<process>

S1: Initialize
- Parse Args: `${PHASE}`, `${PLAN}`.
- `gsd-sdk query init.execute-phase`.

S2: Routing (Pattern A/B/C)
- **Threshold**: `workflow.inline_plan_threshold` (default: 2).
- If tasks <= threshold -> Pattern C (Inline).
- If tasks > threshold:
  - No checkpoints -> Pattern A (Autonomous Subagent).
  - Verify-only checkpoints -> Pattern B (Segmented Subagent).
  - Decision checkpoints -> Pattern C (Inline).

S3: Init Agent Tracking
- Check `.monitoring/agent-history.json`.
- Tracking REQ: `current-agent-id.txt`. If interrupted, ask to resume.
- Proto: Status `spawned` -> `completed`.

S4: Pattern A/B Execution (Subagent)
- Task(gsd-executor):
  - REQ: `isolation="worktree"` (if enabled).
  - Guard: `git reset --hard {EXPECTED_BASE}` (correction).
  - Proto: Single Task call per message. `run_in_background: true`.
  - Content: `<parallel_execution>` rules (no-verify commits, skip shared-file writes).
- Wait for Join. Fallback to SUMMARY.md + git log if signal lost.

S5: Pattern C Execution (Inline)
- Execute `execute-plan.md` steps directly.
- Use normal commits (with hooks).

S6: Execute Protocol (Tasks)
- **MANDATORY read_first**: Read listed files BEFORE ANY EDITS.
- **TDD Flow**: RED -> failing test | GREEN -> implementation | REFACTOR -> cleanup.
- **Commit**: `{type}({phase}-{plan}): {desc}`.
- **Verification Gate**: REQ pass `acceptance_criteria` before next task.

S7: Checkpoint Protocol
- STOP on `type="checkpoint:*"`.
- Show: Progress, Task name, Action needed.
- Types: `human-verify` | `decision` | `human-action`.
- If subagent: return structured state -> Orchestrator handles.

S8: Auth & Deviation Gates
- **Auth**: Indicators (401/403/Unauthorized). Dynamic `checkpoint:human-action`.
- **Deviation**: Rule 1-3 (Auto-fix bugs/missing) | Rule 4 (Architectural -> STOP). Fix limit: 3 retries.

S9: Verification Failure Gate
- `workflow.node_repair` (default: true).
- If fail: invoke `node-repair.md` (budget: 2).
- ESCALATE if repair fails.

S10: Finalize & Summary
- Create `*-SUMMARY.md`. REQ: submarine one-liner, tracked durations, task counts.
- `requirements-completed`: mapped from PLAN.md frontmatter.
- Update tracking (only in sequential mode): STATE.md, ROADMAP.md.

S11: Worktree Cleanup
- Merge WT branch (Main wins for STATE/ROADMAP).
- Rescue uncommitted summary if agent skipped.
- `git worktree remove --force`.
- Delete WT branch.

S12: Completion
- Show: Duration, Tasks, SUMMARY path.
- Next: `/gsd-execute-phase` (more plans) | `/gsd-verify-work` | `/gsd-new-milestone`.
</process>

<success_criteria>
- [ ] Pattern routing (A/B/C) functional.
- [ ] `read_first` gate enforced.
- [ ] TDD RED-GREEN-REFACTOR commits.
- [ ] Acceptance criteria verification gate clears.
- [ ] Shared files protected in parallel merge.
- [ ] SUMMARY.md matches template.
- [ ] Requirements marked complete.
</success_criteria>
