# GSD Universal Anti-Patterns
Critical failure modes. Total stops when flags present.

## Context
- **Overload**: 100+ files in prompt. (Use `sharding`).
- **Bloat**: Reading definitions (`agents/*.md`) into orchestrator.

## Logic
- **Hallucination**: Assumed API. (Use `scouting` / `grep`).
- **Drift**: Ignoring `CLAUDE.md`. (Scan mandatory rules).
- **Magic**: Assuming features "just work". (Adversarial stance).

## Process
- **Soft Review**: LGTM without edge-case trace. (Score 1-4 pillars).
- **Direct Mutate**: Writing to ROADMAP/STATE without SDK. (Use `gsd-sdk`).
- **Ghosting**: Implementation without verification. (Evidence or Fail).
