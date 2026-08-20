---
title: "Debugging and Recovery"
author: AI Coding Course
type: essay
url:
file: 05-implement-and-verify/debugging-and-recovery.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Debugging and Recovery — AI Coding Course

## Summary
Defines debugging as a five-step evidence chain — reproduce, localize, explain, fix, guard — and recovery as returning to a known-good state after a wrong edit or invalid assumption. The throughline is that evidence narrows causes while guesses only multiply them, so agents should not be allowed to stack speculative fixes against a symptom.

## Key takeaways
- Reproduce the smallest failing case before editing anything; localize by testing the helper directly (bypassing the UI) to rule out unrelated layers.
- Distinguish root cause from trigger and symptom — CSV quoting protects commas/quotes but does not stop spreadsheet formula injection, a different mechanism entirely.
- Change one variable at a time; explain *why* the fix addresses the observed cause, not just that the symptom disappeared.
- Add regression protection using realistic malicious inputs, then rerun the original reproduction before declaring recovery.
- Return to a known-good checkpoint after speculative edits rather than layering more changes on top of an unverified state.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Debugging Loop]]
- [[Small Reversible Increments]]

## Notable quotes
> "Evidence narrows the cause; guesses only create more possibilities."

## My reaction
[OPEN] — not yet reviewed by Lin.
