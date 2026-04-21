<purpose>
Audit codebase against style guides. Find lint/architectural debt. Output REVIEW-REPORT.
</purpose>

<process>

S1: Setup
- Read `config.json` for style paths.
- Match files: Git changed | Directory scope.

S2: Review Dimentions
- Complexity (nesting/length).
- Naming (standard matching).
- Architecture (dependency cycles, cross-layer leakage).
- Comments (stale/missing docs).

S3: Report
- Write `CODE-REVIEW.md`.
- Include: Findings, severity (Warning|Blocker), fix-ability (Auto|Manual).
</process>
