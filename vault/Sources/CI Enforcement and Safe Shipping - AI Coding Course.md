---
title: "CI Enforcement and Safe Shipping"
author: AI Coding Course
type: essay
url:
file: 07-design-the-team-harness/ci-and-shipping.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# CI Enforcement and Safe Shipping — AI Coding Course

## Summary
Argues that agent-generated code must clear the same delivery bar as human-written code — shared CI checks that can't be skipped or reconfigured locally — and that safe shipping (review, staged rollout, monitoring, rollback) is what limits production risk after merge, since production behavior can surface failures pre-merge tests never reproduce.

## Key takeaways
- Run required tests, types, linting, builds, and security checks in CI rather than trusting local prompts, which are easy to skip or configure differently per session.
- Use feature flags or staged rollout to separate deployment from release, and define rollback and post-release signals before deployment, not after.
- Keep required local and CI commands aligned, and make checks risk-based and non-flaky rather than a fixed checklist run identically everywhere.
- Do not weaken CI to merge plausible-looking agent output more quickly, and do not deploy irreversible schema changes ahead of the backward-compatible code that reads them.
- Do not call deployment complete before observing runtime signals, and do not rely on the agent's own summary as release approval.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Safe Shipping Pipeline]]

## Notable quotes
> "Production behavior can reveal failures that pre-merge tests cannot reproduce."

## My reaction
[OPEN] — not yet reviewed by Lin.
