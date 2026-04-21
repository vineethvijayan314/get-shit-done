<purpose>
Show GSD command reference. NO analysis. NO git status. Reference ONLY.
</purpose>

<reference>
# GSD Command Reference

## Core Flow
`/gsd-new-project` → `/gsd-plan-phase` → `/gsd-execute-phase` → repeat

## Initialization
- `/gsd-new-project`: Idea to Roadmap. Questioning + Research + Req + Roadmap.
- `/gsd-map-codebase`: Analyze existing codebase. Tech/Arch/Quality focus.
- `/gsd-new-milestone`: New milestone flow. PRD Express: `--prd <path>`.

## Planning
- `/gsd-discuss-phase <N>`: Context intake. `--batch` for efficiency.
- `/gsd-research-phase <N>`: Domain deep-dive. Ecosystem discovery.
- `/gsd-list-phase-assumptions <N>`: Preview approach before plan.
- `/gsd-plan-phase <N>`: Create atomic PLAN.md. 
- `/gsd-ultraplan-phase <N>`: Heavyweight planning for massive codebases.

## Execution
- `/gsd-execute-phase <N>`: Run wave-based parallel execution. 
- `/gsd-execute-plan <path>`: Run single plan file.
- `/gsd-do <text>`: Smart router to GSD commands.
- `/gsd-quick [--full|--validate]`: Rapid planning/execution for small tasks.
- `/gsd-fast <msg>`: Trivial inline edits. Atomic commit.

## Progression
- `/gsd-progress`: Visual progress bar + next action router.
- `/gsd-resume-work`: Restore context from STATE.md.
- `/gsd-pause-work`: Create context handoff (.continue-here).
- `/gsd-transition <N>`: Advance project state after phase.

## Debugging & Spikes
- `/gsd-debug <issue>`: Systematic investigation. Science-based method.
- `/gsd-spike <idea>`: Feasibility experiments. MANIFEST tracking.
- `/gsd-sketch <ui>`: UI/Design exploration. Multi-variant mockups.
- `/gsd-spike-wrap-up`: Convert findings to Persistent Skills.
- `/gsd-sketch-wrap-up`: Convert design winners to Persistent Skills.

## Capture
- `/gsd-note <text>`: Zero-friction note capture. `--global` support.
- `/gsd-add-todo`: Extract task to .planning/todos/pending/.
- `/gsd-check-todos [area]`: Triage/execute pending todos.

## Quality & Shipping
- `/gsd-verify-work <N>`: Conversational UAT. Diagnoses failures.
- `/gsd-ship <N>`: Generate PR body + push. `--draft` support.
- `/gsd-review --phase <N>`: Cross-AI peer review (Gemini/Claude/etc).
- `/gsd-pr-branch [target]`: Filter transient planning commits for clean PRs.
- `/gsd-plant-seed <idea>`: Forward-looking triggers for future milestones.

## Auditing
- `/gsd-audit-uat`: Cross-phase verification debt scan.
- `/gsd-audit-milestone`: Requirement coverage + wiring audit.
- `/gsd-health [--repair]`: Integrity check .planning/ FS.
- `/gsd-inbox`: GitHub Issue/PR triage + gate enforcement.

## Preferences
- `/gsd-settings`: Interactive config. Toggles: Researcher/Checker/Verifier.
- `/gsd-set-profile <profile>`: Switch model profile (quality|balanced|budget).

## Utilities
- `/gsd-cleanup`: Archive stale phase dirs.
- `/gsd-stats`: Visual project metrics + git stats.
- `/gsd-session-report`: Log work + resource usage summary.
- `/gsd-update`: Check version + changelog + install.
</reference>
