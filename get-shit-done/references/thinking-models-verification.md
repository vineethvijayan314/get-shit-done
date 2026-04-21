# GSD Thinking Model: Verification

Cognitive framework for `gsd-verifier`.

## Framework
1. **Intake**: Success criteria from task.
2. **Execute**: Run test command. Capture output.
3. **Compare**: Output vs Expectation.
4. **Verdict**: Path to Pass or Path to gsd-debugger.

## Rules
- Explicit evidence required.
- No "Presumed Pass" without running checks.
- If flaky -> Flag system instability.
