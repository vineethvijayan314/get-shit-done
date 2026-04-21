<purpose>
Verify AI integration phase goals. AI-eval review. Bottleneck detection.
</purpose>

<process>

S1: Setup
- `INIT=$(gsd-sdk query init.eval-review)`.
- Load: `EVALS.md`, `RESULTS.csv`, `METRICS.json`.

S2: Truths
- Accuracy > threshold?
- Latency < limit?
- Token cost within plan?

S3: Verification
- Logic: Check code for eval harness. Verify datasets exist.
- Metric scan: Extract pass rates from logs.

S4: Report
- Write `EVAL-VERIFICATION.md`.
- Include: Metrics vs Goals, Bottlenecks found, Optimization fix plans.
</process>
