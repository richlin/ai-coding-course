---
title: Starting Context
tags: [type/concept]
related: [[Assignment Gap]], [[Six Harness Components]], [[Context Window]]
---

# Starting Context

What an agent needs before beginning a task: goal, constraints, repository instructions, current state, relevant files, known failures — enough for the *first* decision, not an attempt to explain the whole system up front.

## The sufficiency test

Good starting context lets the agent search outward as new questions arise, rather than requiring a repository dump. Include exact acceptance criteria and the first verification command; label assumptions and known failures explicitly; prefer links and paths over pasted content when the agent's tools can retrieve it directly.

## What to leave out — for now

Every order-related file, unrelated screenshots, old rejected proposals, full CI logs — anything that doesn't change the *first* decision. These can come in later if a specific missing fact blocks progress; they don't need to be there pre-emptively.

## Common failure

Presenting an outdated plan as current state; omitting project instructions and then correcting generic conventions later instead of stating them up front; asking the agent to "explore" without a concrete anchor or question, which just relocates the assignment gap into the agent's own guesswork.

## Related concepts
- [[Assignment Gap]] — insufficient starting context is one concrete way a task prompt's assignment gap shows up in practice.
- [[Six Harness Components]] — starting context is the "Context & knowledge" component's per-task instance.
- [[Codebase Map]] + [[Task Specification]] — together, these two durable artifacts *are* the starting context for the next task on a given piece of behavior, instead of the whole repository or an old transcript. Source: [[Create Codebase Navigation Artifacts - AI Coding Course]]

## Sources
- [[Starting Context - AI Coding Course]]
