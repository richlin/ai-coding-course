---
title: Acceptance Checks
tags: [type/concept]
related: [[Non-Determinism]], [[Six Harness Components]], [[Harness Engineering]]
---

# Acceptance Checks

Deterministic checks placed at the end of agent execution paths that define acceptable output regardless of which implementation the agent chose.

```
same request → different implementations → same acceptance checks
```

## Why they're necessary

A precise prompt helps the agent aim at the right target. A prompt is not a test. "Reset after ten minutes" can still produce an off-by-one error or a counter that resets only when the process restarts.

Acceptance checks make the required outcome repeatable across the distribution of possible implementations.

## Types by mechanism

| Check type | What it catches |
|---|---|
| Executable tests | Behavioral requirements (advance fake clock 10min → assert login allowed) |
| Types / linters | Structural rules (forbidden import, invalid return value) |
| Human review | Design costs, readability, side effects that are hard to encode |
| Plain-language acceptance criteria | Shared understanding of what tests are protecting |

## Practical rule

Use the cheapest check that can observe the failure. Don't write a test for something a type can catch. Don't ask a model to think longer about something a deterministic check can settle. [[Deterministic Scripts]] and [[Hooks]] are the two mechanisms that most often carry out that cheapest check without needing model judgment at all. Source: [[Write Deterministic Scripts - AI Coding Course]], [[Use Hooks for Automatic Checks - AI Coding Course]]

## Related development

[[Executable Standards]] is the same idea applied to project-wide rules rather than one feature's criteria. [[Verification Hierarchy]] orders these checks — runtime, tests, types, lint, build, diff review — from cheapest discriminating signal to broadest confidence. [[Test-Driven Development Cycle]] is the practice of writing the check before the implementation it verifies. Source: [[Enforce Coding Standards with Executable Checks - AI Coding Course]], [[Tests Types Linting Builds and Runtime Checks - AI Coding Course]], [[Test-Driven Development - AI Coding Course]]

## Writing criteria that are actually checkable

An acceptance criterion should be specific enough that two reviewers would evaluate it the same way — "export works correctly" fails this because it doesn't define rows, authorization, format, or failure behavior. Cover happy path, boundary, authorization, and failure cases; a criterion that only restates the implementation task isn't an acceptance criterion. Each criterion pairs with a **goal command** — the executable check (focused test, build, lint) that can actually disprove it. Source: [[Acceptance Criteria and Goal Commands - AI Coding Course]]

Source: [[Non-Determinism - AI Coding Course]]
