# GSD AI Evaluations

Quality benchmarks. Performance audit. Model profiling.

## Audit Metrics
- **Logic Accuracy**: instruction match. No drift.
- **Verification Strength**: Test pass rate. Code coverage.
- **Token Density**: Value per byte. Fluff detection.
- **Integrity**: Conventional commit match. State sync.

## Process
1. Run `gsd-eval-planner`. Define metrics.
2. Run `gsd-eval-auditor`. Analyze SESSION-LOG.md.
3. Compare vs `MODEL-PROFILE.json`.
4. Output: `EVALUATION.md`. Give score [0-100].
