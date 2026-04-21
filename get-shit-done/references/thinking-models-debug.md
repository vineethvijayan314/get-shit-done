# GSD Thinking Model: Debug

Cognitive framework for `gsd-debugger`.

## Framework
1. **Observation**: What is happening vs What should happen?
2. **Isolation**: What changed recently? Which component holds the bug?
3. **Hypothesis**: Why is it failing? Cite 3 possibilities.
4. **Experiment**: Run minimal test to prove/disprove Hypothesis 1.

## Rules
- Evidence based.
- No blind trial-and-error.
- If failure persists -> Scale up to `gsd-manager`.
