---
title: Small Reversible Increments
tags: [type/concept]
related: [[Task Decomposition]], [[Debugging Loop]], [[Acceptance Checks]]
---

# Small Reversible Increments

A small change addresses one logical behavior and can be reviewed independently. A reversible change can be undone without damaging unrelated work or data. The two properties compound: small diffs make agent mistakes easier to isolate, and reversibility bounds the cost of a wrong assumption or experiment.

## Distinct from task decomposition

[[Task Decomposition]] is about sequencing *what* work happens before implementation starts. Small reversible increments is about a property each *individual* change should have regardless of how the overall task was split — even a well-decomposed task can still be implemented as one large, unreviewable, hard-to-undo diff.

## What makes an increment reversible

- Git commits, feature flags, additive changes, and explicit rollback plans are the mechanisms that carry reversibility.
- A large diff is not reversible merely because Git can technically revert it — reverting a diff that bundled three unrelated behaviors also undoes the two you wanted to keep.
- Prefer additive migration stages (new path works alongside old) before removing old behavior, so a rollback doesn't require reconstructing deleted state.
- Plan rollback *before* deploying stateful or destructive changes — designed-in reversibility is far cheaper than reversibility improvised after a bad deploy.

## Common mistakes

Combining a feature, a dependency update, and unrelated cleanup in one agent task. Mixing refactoring with a behavioral fix, which erases the signal of which part of the diff caused a regression. Checkpointing failing or unreviewed work as if it were known-good — that just moves the risk downstream instead of removing it.

Source: [[Small and Reversible Changes - AI Coding Course]]
