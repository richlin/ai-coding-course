---
title: Subagent Delegation
tags: [type/concept]
related: [[Task Decomposition]], [[Six Harness Components]], [[Dependency and Ownership Mapping]]
---

# Subagent Delegation

Giving a subagent a bounded task from a coordinating agent or human, so isolated work — focused research, isolated implementation, test creation, independent review — can run without expanding the coordinator's own context, and independent tasks can run in parallel when they don't block or overwrite one another.

## Why it matters

Isolation protects the main context from detailed exploration it doesn't need to hold. Parallelism only reduces elapsed time when the parallel tasks are genuinely independent — dependent tasks parallelized for the appearance of speed just create conflicts to resolve later.

## What good delegation looks like

Each subagent gets a defined scope, inputs, expected artifact, and verification method — an artifact request, not vague help. Shared facts are given through durable contracts or files rather than assumed. Simultaneous edits are isolated with separate branches or worktrees. Final integration and acceptance stay with one named owner regardless of how many agents contributed.

## Common failure

Delegating an ambiguous task and expecting subagents to independently resolve product or architecture conflicts. Letting agents edit the same files concurrently. Accepting a subagent's summary without inspecting the actual artifact it produced. Losing integration ownership among several agents so no one actually combines and verifies the result.

## Related concepts
- [[Task Decomposition]] — decomposition produces the bounded tasks that subagents then execute.
- [[Dependency and Ownership Mapping]] — delegation without explicit ownership recreates the same coordination failures at agent scale.

## Sources
- [[Subagents and Parallel Work - AI Coding Course]]
