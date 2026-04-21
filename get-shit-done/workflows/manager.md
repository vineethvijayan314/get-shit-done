<purpose>
Interactive terminal dashboard. Multi-phase management. Background orchestration.
</purpose>

<process>

S1: Setup
- Load `.planning/ROADMAP.md` + `.planning/STATE.md`.
- Snapshot current workspace health.

S2: Render
- UI: Visual Dashboard (Phase list, status icons, progress bars).
- Data: `gsd-sdk query roadmap.status`.

S3: Interaction Loop
- Input: `[1-N]` (Phase), `[n/m]` (New Milestone), `[p]` (Refresh), `[q]` (Exit).
- IF Phase selected -> Show submenu: `Discuss | Plan | Execute | Verify`.

S4: Dispatch
- Logic: Background task execution.
- Command: `AskUserQuestion(header: "Action", question: "Start background agent?", options: [Yes, No])`.
- IF YES -> Spawn subagent + monitor via statusline.

S5: Refresh
- On subagent completion -> reload roadmap status -> Render frame.
</process>
