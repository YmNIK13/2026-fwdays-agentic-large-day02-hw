# Review Code

## Overview

Review the selected code, file, or diff with a code review mindset. Focus on correctness, regressions, risks, and missing coverage before style or refactoring suggestions.

## Steps

1. **Understand the Change**
   - Read the selected code and the surrounding context
   - Identify the intended behavior and affected code paths
   - Check nearby files when needed to validate assumptions
2. **Find Real Issues**
   - Prioritize bugs, behavioral regressions, race conditions, security risks, and data consistency issues
   - Check edge cases, nullability, mutation side effects, and API contract mismatches
   - Review performance only where it could materially affect behavior or scale
3. **Validate Against Project Conventions**
   - Follow the local rules in `.cursor/rules`
   - Check TypeScript safety, naming, exports, and package-specific invariants
   - Flag missing tests when the change affects risky or stateful logic
4. **Report Clearly**
   - List findings first, ordered by severity
   - Include file and line references when possible
   - Explain why the issue matters and what change would address it
   - If there are no findings, state that explicitly and mention residual risks or testing gaps

## Output Format

- Start with `Findings`
- Use a short, flat list ordered by severity
- Keep each finding concrete: problem, impact, and suggested fix
- Follow with `Open Questions` or `Residual Risks` only if needed
- Add a short summary only after the findings

## Review Checklist

- [ ] Understood the intended behavior and affected code paths
- [ ] Checked for correctness bugs and regressions
- [ ] Checked risky edge cases and state transitions
- [ ] Checked security or data integrity concerns where relevant
- [ ] Checked whether project conventions or module invariants were violated
- [ ] Noted missing or weak test coverage
- [ ] Reported findings first, ordered by severity
- [ ] Explicitly stated when no findings were found
