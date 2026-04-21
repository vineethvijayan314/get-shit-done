# GSD Decimal Phase Calculation

Sub-phase numbering logic.

## Goal
Enable granular progress tracking within a single roadmap phase.

## Format
- Root: `Phase 01`
- Sub: `Phase 01.1`, `Phase 01.2`

## Logic
1. `gsd-add-phase --decimal`.
2. Insert after Parent phase.
3. Roadmap stats count decimal as 1/N of Parent weight.
