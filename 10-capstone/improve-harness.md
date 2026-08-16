# Improve the Project Harness

## What It Means

- Use the capstone retrospective to identify one durable improvement to the project workflow.
- The improvement may be a test, rule, skill, script, template, permission boundary, or knowledge artifact.
- The chosen change should address observed evidence from the capstone.

## Why It Matters

- Reliable teams learn from delivery instead of treating every agent session as isolated.
- One measured improvement is more useful than a large speculative harness redesign.

## Concrete Example

- Review discovers the agent initially omitted session revocation because the feature template asked about data but not active credentials.
- Add one explicit identity-lifecycle question to the template and a reusable test helper that asserts all sessions are invalidated.
- Test the revised harness on account deletion and password-reset examples.
- Measure whether future identity changes need fewer review corrections.

## Best Practices

- Identify where the largest confusion, retry, or risk occurred.
- Select the earliest practical prevention or detection point.
- Implement the smallest control and define how to evaluate it.
- Document ownership and remove any instruction it supersedes.
- Improve the earliest point that could prevent or detect the issue.
- Prefer one measurable change over a broad rewrite.
- Test triggering and non-triggering examples.
- Set a review date and removal condition.

## Common Mistakes

- Do not add a permanent rule for a one-time error without evidence it will recur.
- Do not improve the harness before identifying the actual cause.
- Do not duplicate an existing check in prose.
- Do not measure success by instruction length.
- Do not leave the new control ownerless.

## Try It

1. Review capstone retries, corrections, review findings, permission prompts, and context failures.
2. Select one recurring or high-impact issue and identify its earliest preventable point.
3. Choose one test, rule, template, skill, tool, permission, or knowledge improvement.
4. Define owner, expected behavior, normal case, edge case, non-trigger case, and success metric.
5. Implement and run those cases.
6. Record baseline, result, review date, and what old guidance it replaces.

## Expected Result

- One tested harness improvement directly tied to capstone evidence.
- A measurable evaluation plan prevents the harness from growing without proof.