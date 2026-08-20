# Write and Test a Skill

## What It Means

- A skill packages a recurring workflow so an agent can recognize and follow it consistently.
- It usually defines when to activate, what evidence to gather, which steps to follow, and how to verify completion.
- Testing checks whether the skill changes behavior on representative tasks.

## Why It Matters

- A written procedure reduces reinvention and spreads team practices.
- Untested instructions may sound good while adding no reliable behavior.

## Concrete Example

- An `export-security-review` skill triggers on CSV, spreadsheet, or bulk-data export changes.
- It inspects authorization, tenant isolation, formula injection, sensitive fields, limits, logging, and tests.
- Its output is a severity-ordered finding list with evidence and verification gaps.
- It should not trigger for internal JSON serialization with no user download.

## Best Practices

- Start from a workflow the team has repeated successfully.
- Write specific triggers and observable outputs.
- Include stopping conditions and verification.
- Test normal, edge, and non-triggering examples.
- Start from a workflow already performed successfully several times.
- Use clear trigger and non-trigger descriptions.
- Require concrete artifacts and evidence.
- Version skills with the project when they encode project practice.

## Common Mistakes

- Do not build a broad “do everything well” skill with vague steps.
- Do not omit non-trigger examples.
- Do not encode commands that differ across repositories without discovery.
- Do not trust a skill because its prose sounds thorough.
- Do not let a skill silently change code when its role is review.

## Exercise

1. Choose a workflow repeated at least three times.
2. Write trigger, non-trigger, inputs, ordered steps, output, stop conditions, and verification.
3. Prepare one normal case, one edge case, and one unrelated case.
4. Run the skill on all three without manual hints.
5. Compare output with a human-created rubric.
6. Revise only instructions tied to observed failures.

Complete the exercise when:

- A focused skill that activates correctly and produces a reviewable artifact.
- Test evidence covers normal, edge, and non-triggering behavior.
