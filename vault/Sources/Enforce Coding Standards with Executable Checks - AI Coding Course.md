---
title: "Enforce Coding Standards with Executable Checks"
author: AI Coding Course
type: essay
url:
file: 05-implement-and-verify/enforce-coding-standards.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Enforce Coding Standards with Executable Checks — AI Coding Course

## Summary
Argues that prose standards should be converted into executable checks — tests, linters, type checkers, formatters, or CI gates — wherever a rule is objective and repeatable, because agents forget written standards over long sessions while automated checks apply consistently regardless of who or what produced the change.

## Key takeaways
- A goal command gives agents and humans the same pass/fail completion signal, closing the gap between stated intent and enforced behavior.
- Automate rules that can be detected reliably; keep subjective design judgment in concise project instructions and human review rubrics instead of brittle regexes.
- Run focused checks during work and the full required checks before merging — local and CI commands should be the same commands.
- Once a check exists, prose can shrink to rationale and remediation instead of restating the rule itself.
- Do not weaken a check because generated code fails it, and do not accept flaky checks as standards — both erode the signal the check exists to provide.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Executable Standards]]
- [[Acceptance Checks]]

## Notable quotes
> "Prose explains judgment and intent; tools enforce objective, repeatable conditions."

## My reaction
[OPEN] — not yet reviewed by Lin.
