# Workflow: Health
Trigger: `/gsd-health [--repair] [--backfill]`

## S1: Scan
- Logic: `gsd-sdk query validate.health $REPAIR_FLAG $BACKFILL_FLAG`.
- Check: config, PROJECT, ROADMAP, STATE.

## S2: Repair
- If `--repair`: createConfig, resetConfig, regenerateState.
- If `--backfill`: backfill milestones.

## S3: Report
- Status: healthy | degraded | broken.
- List: Errors [E-XX], Warnings [W-XX].
