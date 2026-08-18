# Integration Checkpoints

## What It Means

- An integration checkpoint combines completed work and verifies the system as a whole.
- It checks contracts, migrations, shared state, end-to-end behavior, and unresolved assumptions.
- Checkpoints occur throughout delivery, not only before release.

## Why It Matters

- Independently correct changes can fail when combined.
- Frequent integration detects incompatibility while each change is still understandable.

## Concrete Example

- **Checkpoint 1:** Contract and migration defaults agreed; schema tests pass.
- **Checkpoint 2:** Email preference endpoint and settings control work together in a test environment.
- **Checkpoint 3:** Push and email channels honor defaults; migrations, end-to-end tests, metrics, and rollback are ready.
- A failure at Checkpoint 2 is fixed before more channels multiply the inconsistency.

## Best Practices

- Integrate after a small group of related tickets.
- Run contract, integration, and end-to-end checks appropriate to the risk.
- Review combined behavior and diff scope with the integration owner.
- Record failures as new evidence, not as pressure to bypass checks.
- Define checkpoint criteria before parallel work starts.
- Integrate the highest-risk contract early.
- Use production-like data and environment where risk warrants it.
- Keep checkpoint owners and evidence visible in the tracker.

## Common Mistakes

- Do not wait for every parallel task to finish before attempting the first integration.
- Do not define checkpoints as meetings without pass/fail evidence.
- Do not test only each component in isolation.
- Do not continue accumulating changes after a failed checkpoint.
- Do not omit migration and rollback behavior from integration.

## Exercise

1. Choose a decomposed feature with at least two parallel tickets.
2. Place checkpoints after shared contract, first end-to-end slice, and release readiness.
3. Add pass criteria, commands, runtime observations, owner, and failure response.
4. Run the earliest checkpoint as soon as prerequisites finish.
5. Record evidence and block dependent work if it fails.

Complete the exercise when:

- Three evidence-based checkpoints connected to dependency boundaries.
- Integration failures surface before all parallel work is complete.
