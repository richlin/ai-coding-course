---
title: Test-Driven Development Cycle
tags: [type/concept]
related: [[Acceptance Checks]], [[Debugging Loop]], [[Verification Hierarchy]]
---

# Test-Driven Development Cycle

The red-green-refactor cycle: write a failing test, make it pass with the smallest implementation, then simplify while keeping it green. The failing test is not a formality — observing it fail *for the expected reason* is what proves the test can actually detect the missing or broken behavior, something a test written after the implementation can never prove.

## Why red comes first

A test added after the implementation and never run against the broken state is an assumption, not evidence, that it would have caught the original defect. Red-first turns "this test should catch that bug" into an observed fact.

## The three steps

1. **Red** — write one test naming the input and the expected outcome; run it and confirm it fails for the intended reason, not because of a broken fixture.
2. **Green** — write only enough code to pass; resist expanding scope before the focused test is green.
3. **Refactor** — improve clarity only if it improves clarity, then rerun the same test and the relevant suite to confirm nothing regressed.

## What to test

Public behavior and meaningful boundaries — not private implementation details that are free to change without altering behavior. Add broader (e.g., endpoint-level) coverage only after the narrower unit behavior is established, which keeps the causal signal of each test level distinct — see [[Verification Hierarchy]].

## Common mistakes

Writing many tests before making the first one pass, which defeats the tight red-green feedback loop. Changing the test to accept incorrect implementation output — the test is meant to be the fixed point the implementation converges toward, not a variable that moves to match whatever the agent produced.

Source: [[Test-Driven Development - AI Coding Course]]
