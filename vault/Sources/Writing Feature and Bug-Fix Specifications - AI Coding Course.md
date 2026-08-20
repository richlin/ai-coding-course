---
title: Writing Feature and Bug-Fix Specifications
author: AI Coding Course
type: essay
url:
file: 04-specify-and-plan-work/writing-specifications.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Writing Feature and Bug-Fix Specifications — AI Coding Course

## Summary
The vault's central treatment of the task specification: a spec is a task contract (outcome, boundaries, constraints, examples, acceptance criteria) that keeps implementation freedom inside an agreed behavioral boundary, without prescribing an implementation the agent hasn't researched yet. Distinguishes a spec (what must remain true) from a plan (how this repository will be changed to make it true), and feature specs (start from a user problem, define new boundary) from bug-fix specs (start from reproducible incorrect behavior, require regression protection).

## Key takeaways
- "Same vague request → different inferred requirements → incompatible implementations; same specification → different valid designs → same accepted behavior." The goal isn't identical code, it's a shared behavioral boundary.
- A spec becomes enforceable, not just descriptive, only when its acceptance criteria point to tests, commands, or explicit manual checks — prose alone is a task contract, not an executable one.
- For bug fixes: record the observed defect and safe expected output before choosing the repair, so a specific fix ("prefix with apostrophe") doesn't get mistaken for the actual requirement ("`=2+2` must not execute as a formula").
- Match specification detail to the cost of being wrong: a small reversible edit may need only a task prompt with precise acceptance criteria; a cross-owner, hard-to-reverse, or multi-system change needs the fuller contract. Stop adding detail once an implementer can plan without inventing a product decision and a reviewer can reject out-of-boundary behavior.
- Verify a spec with a fresh agent/peer: if it invents user-visible behavior or limits, the spec is incomplete; if it picks a different internal design that still satisfies every criterion, the spec is appropriately flexible; if a criterion can't be checked by any test/command/inspection, it's an aspiration, not a stopping condition.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Task Specification]]
- [[Task Boundary]]
- [[Acceptance Checks]]
- [[Specification Lifecycle]]

## Notable quotes
> "The specification says what must remain true; the plan says how this repository will be changed to make it true."

## My reaction
[OPEN] — not yet reviewed by Lin.
