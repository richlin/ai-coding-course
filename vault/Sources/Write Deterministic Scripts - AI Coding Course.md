---
title: Write Deterministic Scripts
author: AI Coding Course
type: essay
url:
file: 02-configure-agent-harness/write-deterministic-scripts.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Write Deterministic Scripts — AI Coding Course

## Summary
Argues for moving mechanical, judgment-free operations out of prose instructions and into scripts with a defined contract (inputs, output, exit status, side effects), reused by commands, hooks, and CI rather than reimplemented per caller.

## Key takeaways
- Use a script when correctness doesn't require judgment — formatting, schema generation, link validation, focused test selection.
- A useful script has a stable contract: accepted inputs, what it prints, what exit codes mean, whether it touches state outside the working tree.
- Scripts should be safe to rerun (same inputs → same result, no hidden partial writes).
- Reuse one implementation across the review command, the pre-commit hook, and CI instead of maintaining parallel copies of the same rule.
- Deterministic ≠ safe to auto-trigger for consequential actions (production data, publishing, external systems) — those still need an explicit approval boundary.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Deterministic Scripts]]
- [[Hooks]]
- [[Acceptance Checks]]

## Notable quotes
> "Deterministic behavior does not make a consequential action safe to trigger automatically."

## My reaction
[OPEN] — not yet reviewed by Lin.
