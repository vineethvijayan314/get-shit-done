# Phase: Update
Trigger: `/gsd-update [requirement_id]`

## S1: Change Request
- Agent: `gsd-roadmapper`.
- Logic: Assess impact on ROADMAP/STATE.

## S2: Propagation
- Action: Update PLAN.md if phase affected.
- Reset: Re-verify if logic changed.
