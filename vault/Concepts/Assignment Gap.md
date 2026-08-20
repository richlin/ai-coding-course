---
title: Assignment Gap
tags: [type/concept]
related: [[Compliance Bias]], [[Active Partnership]], [[Handoff Document]]
---

# Assignment Gap

The distance between the full task as the author holds it in their head and the task actually stated in the prompt.

## Mechanism

A prompt like "fix this" or "research context windows" names a topic without stating the observed problem, the decision already made, the boundaries that apply, or the evidence that would prove success. The author often carries those details unconsciously and reads them back into their own compressed words. The agent receives only the fragment and fills the gap with plausible guesses — producing fluent, polished work that may target the wrong assignment. Fluency is not evidence of alignment.

## Closing the gap

A minimum viable prompt states:
- the observed problem or desired outcome;
- context and decisions the agent cannot discover on its own;
- constraints that bound acceptable solutions; and
- observable evidence that would demonstrate success.

This gives the agent a destination without prescribing a turn-by-turn route — the target question is "did I make success and the important boundaries observable?", not "did I specify every step?".

## Related concepts
- [[Compliance Bias]] — a wide assignment gap is exactly the space in which an agent's guess can quietly become the accepted requirement.
- [[Active Partnership]] — one way to close the gap collaboratively: the agent surfaces material questions instead of silently guessing.
- [[Handoff Document]] — the session-boundary analogue: what the next agent would guess wrong if a fact isn't written down.
- [[Starting Context]] — the practical brief that closes the gap at the start of a task: enough for the first decision, without a repository dump.
- [[Task Boundary]] — a structured, four-part version of closing this gap (intent, assumptions, constraints, non-goals) for work substantial enough to need a written specification.

## Sources
- [[Write an Effective Task Prompt - AI Coding Course]]
