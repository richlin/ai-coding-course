---
title: "Test-Driven Development"
author: AI Coding Course
type: essay
url:
file: 05-implement-and-verify/test-driven-development.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Test-Driven Development — AI Coding Course

## Summary
Presents the red-green-refactor cycle — write a failing test, make it pass with the smallest implementation, then simplify while staying green — as a way to give an agent a precise, falsifiable target instead of an open-ended implementation request. The failing test first proves the test can actually detect the missing behavior, which a test written after the fact cannot prove.

## Key takeaways
- Observe the red failure for the expected reason before writing any implementation — a fixture bug masquerading as a failing test proves nothing.
- Write only enough code to pass, then improve clarity while keeping all tests green; refactor is a distinct, lower-risk step from making the test pass.
- Test public behavior and meaningful boundaries, not private implementation details that are free to change.
- Do not write tests after implementation and assume they would have caught the original defect — that assumption is unverifiable after the fact.
- Do not change the test merely to accept incorrect implementation output; the test is the fixed point, not the moving target.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Test-Driven Development Cycle]]
- [[Acceptance Checks]]

## Notable quotes
> "The failing test proves the test can detect the missing or broken behavior."

## My reaction
[OPEN] — not yet reviewed by Lin.
