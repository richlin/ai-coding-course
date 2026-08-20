---
title: Reasoning Effort
author: AI Coding Course
type: essay
url:
file: 01-ai-coding-system/effort.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Reasoning Effort — AI Coding Course

## Summary
Distinguishes reasoning effort (how much internal reasoning the selected model performs per request) from model selection (which model is used). Effort is not an intelligence upgrade; it is time at the whiteboard. The useful setting is the lowest effort that produces reliable work for the task — not the highest available.

## Key takeaways
- Effort and model selection are independent controls; effort adjusts internal reasoning within the chosen model.
- Hidden reasoning tokens count as output usage (provider-specific) but don't appear in the visible answer.
- Effort is not the same as agent iteration count — that is controlled by the harness.
- Low effort: mechanical tasks (search, format, isolated edit). Medium: ordinary coding. High: ambiguous bugs, cross-file behavior, security, migrations. Very high: genuinely expensive mistakes only.
- Effort won't help if the failure is a missing file, a broken tool, a vague requirement, or irrelevant context.
- Think of effort as "time at the whiteboard, not an intelligence upgrade."

## Open questions it raises
- How do providers differ in how they expose and bill for reasoning effort controls?

## Concepts touched
- [[Reasoning Effort]]
- [[Total Cost of AI Development]]
- [[Model vs Harness]]

## Notable quotes
> "Think of effort as time at the whiteboard, not as an intelligence upgrade. More time helps when the problem rewards careful reasoning. It does not teach the model facts it never learned, reveal files it was never shown, grant missing permissions, or repair a vague requirement." (Effort Changes Latency)

## My reaction
The whiteboard analogy is the most memorable framing in the course for this concept. The failure-mode taxonomy (missing file vs. overlooked constraint vs. wrong solution) is practically useful for deciding when to escalate effort vs. fix the environment.
