---
title: Task Decomposition
tags: [type/concept]
related: [[Task Specification]], [[Research Plan Implement Verify Loop]], [[Six Harness Components]], [[Task Size Signals]], [[Verifiable Ticket]], [[Subagent Delegation]]
---

# Task Decomposition

Dividing a large outcome into small, ordered, independently verifiable tasks, with dependencies determining what must happen first versus what can run in parallel. Plan mode is the discipline of doing this investigation and sequencing *before* touching code.

## Why smaller tasks help

Smaller tasks reduce context load per session (see [[Smart Zone vs Dumb Zone]]), reduce review difficulty, and reduce rollback cost if one task turns out wrong.

## What makes a good split

Vertical slices that each produce working, reviewable behavior — not a split solely by layer (frontend/backend/tests) where no single task delivers behavior on its own. Every task gets acceptance criteria and a verification step. High-risk assumptions and shared contracts go early, because tasks that still depend on an undecided contract can't safely run in parallel. Likely files are named as navigation help, not as an inflexible mandate that blocks a better path found during implementation.

## Common failure

Planning speculative architecture for requirements that don't exist yet, instead of stopping once the next safe increment and its check are clear. Tickets titled "implement feature" that hide every real decision inside one opaque unit. A decomposition is good when another engineer can pick the next unblocked task without needing the original conversation.

## Related concepts
- [[Task Specification]] — decomposition assumes the boundary is already settled; it sequences the *how*, not the *what must remain true*.
- [[Research Plan Implement Verify Loop]] — each decomposed task is typically small enough to run through one full loop.
- [[Small Reversible Increments]] — decomposition sequences the work; this is the property each resulting change should still have on its own, regardless of how the split was made.
- [[Task Size Signals]] — the signals that trigger a decomposition decision in the first place.
- [[Verifiable Ticket]] — the unit a good decomposition should produce: a vertical, independently checkable slice.
- [[Subagent Delegation]] — once tasks are decomposed, this is how independent ones get executed in parallel.

## Sources
- [[Plan Mode and Task Decomposition - AI Coding Course]]
- [[Recognizing Work That Exceeds One Context Window - AI Coding Course]]
- [[Splitting Features into Verifiable Tickets - AI Coding Course]]
