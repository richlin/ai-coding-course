# Feeding Lessons Back into the Harness

## What It Means

- Continuous improvement converts observed outcomes into better specs, tests, rules, skills, tools, and memory.
- A retrospective separates one-time mistakes from recurring system weaknesses.
- Improvements should target the earliest point where a failure could have been prevented or detected.

## Why It Matters

- Repeatedly correcting the same agent mistake wastes review time.
- Harness improvements let the whole team benefit from one task's learning.

## Concrete Example

- Three notification changes miss tenant-isolation tests and reviewers catch them manually.
- Root cause: the feature template mentions authorization vaguely and no focused test helper exists.
- Improve the template with explicit tenant criteria and add a reusable authorization test fixture.
- Compare review findings on the next three changes; remove or revise the control if it does not help.

## Best Practices

- Review failures, near misses, costly retries, and unusually successful workflows.
- Prefer one small measurable control over many new instructions.
- Assign an owner and test the changed workflow.
- Remove controls that create noise without improving outcomes.
- Improve the earliest reliable prevention or detection point.
- Change one control at a time when evaluating impact.
- Assign owner and review date.
- Preserve examples of the failure the control addresses.

## Common Mistakes

- Do not turn every isolated mistake into another permanent rule.
- Do not blame an individual agent before inspecting the system.
- Do not add controls without baseline or success measure.
- Do not preserve ineffective controls because they appear rigorous.
- Do not optimize only failed tasks; study efficient successes too.

## Try It

1. Collect three recent tasks or one high-impact incident.
2. Identify repeated failure, first observable cause, and current missed detection point.
3. Choose one small test, rule, skill, tool, permission, or knowledge change.
4. Define owner, expected effect, metric, and review date.
5. Apply it to representative future tasks.
6. Keep, revise, or remove it based on evidence.

## Expected Result

- A closed improvement record from evidence to control to measured outcome.
- The harness becomes simpler or more reliable, not merely larger.
