<purpose>
Offload planning to cloud infrastructure. High-performance generation. Complex logic.
</purpose>

<process>

S1: Setup
- Resolve phase context (ROADMAP, CONTEXT.md).
- Pack context: `gsd-sdk query pack-phase-context`.

S2: Dispatch
- Command: `gsd-sdk ultraplan --phase {N}`.
- Logic: Background async processing.

S3: Reception
- Pull results from cloud buffer.
- Unpack PLAN.md files to phase directory.

S4: Verify
- Validate syntax + integrity vs local PROJECT.md.
</process>
