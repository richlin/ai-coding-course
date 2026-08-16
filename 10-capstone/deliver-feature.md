# Research, Plan, Implement, and Verify

## What It Means

- Trace the controlling code path and confirm existing project patterns.
- Decompose the feature into small, verifiable increments.
- Implement each increment and run the focused check immediately afterward.
- Finish with broader required checks and direct behavior validation.

## Why It Matters

- This is the central demonstration that the earlier concepts work together.
- Incremental evidence keeps the implementation aligned with the specification.

## Concrete Example

- **Increment 1:** Add service-level account-deletion tests for authorization, retention, and idempotency.
- **Increment 2:** Implement service behavior and session revocation; run focused tests.
- **Increment 3:** Add the authenticated endpoint and route tests.
- **Increment 4:** Add settings confirmation UI and verify end to end.
- Broader checks and final diff review happen only after focused evidence passes.

## Best Practices

- Record the hypothesis and verification for each increment.
- Keep unrelated cleanup outside the capstone scope.
- Update the plan when evidence changes an assumption.
- Inspect the final diff against every acceptance criterion.
- Record hypothesis and expected check for each increment.
- Keep the repository working after each step.
- Address high-risk boundaries before cosmetic UI.
- Preserve commands and results for review.

## Common Mistakes

- Do not ask the agent to implement the entire spec before the first verification.
- Do not mix account deletion with unrelated account-settings cleanup.
- Do not change tests merely to fit generated behavior.
- Do not skip direct runtime checks after unit success.
- Do not claim completion while a criterion lacks evidence.

## Try It

1. Research the controlling service, routes, data relationships, and neighboring tests.
2. Write an ordered increment plan with one behavior, check, and rollback per step.
3. Implement the highest-risk small increment first.
4. Run its focused check immediately and record output.
5. Continue one increment at a time, updating the plan from evidence.
6. Run required broad checks, exercise the user flow, and map results to every criterion.
7. Inspect the final diff for scope, security, and unintended data changes.

## Expected Result

- A complete feature delivered through at least two independently verified increments.
- An evidence table mapping every acceptance criterion to a command or observation.
