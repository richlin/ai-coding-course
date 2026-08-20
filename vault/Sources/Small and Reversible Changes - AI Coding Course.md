---
title: "Small and Reversible Changes"
author: AI Coding Course
type: essay
url:
file: 05-implement-and-verify/reversible-changes.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Small and Reversible Changes — AI Coding Course

## Summary
Defines a small change as addressing one logical behavior reviewable on its own, and a reversible change as one undoable without damaging unrelated work or data. Small diffs make agent mistakes easier to isolate; reversibility bounds the cost of a wrong assumption — the two properties compound, since a large diff is not made reversible merely because Git can technically revert it.

## Key takeaways
- Split work into increments that each have a focused purpose, visible evidence, and can be reverted independently — e.g., failing tests, then an escaping helper, then wiring the helper into the serializer, as three separate increments.
- Separate refactoring from new behavior; mixing them in one diff makes the intent-vs-noise ratio of a review much worse.
- Inspect the diff before treating an increment as complete — "the tests pass" is not the same claim as "the diff only contains what I intended."
- Prefer additive migration stages before removing old behavior; commit or checkpoint only after a verified increment, never a failing or unreviewed one.
- Plan rollback before deploying stateful or destructive changes — reversibility purchased after the fact is much more expensive than reversibility designed in.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Small Reversible Increments]]
- [[Task Decomposition]]

## Notable quotes
> "A reversible change can be undone without damaging unrelated work or data."

## My reaction
[OPEN] — not yet reviewed by Lin.
