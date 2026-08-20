---
title: Tool and Integration Design
tags: [type/concept]
related: [[Permission Boundaries]], [[Six Harness Components]], [[Instructions vs Permissions]]
---

# Tool and Integration Design

Designing the operations an agent uses to read, search, edit, test, browse, and act on external systems (tools), and the connections that let the harness reach repositories, issue trackers, documentation, and CI (integrations) — with inputs, outputs, permissions, error handling, and observability treated as first-class design decisions, not incidental plumbing.

## Why it matters

Reliable tools ground an agent in real state and make its actions verifiable. But every integration also adds a failure mode and a security exposure — the capability and the risk arrive together, so tool design is where [[Permission Boundaries|permission boundaries]] actually get implemented at the operation level.

## What good tool design looks like

A tool added only for a clear workflow need, with structured, typed, narrow operations preferred over unrestricted shell access or free-form command construction. Read and write capabilities kept separate, with write access and sensitive data restricted by default. Failures returned as actionable, specific errors rather than generic messages. Consequential external actions logged without exposing secrets, with an owner and credential-rotation plan attached to every integration.

## Common failure

Adding many overlapping tools that make action selection ambiguous. Exposing production write access for what is really a local implementation task. Returning huge unstructured payloads when specific fields would answer the question. Hiding a tool failure behind a generic error. Adding an integration with no ownership or credential rotation.

## Related concepts
- [[Permission Boundaries]] — the consequence-tier model that tool design has to actually implement at the level of individual operations.
- [[Instructions vs Permissions]] — a narrow, typed tool enforces a boundary the harness can guarantee; an instruction telling the model not to misuse a broad tool cannot.

## Sources
- [[Tools and Integrations - AI Coding Course]]
