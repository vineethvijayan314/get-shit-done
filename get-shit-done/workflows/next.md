<purpose>
State-based auto-advancement. Progress detection. Intelligent routing.
</purpose>

<process>

S1: Intake
- Resolve project state: `roadmap`, `state`, `manifest`.
- Find: Highest completed phase. Target phase.

S2: Progression Logic
- IF UAT `diagnosed` -> `/gsd-plan-phase --gaps`.
- IF ROADMAP exists BUT Phase 1 not started -> `/gsd-discuss-phase 01`.
- IF Plan exists BUT no Summary -> `/gsd-execute-phase`.
- IF Execute complete BUT no Verification -> `/gsd-verify-work`.
- IF All Summary exists BUT Milestone open -> `/gsd-complete-milestone`.

S3: Confirm
- `AskUserQuestion(header: "Next Step", question: "Advance to '/gsd-{cmd}'?", options: [Yes, Alternate, No])`.

S4: Hand-off
- Trigger selected command.
</process>
