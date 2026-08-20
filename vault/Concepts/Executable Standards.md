---
title: Executable Standards
tags: [type/concept]
related: [[Acceptance Checks]], [[Deterministic Scripts]], [[Verification Hierarchy]]
---

# Executable Standards

Coding rules enforced by tests, linters, type checkers, formatters, build tools, or CI — as opposed to rules that live only in prose. Prose explains judgment and intent; executable standards enforce objective, repeatable conditions, and give agents and humans the same pass/fail completion signal (a goal command).

## Why prose alone fails with agents

Agents can forget written standards, especially in long sessions where the instruction was set early and never resurfaces. A rule that only exists as a sentence in project documentation has no mechanism forcing it back into view at the moment it matters. An automated check applies the same way regardless of which model, tool, or contributor produced the change.

## What to automate vs. what to keep as prose

Automate rules that can be detected reliably — a security-sensitive escaping rule, a forbidden import, a formatting convention. Keep subjective design judgment (naming, architecture trade-offs, readability) in concise project instructions and human review rubrics — attempting to encode judgment calls as brittle regexes produces false confidence, not enforcement.

## Practical rules

- Keep local and CI commands consistent — a check that only runs in CI can't be reproduced by whoever hits the failure.
- Once the check exists, prose can shrink to rationale and remediation instead of restating a rule the tooling already enforces.
- Do not weaken a check because generated code fails it, and do not accept flaky checks as standards — both quietly convert a real signal into noise.

Source: [[Enforce Coding Standards with Executable Checks - AI Coding Course]]
