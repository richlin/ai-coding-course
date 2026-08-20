---
title: Harnesses, Agents, and Models
author: AI Coding Course
type: essay
url:
file: 01-ai-coding-system/system-components.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Harnesses, Agents, and Models — AI Coding Course

## Summary
Defines the core equation `agent = model + harness` and explains the six harness components that turn a model's prediction capability into a governable development workflow. The model predicts; the harness operates. Distinguishing these two roles is the prerequisite for correctly diagnosing failures and designing reliable coding workflows.

## Key takeaways
- A model predicts tokens; everything agentic comes from the harness around it.
- An agent is the loop created when the harness repeatedly calls the model, runs tools, and returns results — one visible task may involve dozens of model requests.
- The six harness components: ground rules/specs, context/knowledge, tools/integrations, skills/reusable assets, permissions/human approval, validation/feedback.
- Instructions and permissions are not interchangeable: instructions shape model behavior; permissions enforce harness boundaries regardless of what the model requests.
- Validation closes the control loop — without it the agent can't know when to stop or whether the change worked.
- Build the smallest harness that closes the loop; avoid adding components without a defined job.

## Open questions it raises
- What is the right level of granularity for a "skill" — when does a reusable asset become too coarse or too narrow?

## Concepts touched
- [[Model vs Harness]]
- [[Harness Engineering]]
- [[Six Harness Components]]
- [[Instructions vs Permissions]]

## Notable quotes
> "The model is usually supplied to you. The harness is where you encode how work happens in this codebase: which rules apply, what evidence enters context, which actions are available, where a human must approve, and what proves the result is acceptable." (Harness Engineering Makes Fast Changes Governable)

## My reaction
The clearest conceptual foundation in the course. The six-component framing is a useful checklist for diagnosing gaps in any agentic workflow.
