<purpose>
Orchestrate phase execution. Wave-based parallel spawning or sequential inline.
</purpose>

<process>

S1: Initialize
- Parse Args: `${PHASE}`, `--wave`, `--gaps-only`, `--cross-ai`.
- `gsd-sdk query init.execute-phase`.
- Sync: Clear `_auto_chain_active` if not `--auto`.
- Guard: `.gitmodules` -> Fallback sequential (no worktrees).

S2: Blocking Anti-Patterns
- Check `${phase_dir}/.continue-here.md`.
- REQ: If `severity="blocking"`, explain What/Manifest/Fix for each.

S3: Interactive Mode
- Activated by: `--interactive`.
- Logic: Skip spawning. Execute `execute-plan.md` INLINE sequentially.
- Task checkpoints: Pause after every task for user feedback.

S4: Plan Discovery & Grouping
- `gsd-sdk query phase-plan-index`.
- Filtering: Skip completed plans. Apply gaps/wave filters.
- Prerequisite: Fail if Wave N+1 started with Wave N incomplete.
- Show: Execution table (Wave | Plans | Objective).

S5: Cross-AI Delegation
- Activated by: `--cross-ai` or `cross_ai: true` frontmatter.
- Logic: Execute via `workflow.cross_ai_command` with stdin delivery.
- REQ: Successful SUMMARY.md and non-zero exit before marking complete.

S6: Wave Execution (Parallel)
- Check: Intra-wave `files_modified` overlap. Overlap -> Force sequential for wave.
- Describe Wave: 2-3 sentences per plan (What/How/Why).
- Spawn: `gsd-executor` with `isolation="worktree"`.
- Dispatch REQ: Sequential dispatch (single Task call per message) to avoid `.git/config.lock` race.
- Branch Guard: Agent MUST `git reset --hard {EXPECTED_BASE}` first.

S7: Wave Execution (Sequential Fallback)
- Trigger: Worktrees disabled OR Copilot runtime.
- Logic: Dispatch `gsd-executor` WITHOUT `isolation` OR execute inline.

S8: Join & Merge (Parallel)
- Wait for agents. Fallback to filesystem spot-checks if signal fails.
- Hook Check: Run `pre-commit` once after wave.
- Merge Logic:
  - FF-check: Main always wins for STATE.md/ROADMAP.md.
  - Deletion guard: Block if worktree deleted files.
  - Resurrection guard: `git rm` files re-added by merge but absent in Main.
  - Rescue SUMMARY.md: Commit if agent skipped.
- Cleanup: `git worktree remove --force`.

S9: Integration Tests
- Script: `npm test` | `cargo test` | `pytest`.
- Guard: If test fail/timeout -> Skip tracking update. DO NOT mark plans complete.

S10: Tracking Update
- `gsd-sdk query roadmap.update-plan-progress`.
- `gsd-sdk query commit "docs(phase): update tracking after wave"`.

S11: Completion
- Show summary results.
- Handoff: `/gsd-verify-work`.
</process>

<success_criteria>
- [ ] Wavestructure respected. Prereqs enforced.
- [ ] Concurrent worktrees used with sequential dispatch.
- [ ] Branch reset guard active in subagents.
- [ ] Shared files (STATE/ROADMAP) protected during merge.
- [ ] Post-merge test gate catches integration conflicts.
- [ ] Resurrection guard prevents zombie files.
</success_criteria>
