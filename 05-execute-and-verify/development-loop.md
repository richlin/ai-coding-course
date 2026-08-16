# Research, Plan, Implement, Verify

## What It Means

- **Research:** Understand the requirement, code path, constraints, and existing patterns.
- **Plan:** Choose a small change and the check that can disprove it.
- **Implement:** Make the smallest complete edit that tests the plan.
- **Verify:** Run the focused check and update the plan from the result.

## Why It Matters

- Separating these stages prevents premature editing and unchecked implementation.
- Repeating the loop keeps the agent grounded in current evidence.

## Concrete Example

- **Research:** Reproduce a CSV export where customer name `=2+2` is emitted as an executable formula and find the serialization helper.
- **Plan:** Add one failing helper test for dangerous prefixes, then escape cells without changing ordinary values.
- **Implement:** Make the smallest helper change needed for the test.
- **Verify:** Run the helper test, export endpoint test, type check, and a manual download opened as plain text.
- If the test reveals a library already handles quoting but not formula prefixes, update the hypothesis rather than replacing the library.

## Best Practices

- Stop researching once you can state a falsifiable local hypothesis.
- Put verification in the plan before editing.
- Let failed checks change your understanding instead of merely triggering more code.
- Define the cheapest discriminating check before editing.
- Keep one active hypothesis visible.
- Separate research findings from implementation decisions.
- Preserve evidence from failed as well as passing checks.

## Common Mistakes

- Do not perform all research, all edits, and all testing as three large disconnected phases.
- Do not keep researching after one small experiment can answer the question.
- Do not edit while the controlling code path is still ambiguous.
- Do not add unrelated cleanup during the implementation step.
- Do not broaden tests before the focused check passes.

## Try It

1. Choose a reproducible defect with a focused test surface.
2. Record reproduction, suspected owner, and one falsifiable hypothesis.
3. Name the first check and its expected failure.
4. Make one small implementation change.
5. Run the check and update the hypothesis from actual output.
6. Repeat until the behavior passes, then run broader relevant checks.

## Expected Result

- A short loop log connecting every edit to evidence.
- The final change solves the reproduced defect without unrelated modifications.
