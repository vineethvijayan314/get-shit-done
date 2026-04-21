<purpose>
Close audit gaps. Group MILESTONE-AUDIT findings into phases. Auto-insert into ROADMAP.md.
</purpose>

<process>

S1: Intake
- Read `.planning/MILESTONE-AUDIT.md`. Find `[ ]` gaps.

S2: Group
- Resolve logical grouping (Dependencies, Area, Priority).
- Create 1-3 new fix phases.

S3: Roadmap Update
- Logic: `gsd-roadmapper`. Insert after highest completed phase.
- Status: `pending`. Theme: `remediation`.

S4: Offer Plan
- `AskUserQuestion(header: "Plan Now?", question: "Proceed to /gsd-plan-phase {N}?", options: [Each, All, No])`.
</process>
