# Phase: Transition
Trigger: `/gsd-transition [next_phase]`

## S1: Close
- Logic: `gsd-sdk query state.save`.
- Action: Mark current phase `passed` in ROADMAP.md.

## S2: Open
- Action: Initialize `[next_phase]` directory.
- Copy: `STATE.md`, `ROADMAP.md` into new phase context.
