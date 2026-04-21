<purpose>
Generate AI-SPEC.md. Orchestrate framework-selector -> research -> eval-planner. Lock before planning.
</purpose>

<process>

S1: Init
- `gsd-sdk query init.plan-phase "$PHASE"`.
- Agent list: `framework-selector`, `ai-researcher`, `domain-researcher`, `eval-planner`.
- Gate: `workflow.ai_integration_phase == true`.

S2: Parse Phase
- `gsd-sdk query roadmap.get-phase "${PHASE}"`.
- REQ: Phase exists.

S3: AI-SPEC Exist Check
- Find `*-AI-SPEC.md`.
- Found -> Update | View | Skip choice.

S4: Framework Selection
- Task(gsd-framework-selector).
- Inputs: Goal, CONTEXT.md, REQUIREMENTS.md.
- Output: `primary_framework`, `system_type`, `model_provider`, `eval_concerns`.
- REQ: Non-empty result.

S5: Init AI-SPEC
- Template: `~/.claude/get-shit-done/templates/AI-SPEC.md`.
- Inject: Header, Classification, Framework.

S6: Research
- Task(gsd-ai-researcher).
- Action: Write AI-SPEC Sections 3 + 4.
- Content: Framework docs, patterns, pitfalls.

S7: Domain Validation
- Task(gsd-domain-researcher).
- Action: Write AI-SPEC Section 1b.
- Content: Expert eval rubrics, failure modes.

S8: Eval Planning
- Task(gsd-eval-planner).
- Action: Write Sections 5, 6, 7.
- Content: Strategy, guardrails, reference dataset.

S9: Completion
- `git commit`: `docs({phase}): generate AI-SPEC.md`.
- Summary: Framework + System Type + Eval Dimensions.
- Next: `/gsd-plan-phase {N}`.
</process>

<success_criteria>
- [ ] AI-SPEC.md created + validated.
- [ ] Framework docs researched.
- [ ] Domain rubrics included.
- [ ] 0 placeholders.
</success_criteria>
