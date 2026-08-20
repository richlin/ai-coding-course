---
title: Task Size Signals
tags: [type/concept]
related: [[Task Decomposition]], [[Smart Zone vs Dumb Zone]], [[Context Window]]
---

# Task Size Signals

The observable signals that a task exceeds what one context window can hold clearly — many independent subsystems, unclear dependencies, repeated compaction, and changes that can't be reviewed together as one coherent diff. Task size is a claim about cognitive and coordination load, not file count.

## Why it matters

Oversized tasks encourage forgotten constraints, overly broad edits, and weak verification. Deciding a task is too large early — before the session degrades — creates clear ownership and stopping points; deciding it late means the damage (a degraded session, an unreviewable diff) has already happened.

## What good sizing looks like

Estimating decision and integration boundaries, not tokens alone. Splitting when a task contains independently valuable outcomes. Isolating unknown or high-risk work as a separate research task before committing to full implementation. Keeping one named owner for the full outcome even after splitting.

## Common failure

Using file count as the only size measure — a one-file change with many lines can still fit one context. Waiting until context is already degraded to decide a task was too large. Splitting tightly coupled edits into artificial tickets. Calling a task small because the prompt describing it is short.

## Related concepts
- [[Task Decomposition]] — size signals are the trigger; decomposition is the response once a task is judged too large.
- [[Smart Zone vs Dumb Zone]] — repeated compaction and degrading review quality are the same phenomenon size signals are meant to catch before it happens.

## Sources
- [[Recognizing Work That Exceeds One Context Window - AI Coding Course]]
