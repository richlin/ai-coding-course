---
title: "Research, Plan, Implement, Verify"
author: AI Coding Course
type: essay
url:
file: 04-specify-and-plan-work/development-loop.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Research, Plan, Implement, Verify — AI Coding Course

## Summary
Frames the practical operating cycle for a development task as four stages — research (understand requirement/code/constraints), plan (choose a small change and a check that could disprove it), implement (the smallest complete edit that tests the plan), verify (run the check, update the plan from the result) — as the concrete form of observe-decide-act-update.

## Key takeaways
- Stop researching once a falsifiable local hypothesis can be stated — not once everything about the area is understood.
- Put verification into the plan *before* editing, not after; define the cheapest discriminating check up front.
- A failed check should change the working hypothesis, not just trigger another round of code — e.g., discovering a library already handles quoting reshapes the plan instead of triggering a library swap.
- Keep one active hypothesis visible; separate research findings from implementation decisions so a wrong hypothesis doesn't get baked into the diff.
- Don't broaden tests before the focused check passes, and don't add unrelated cleanup during implementation.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Research Plan Implement Verify Loop]]
- [[Acceptance Checks]]
- [[Time to Accepted Result]]

## Notable quotes
> "Let failed checks change your understanding instead of merely triggering more code."

## My reaction
[OPEN] — not yet reviewed by Lin.
