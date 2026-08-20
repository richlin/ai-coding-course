---
title: "Scaling Ground Rules and Specifications Across a Team"
author: AI Coding Course
type: essay
url:
file: 07-design-the-team-harness/ground-rules.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Scaling Ground Rules and Specifications Across a Team — AI Coding Course

## Summary
Extends the individual-engineer practice of writing project instructions ([[Write a Good AGENTS.md - AI Coding Course|the AGENTS.md introduction]]) to team scale, where instruction files need shared ownership, consistent scope, and enforceable boundaries. Draws a hard line between ground rules ("how we work here" — stable conventions and safety boundaries) and specifications ("what this task must achieve" — outcome and constraints for one change), arguing that collapsing the two makes both harder to maintain.

## Key takeaways
- Keep project rules concise and specific to the repository; put task-specific detail in specs or tickets instead of growing the rule file per task.
- Automate objective rules with tests, linters, hooks, or CI, and link the executable enforcement beside the prose rule that describes it.
- Define explicitly which instruction wins when user, project, and task scopes overlap — ambiguous precedence is itself a defect.
- Do not copy every past task instruction into permanent project rules, and do not place changing product requirements inside repository rules.
- Do not duplicate CI behavior with conflicting prose, and do not keep a rule that has no observable effect on agent behavior.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Team Ground Rules]]

## Notable quotes
> "Rules answer 'how we work here'; specs answer 'what this task must achieve.'"

## My reaction
[OPEN] — not yet reviewed by Lin.
