<purpose>
Freeform intent dispatcher. Natural language -> GSD Command. NO action, only routing.
</purpose>

<process>

S1: Parse
- Analyize `$ARGUMENTS`. Detect intent keywords (new, plan, ship, doc, fix, state).

S2: Match
- Core Commands: `/gsd-new-milestone`, `/gsd-plan-phase`, `/gsd-execute-phase`, `/gsd-ship`, `/gsd-ingest-docs`.
- Context check: Is project initialized?

S3: Confirm
- `AskUserQuestion(header: "Routing", question: "Matches '/gsd-{command}'. Execute?", options: [Yes, No, Edit])`.

S4: Hand-off
- IF YES -> Trigger target workflow.
- IF EDIT -> Prompt for manual correction.
</process>
