---
title: "Tests, Types, Linting, Builds, and Runtime Checks"
author: AI Coding Course
type: essay
url:
file: 05-implement-and-verify/verification-hierarchy.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Tests, Types, Linting, Builds, and Runtime Checks — AI Coding Course

## Summary
Lays out a hierarchy of verification layers — runtime/behavior checks, tests, type checks, linting, builds, and diff review — each catching a different class of failure, so passing a weak check (a successful build) is never proof of a stronger claim (the feature behaves correctly for the user). The practical move is choosing checks by changed behavior and risk, ordered from cheapest discriminating signal to broadest confidence.

## Key takeaways
- Run the narrowest behavior-specific check first, then expand to broader tests, types, lint, and build as risk increases — a unit test on the escaping helper before an endpoint test on the whole export flow.
- Diff review catches what automated checks structurally cannot: unintended scope, unrelated formatting changes, or an authorization check that quietly went missing.
- Do not treat a successful build or lint run as proof the feature works, and do not run only the broad suite and lose the causal signal a focused test provides.
- Do not accept passing tests that never observed the original failure — a test that was always green never demonstrated it could catch the defect.
- Include negative and security behavior in the check inventory where applicable, and inspect the diff even when every automated check passes.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Verification Hierarchy]]
- [[Acceptance Checks]]

## Notable quotes
> "Passing a weak check does not prove stronger user behavior."

## My reaction
[OPEN] — not yet reviewed by Lin.
