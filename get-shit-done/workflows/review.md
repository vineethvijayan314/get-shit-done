<purpose>
Cross-AI Peer Review. Invoke external AI CLIs. Synthesize feedback.incorporate via --reviews.
</purpose>

<process>

S1: Setup
- Find CLIs: gemini, claude, codex, coderabbit, opencode, qwen, cursor.
- Flags: `--all` | `--model` per runtime.
- Skip: `SELF_CLI` (independence guard).

S2: Context
- Load PROJECT.md (top 80), ROADMAP phase section, PLAN.md files, REQUIREMENTS.md.

S3: Prompt
- Task: Professional security/arch/quality review.
- Output: Markdown (Summary, Strengths, Concerns (H/M/L), Suggestions, Risk).

S4: Invoke
- Run each CLI in sequence. Redirect output to `/tmp/gsd-review-{CLI}-{phase}.md`.
- Timeout: 360s (CodeRabbit support).

S5: Synthesize
- Combine into `${PHASE_DIR}/${PADDED_PHASE}-REVIEWS.md`.
- Sections: Per-AI Review + Consensus Summary (Shared Strengths/Concerns) + Divergent Views.

S6: Finalize
- Commit report. Next: `/gsd-plan-phase {N} --reviews`.
</process>
