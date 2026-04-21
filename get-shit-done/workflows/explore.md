<purpose>
Socratic ideation. Crystalize raw ideas. Probing questions. Mid-thread research. Routes to GSD artifacts.
</purpose>

<process>

S1: Intake
- Raw input `$TOPIC`. Goal: Define boundary + value prop.

S2: Probe
- Interactive loop. Questions focus on: Users, technical constraints, viability.
- Logic: `AskUserQuestion`. Limit 5-7 questions to prevent fatigue.

S3: Research
- IF research needed -> `AskUserQuestion` (Research now?).
- Spawn `gsd-advisor-researcher`. Update probe pool based on findings.

S4: Synthesize
- Format finalized idea: Goal, Context, Acceptance Criteria.

S5: Route
- `AskUserQuestion(header: "Route Output", question: "Save as?", options: [Todo, Phase, Note, README])`.
- Move content to target GSD file.
</process>
