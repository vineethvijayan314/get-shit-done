# Phase: Ingest Docs
Trigger: `/gsd-ingest-docs [path]`

## S1: Scan
- Agent: `gsd-doc-classifier`.
- Logic: Glob `[path]`. Identify: ADR (Accepted/Proposed), PRD, SPEC, DOC.

## S2: Index
- Action: Map metadata to JSON hash files.
- Path: POSIX-style path hashing.

## S3: Map
- Update: SITE-MAP.md or INDEX.md with new references.
