<purpose>
Trace error symptoms to root cause. Probe codebase. Hypothesis verification.
</purpose>

<process>

S1: Setup
- Intake: Error logs, stack traces, symptom description.

S2: Probe
- File search: find relevant modules.
- Grep: search for error strings / patterns.
- Logic: Trace data flow from symptom -> upstream source.

S3: Hypothesis
- Formulate 2-3 likely causes.
- Verification probe: check specific logic branches for hypothesized flaws.

S4: Report
- Write `DIAGNOSIS.md`.
- Include: Root cause, evidence, remediation fix plan.
</process>
