---
title: "Validation, Observability, and Feedback"
author: AI Coding Course
type: essay
url:
file: 07-design-the-team-harness/validation-and-feedback.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Validation, Observability, and Feedback — AI Coding Course

## Summary
Validation checks whether outputs satisfy predefined goals and constraints; observability exposes actions, tool results, failures, costs, and runtime outcomes; feedback uses those signals to choose the next action or improve the harness. A team cannot improve a workflow it cannot observe or evaluate, and fast generation without feedback can move quickly in the wrong direction.

## Key takeaways
- Define success signals before enabling a workflow, and capture a baseline before changing the harness so a later comparison is actually meaningful.
- Capture tool failures, verification results, approvals, and relevant cost or latency, and tie every signal to a decision or an owner.
- Review successful outliers as well as failures — a recurring review finding is a signal to convert into a test, control, or clearer boundary, not just fix and move on.
- Do not collect large volumes of logs without a decision they're meant to support, and do not measure output volume as productivity.
- Do not optimize token cost while ignoring correction time, and do not add a metric that has no threshold or response attached to it.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Harness Observability]]

## Notable quotes
> "A team cannot improve agent workflows it cannot observe or evaluate."

## My reaction
[OPEN] — not yet reviewed by Lin.
