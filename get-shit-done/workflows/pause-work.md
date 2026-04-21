<purpose>
Cross-session handoff. State preservation. JSON (machine) + Markdown (human).
</purpose>

<process>

S1: Intake
- Current Phase, Plan, Task, Cursor (execution_context).
- Recent git commits (log -5).
- Unfinished work (STATE.md, TODOs).

S2: Write JSON
- `.planning/HANDOFF.json`.
- Schema: phase, plan, task_status, modified_files, next_action.

S3: Write Human
- `.continue-here.md`.
- Content: Status Summary, Blocks, Next Step command (ready to copy).

S4: Sync
- Commit handoff files if project exists.
</process>
