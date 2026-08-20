---
title: Cost
author: AI Coding Course
type: essay
url:
file: 01-ai-coding-system/cost.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Cost — AI Coding Course

## Summary
Argues that the provider token bill is only one component of the total cost of AI-assisted development. Time to accepted result — including retries, review, and the cost of being wrong — is the right optimization target. The cheapest model request is not always the cheapest path to a trustworthy result.

## Key takeaways
- Total cost = model tokens + engineer time + tool execution + retries + review + consequence of wrong answers.
- Time to accepted result (not time-to-first-token or latency per response) is the useful latency metric.
- The agentic loop is often the dominant cost: each failed pass consumes both tokens and human attention.
- Cost scales with consequence: a wrong authorization check costs far more than a wrong variable name.
- A practical default: capable general model + medium effort for ordinary work; route up/down based on evidence, not habit.
- Escalating model strength cannot fix a missing file, a broken tool, or an unstated requirement.

## Open questions it raises
- How do you measure "time to accepted result" consistently enough to use it for routing decisions?

## Concepts touched
- [[Total Cost of AI Development]]
- [[Time to Accepted Result]]
- [[Reasoning Effort]]
- [[Model vs Harness]]

## Notable quotes
> "The cheapest model request is not necessarily the cheapest way to finish a task. A low-cost model that needs repeated correction can consume more tokens and more engineering time than a stronger model that succeeds on the first pass." (Direct Model Cost)

> "The size of the diff is a poor proxy for risk. Renaming a hundred private variables may be cheap and reversible. Changing one boolean in an access-control path may deserve the most careful workflow available." (Include the Cost of Being Wrong)

## My reaction
The "loop is expensive" framing reframes cost optimization away from per-request token price toward end-to-end workflow design — a useful shift for practitioners who default to "use the cheapest model."
