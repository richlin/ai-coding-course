---
title: Harness Observability
tags: [type/concept]
related: [[Acceptance Checks]], [[Harness Retrospective]], [[Verification Hierarchy]], [[Six Harness Components]]
---

# Harness Observability

Exposing actions, tool results, failures, costs, and runtime outcomes (observability), checking whether outputs satisfy predefined goals and constraints (validation), and using those signals to choose the next action or improve the harness (feedback) — three parts of the same loop. A team cannot improve a workflow it cannot observe or evaluate, and fast generation without feedback can move quickly in the wrong direction.

## What good observability looks like

Success signals defined before a workflow is enabled, with a baseline captured before any harness change so a later comparison is meaningful. Tool failures, verification results, approvals, cost, and latency all captured and tied to a specific decision or owner. Successful outliers reviewed alongside failures, not just failures. A recurring finding converted into a test, control, or clearer boundary rather than re-fixed by hand every time it recurs.

## Common failure

Collecting large volumes of logs with no decision they're meant to support. Measuring output volume as if it were productivity. Optimizing token cost while ignoring correction time. Collecting sensitive prompts or code with no policy or control around them. Adding a metric with no threshold or response defined.

## Related concepts
- [[Acceptance Checks]] — the per-task instance of validation; observability is the standing infrastructure that makes those checks' results visible and comparable over time.
- [[Harness Retrospective]] — the mechanism that turns an observability signal into an actual harness improvement.

## Sources
- [[Validation Observability and Feedback - AI Coding Course]]
