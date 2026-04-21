# GSD Context Budget

Guidelines for managing LLM context token usage.

## Thresholds
- **Critical (75%+)**: ABORT. Split phase. Checkpoint required.
- **Warning (50-75%)**: Alert user. Recommend summary extraction.
- **Healthy (<50%)**: Normal operations.

## Strategies
- **Sharding**: Move large logic to subagents. Orchestrator reads only interfaces.
- **Ghosting**: Use `@file` references instead of inlining content.
- **Cavemanification**: Use terse fragments (Tiers: Lite/Full/Ultra).
- **TTL**: Rotate logs. Clear stale subagent tasks.
