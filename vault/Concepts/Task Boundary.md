---
title: Task Boundary
tags: [type/concept]
related: [[Task Specification]], [[Assignment Gap]], [[Compliance Bias]]
---

# Task Boundary

A four-part framework for bounding what a task actually asks for, so an agent doesn't fill the gaps with its own guesses.

## The four parts

- **Intent** — the user or business outcome the work should produce. Name the user and the decision the outcome supports, not just the feature.
- **Assumptions** — beliefs treated as true until evidence confirms or rejects them. Surface uncertain ones explicitly so they get checked early, instead of hiding inside the requirement.
- **Constraints** — limits on acceptable solutions (compatibility, security, scope). Keep policy constraints distinct from mere technical preferences.
- **Non-goals** — what the task deliberately will not solve. Name the *specific* tempting adjacent behavior being excluded — "out of scope" without naming it doesn't actually constrain anything.

## Why it's needed

Agents fill gaps when requirements are ambiguous, and they often fill them differently from what the requester meant. A boundary this specific is enough to plan against while still leaving implementation choices open — it bounds the decision space without prescribing the design.

## Failure modes

Confusing an implementation preference with the actual outcome or constraint. Hiding an unresolved product decision inside an "assumption" instead of flagging it for a check. Letting a small feature expand into platform work because nothing named the adjacent behavior as out of scope.

## Verification

Ask a peer or fresh agent to name two plausible interpretations still allowed by the boundary as written. Revise only the interpretations that would actually cause incorrect work — not every conceivable ambiguity.

## Related concepts
- [[Task Specification]] — this framework is what fills a spec's context/goal/non-goals/constraints sections.
- [[Assignment Gap]] — this is the structured version of closing that gap: instead of an implicit shared understanding, each of the four parts is written down and checkable.

## Sources
- [[Intent Assumptions Constraints and Non-Goals - AI Coding Course]]
