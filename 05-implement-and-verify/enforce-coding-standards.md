# Enforce Coding Standards with Executable Checks

## What It Means

- Executable standards are rules enforced by tests, linters, type checkers, formatters, build tools, or CI.
- Prose explains judgment and intent; tools enforce objective, repeatable conditions.
- A goal command gives agents and humans the same completion check.

## Why It Matters

- Agents can forget written standards, especially in long sessions.
- Automated checks apply consistently across models, tools, and contributors.

## Concrete Example

- Prose says exports must prevent spreadsheet formulas, but agents repeatedly forget.
- Add parameterized tests for dangerous prefixes and run them in CI.
- Keep prose explaining the security reason and location of the check.
- Now every human and agent receives the same pass/fail signal.

## Best Practices

- Automate rules that can be detected reliably.
- Keep subjective design guidance in concise project instructions and review rubrics.
- Run focused checks during work and the full required checks before merging.
- Automate objective rules at the earliest useful boundary.
- Make local and CI commands consistent.
- Keep failures actionable and easy to reproduce.
- Remove prose duplicated by self-explanatory tooling.

## Common Mistakes

- Do not duplicate a linter rule in a long prompt unless the agent needs context for fixing it.
- Do not automate subjective design judgment with brittle regexes.
- Do not add a CI-only check engineers cannot run locally.
- Do not accept flaky checks as standards.
- Do not weaken a check because generated code fails it.

## Exercise

1. Find one objective “must” or “never” rule in project documentation.
2. Collect one conforming and one violating example.
3. Choose test, type, linter, formatter, hook, or CI enforcement.
4. Implement the smallest check and run it on both examples.
5. Add it to the normal local and CI workflow.
6. Shorten the prose to rationale and remediation.

Complete the exercise when:

- One objective standard produces a reliable pass/fail signal.
- Engineers and agents can reproduce the same result locally.
