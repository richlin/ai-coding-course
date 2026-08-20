---
title: Verification Hierarchy
tags: [type/concept]
related: [[Acceptance Checks]], [[Test-Driven Development Cycle]], [[Executable Standards]], [[Safe Shipping Pipeline]]
---

# Verification Hierarchy

Verification layers — runtime/behavior checks, tests, type checks, linting, builds, and diff review — each catch a different class of failure. Passing a weak check is never proof of a stronger claim: a successful build proves the project produces its artifact, nothing about whether the feature behaves correctly for a user.

## The layers and what each one catches

| Layer | What it proves | What it can't prove |
|---|---|---|
| Runtime/behavior check | The user gets the intended outcome | Coverage of untested paths |
| Tests | Selected behavior and failure cases hold | Behavior no test encodes |
| Type checks | Values/interfaces are compatible | Runtime logic correctness |
| Linting | Selected style/correctness rules hold | Semantic correctness |
| Build | The project can produce its artifact | The artifact behaves correctly |
| Diff review | Scope matches intent; nothing unrelated slipped in | Anything a human reviewer misses |

## The ordering principle

Run the narrowest, cheapest, most behavior-specific check first — it gives the clearest causal signal for the least cost. Expand to broader tests, types, lint, and build as risk increases. Choose the set of checks based on changed behavior and risk, not a fixed checklist run identically on every change.

## Diff review is not redundant with automated checks

Diff review catches what automated checks structurally cannot: unintended scope creep, unrelated formatting changes, or an authorization check that quietly disappeared — none of which necessarily breaks a test, a type, or a build. Inspecting the diff even when every automated check passes is what catches a suspicious change that "technically" passes everything.

## Common mistakes

Treating a passing build or lint run as proof the feature works. Running only the broad suite and losing the causal signal a focused test provided. Accepting a test that passed without ever having observed the original failure — a test that was always green never demonstrated it could catch the defect (see [[Test-Driven Development Cycle]]).

## Related concepts
- [[Safe Shipping Pipeline]] — where these layers get enforced as a shared, non-skippable CI gate, plus the release-time layers (staged rollout, rollback) this hierarchy doesn't cover on its own.

Source: [[Tests Types Linting Builds and Runtime Checks - AI Coding Course]]
