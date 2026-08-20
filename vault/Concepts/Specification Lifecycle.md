---
title: Specification Lifecycle
tags: [type/concept]
related: [[Task Specification]], [[Rerouting]], [[Handoff Document]]
---

# Specification Lifecycle

A spec is a living decision artifact while work is active — it has a lifecycle, not a fixed "done" state.

## The three states

- **Update** — when accepted requirements, constraints, or decisions change.
- **Retain** — when it explains durable behavior or an important tradeoff, even after the work ships.
- **Archive/discard** — when it's temporary, has been superseded, and is no longer useful.

## Why the distinction matters

A stale spec can mislead future agents *more* than having no spec at all — it looks authoritative while describing a plan that no longer holds. Durable rationale, in contrast, prevents a team from re-litigating a decision or accidentally reversing something deliberate.

## Practical discipline

Record *why* a meaningful requirement changed, not just what changed. Mark superseded documents clearly and link to the replacement rather than leaving two active specs for the same behavior. Don't update code while leaving acceptance criteria knowingly false — code and spec drift apart exactly where trust erodes fastest. After delivery, keep user-visible behavior and rationale; archive the temporary investigation notes that got there.

## Related concepts
- [[Rerouting]] — the event that most often forces a spec into its "update" state: new evidence invalidated the plan the spec described.
- [[Handoff Document]] — links to the current spec state rather than restating it; a handoff pointing at a superseded spec is a bug in the handoff, not the spec.

## Sources
- [[Updating Retaining or Discarding a Specification - AI Coding Course]]
