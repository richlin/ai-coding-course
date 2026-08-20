---
title: The 80% Problem
tags: [type/concept]
related: [[Total Cost of AI Development]], [[Implementation vs Evaluation Task]], [[Lifecycle Compression]]
---

# The 80% Problem

Agents reach initial working functionality quickly, but the remaining fraction — edge cases and system-integration seams — resists the same speed.

## Mechanism

Initial functionality is usually well-represented in training data and requires context the agent can gather locally (the function signature, a nearby example). Edge cases and integration seams require context that is scattered across the system, undocumented, or only known to people outside the immediate task — the kind of information a harness has to go out of its way to supply. Without it, the agent is guessing at the last mile.

## Consequence

The visible progress curve (a demo works fast) is a poor predictor of remaining effort. The last 20% is where [[Acceptance Checks]] and human review earn their cost, and where [[Total Cost of AI Development]]'s "consequence of wrong answers" term concentrates.

## Open questions it raises
- How do teams close this gap systematically rather than case-by-case? [OPEN]

## Sources
- [[The New Software Lifecycle - Addy Osmani]]
