# Recognizing Work That Exceeds One Context Window

## What It Means

- A task is too large when one session cannot hold its goals, evidence, active decisions, and verification state clearly.
- Common signals include many independent subsystems, unclear dependencies, repeated compaction, and changes that cannot be reviewed together.
- Task size is about cognitive and coordination load, not only the number of files.

## Why It Matters

- Oversized tasks encourage forgotten constraints, broad edits, and weak verification.
- Early decomposition creates clear ownership and stopping points.

## Concrete Example

- “Add notification preferences” includes schema migration, API contract, authorization, email and push behavior, settings UI, migration defaults, tests, and rollout.
- It spans independent decisions and cannot be verified as one small change.
- Split it into a contract and default decision, one end-to-end email-preference slice, then additional channels and rollout.
- A one-file parser change with many lines may still fit one context; file count alone is not the signal.

## Best Practices

- Split work when it contains independently valuable outcomes.
- Isolate high-risk research before committing to a full implementation.
- Give each slice its own acceptance criteria and verification.
- Estimate decision and integration boundaries, not tokens alone.
- Isolate unknown or high-risk work as research tasks.
- Keep one named owner for the full outcome.
- Decompose before the session starts degrading.

## Common Mistakes

- Do not wait until the context is degraded before deciding the task is too large.
- Do not use file count as the only size measure.
- Do not split tightly coupled edits into artificial tickets.
- Do not delegate work while shared contracts remain undefined.
- Do not call a task small because the prompt is short.

## Try It

1. Choose a feature touching several behaviors or subsystems.
2. List decisions, contracts, migrations, user flows, risks, and verification layers.
3. Mark which items can finish independently.
4. Identify the largest coherent slice that fits one focused session.
5. Define a stop signal for further decomposition.

## Expected Result

- A size assessment based on cognitive and integration boundaries.
- A first independently verifiable slice with clear ownership.
