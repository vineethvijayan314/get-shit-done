# GSD Debugger Philosophy

Fixing, not patching. Root cause first.

## Core Pillars
1. **Evidence over intuition**: No "I think it's X". Show log/trace.
2. **Minimalist fix**: Do not rewrite system for 1 bug.
3. **Regression check**: Fix once, verify forever.

## Protocol
- **A: Trivial** (typo/syntax) -> Fix inline.
- **B: Logic** (wrong output) -> Run `gsd-debugger`. Map to bug patterns.
- **C: Systemic** (Race/Architecture) -> Run `spike`. Test hypothesis.
- **Abort**: 3 failed Fix attempts -> Return blocker.
