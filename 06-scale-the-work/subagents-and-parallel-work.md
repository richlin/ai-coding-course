# Subagents and Parallel Work

## What It Means

- A subagent receives a bounded task from a coordinating agent or human.
- Parallel work runs independent tasks at the same time.
- Useful subagent roles include focused research, isolated implementation, test creation, and independent review.

## Why It Matters

- Isolation protects the main context from detailed exploration.
- Parallelism reduces elapsed time only when tasks do not block or overwrite one another.

## Concrete Example

- A research subagent compares official provider semantics and returns a cited recommendation without editing.
- A backend agent implements one accepted contract in a worktree.
- A frontend agent implements against the same checked-in contract and mock.
- A fresh reviewer inspects both; the integration owner combines and verifies the full flow.

## Best Practices

- Define each subagent's scope, inputs, expected artifact, and verification.
- Give shared facts through durable contracts or files.
- Use separate branches or worktrees for simultaneous edits.
- Keep final integration and acceptance with a named owner.
- Delegate artifacts, not vague help.
- Isolate write work with branches or worktrees.
- Give every agent a source of truth and non-goals.
- Require status, evidence, and unresolved questions in returns.

## Common Mistakes

- Do not delegate an ambiguous task and expect subagents to resolve product or architecture conflicts independently.
- Do not let agents edit the same files concurrently.
- Do not accept summaries without inspecting artifacts.
- Do not parallelize dependent tasks for the appearance of speed.
- Do not lose integration ownership among several agents.

## Exercise

1. Choose a feature with research, implementation, and review needs.
2. Define one bounded assignment per role with inputs, non-goals, output, and verification.
3. Mark sequential and parallel relationships.
4. Create isolated workspaces for simultaneous edits.
5. Run or simulate the assignments and collect artifacts.
6. Have the integration owner inspect and combine results.

Complete the exercise when:

- Delegation briefs that produce compatible, reviewable artifacts.
- Parallelism reduces elapsed time without conflicting edits or decisions.
