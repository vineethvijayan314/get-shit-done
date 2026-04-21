<purpose>
Validate .planning/ integrity. Missing files / Invalid config / Stale states.
</purpose>

<process>

S1: Setup
- Parse `$ARGUMENTS` for `--repair`.

S2: Check
- `gsd-sdk query validate.health $REPAIR_FLAG`.
- Results: Status (healthy|degraded|broken), Errors, Warnings, Repairable count.

S3: Diagnostics
- PROJECT.md missing? (E002).
- config.json parse error? (E001/E005).
- STATE.md sync issue? (W002).
- Phase directory naming (W005).
- Claude tasks accumulation (I002).

S4: Repair
- Action (if --repair): createConfig, resetConfig, regenerateState, addNyquistKey.
- Windows/mac cleanup: `rm -rf ~/.claude/tasks/*` for dead subagents.

S5: Report
- Output status summary.
- Suggest: `/gsd-health --repair` if errors found.
</process>
