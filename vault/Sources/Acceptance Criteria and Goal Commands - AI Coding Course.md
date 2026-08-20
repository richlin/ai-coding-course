---
title: Acceptance Criteria and Goal Commands
author: AI Coding Course
type: essay
url:
file: 04-specify-and-plan-work/acceptance-criteria.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Acceptance Criteria and Goal Commands — AI Coding Course

## Summary
Defines acceptance criteria as observable conditions that must hold when work is complete, and a goal command as the executable check (test/build/lint) that verifies one. Argues the agent needs a stopping condition stronger than "the code looks finished," and gives concrete do/don't examples for CSV export.

## Key takeaways
- Pair each criterion with the cheapest check that could disprove it — not the most thorough check available.
- Cover happy path, boundary, authorization, and failure behavior — omitting negative cases for permissions/untrusted input is a named common mistake.
- Criteria describe observable behavior, not private implementation — "works correctly" fails because it doesn't define rows, authorization, format, or failure behavior.
- Criteria that only restate implementation tasks aren't acceptance criteria; a criterion two reviewers would evaluate identically is the bar.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Acceptance Checks]]
- [[Task Specification]]

## Notable quotes
> "Export works correctly" is not acceptable because it does not define rows, authorization, format, or failure behavior."

## My reaction
[OPEN] — not yet reviewed by Lin.
