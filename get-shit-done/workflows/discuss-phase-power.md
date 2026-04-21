<purpose>
Async discovery for large phases. Batch questions into JSON/HTML. Answer at user pace. Single-pass CONTEXT generation.
</purpose>

<process>

S1: Generate
- Spawn `gsd-advisor-researcher`. Analyze PLAN/ROADMAP.
- Produce `POWER-DISCUSS-STATE.json`: structured questions, categories, dependencies.
- Render `power-discuss-ui.html` (interactive form).

S2: Answer
- User completes JSON or HTML form.
- Metadata: Track answered/pending/optional fields.

S3: Process
- Resolve `--ready` flag.
- Parse answers. Synthesize logic. Detect contradictions.

S4: Synthesize
- Produce CONTEXT.md (standard format).
- Sync artifacts to phase directory.

S5: Wrap
- Commit context. Next: `/gsd-plan-phase`.
</process>
