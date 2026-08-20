---
title: Model Selection
author: AI Coding Course
type: essay
url:
file: 01-ai-coding-system/model-selection.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Model Selection — AI Coding Course

## Summary
Explains the model tier tradeoff (lightweight / general / heavyweight) and the heuristics for choosing correctly. Adds the concept of switching models mid-task. The optimization target is the shortest dependable path to an accepted result — not the fastest first token or lowest token price.

## Key takeaways
- Haiku tier: search, extraction, formatting, isolated edits with narrow scope and cheap checks.
- Sonnet tier: general default — implement a clear requirement across a few files, run focused tests.
- Opus tier: ambiguous problems, cross-system changes, security-sensitive work, unfamiliar debugging.
- Deterministic tool: always prefer a formatter, compiler, or test runner when one can settle the question.
- A task needs a stronger model when it is ambiguous, cross-file, difficult to verify, or costly to get wrong.
- A bounded change with a good test suite is friendly to smaller models — the test provides objective feedback.
- Models can be switched mid-task; most effective when the handoff is concrete (a reviewed plan → mechanical execution).

## Open questions it raises
- When does the cost of rebuilding mental model context erase the savings from switching to a lighter model?

## Concepts touched
- [[Model vs Harness]]
- [[Total Cost of AI Development]]
- [[Time to Accepted Result]]

## Notable quotes
> "Choose the least expensive model that has been reliable on similar work. Optimize for the shortest dependable path to an accepted result, not the fastest first token." (Model Choice Changes Latency)

## My reaction
The "deterministic tool instead of a model" row in the tier table is the most under-used insight. Practitioners reach for model capability when a compiler or test runner would answer the question faster and more reliably.
