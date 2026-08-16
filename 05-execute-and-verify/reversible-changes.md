# Small and Reversible Changes

## What It Means

- A small change addresses one logical behavior and can be reviewed independently.
- A reversible change can be undone without damaging unrelated work or data.
- Git commits, feature flags, additive changes, and rollback plans support reversibility.

## Why It Matters

- Small diffs make agent mistakes easier to detect and isolate.
- Reversibility limits the cost of experiments and incorrect assumptions.

## Concrete Example

- **Increment 1:** Add failing tests for `=`, `+`, `-`, and `@` CSV-cell prefixes.
- **Increment 2:** Add one escaping helper and make the tests pass.
- **Increment 3:** Apply the helper to the export serializer and run endpoint tests.
- Each increment has a focused purpose, visible evidence, and can be reverted without discarding the others.

## Best Practices

- Change one behavior at a time and verify it before expanding scope.
- Separate refactoring from new behavior.
- Inspect the diff before treating the increment as complete.
- Use extra safeguards for irreversible data or production changes.
- Commit or checkpoint after verified increments when the workflow allows.
- Prefer additive migration stages before removing old behavior.
- Keep generated changes separate from handwritten logic.
- Plan rollback before deploying stateful or destructive changes.

## Common Mistakes

- Do not combine a feature, dependency update, and unrelated cleanup in one agent task.
- Do not call a large diff reversible merely because Git can revert it.
- Do not mix refactoring with a behavioral fix.
- Do not remove old data or schema before new readers are compatible.
- Do not checkpoint failing or unreviewed work as known-good.

## Try It

1. Choose a task currently described as one large change.
2. Split it into at least three increments, each with one behavior or risk reduction.
3. Add a focused check and rollback action to every increment.
4. Order increments so the repository remains usable after each one.
5. Implement only the first increment and inspect its diff.
6. Revert it in a temporary branch or explain why the rollback is incomplete.

## Expected Result

- An increment plan with verification and rollback for every step.
- The first increment can be reviewed and reversed without affecting unrelated work.
