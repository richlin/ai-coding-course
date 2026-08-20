---
title: "Tools and Integrations"
author: AI Coding Course
type: essay
url:
file: 07-design-the-team-harness/tools-and-integrations.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Tools and Integrations — AI Coding Course

## Summary
Tools let an agent read, search, edit, test, browse, and act on external systems; integrations connect the harness to repositories, issue trackers, documentation, CI, and other services. Reliable tools ground agents in real state and make their actions verifiable, but every integration also adds a failure mode and a security exposure — tool design (inputs, outputs, permissions, error handling, observability) is a first-class part of the harness, not an afterthought.

## Key takeaways
- Add a tool only for a clear workflow need, and prefer structured, typed, narrow operations over unrestricted shell access or free-form command construction.
- Separate read and write capabilities, restrict write access and sensitive data by default, and expose useful, actionable failures so agents can recover safely.
- Log consequential external actions without exposing secrets, and assign ownership plus credential rotation to every integration.
- Do not add many overlapping tools that make action selection ambiguous, and do not expose production write access for what is really a local implementation task.
- Do not return huge unstructured payloads when specific fields would answer the question, and do not hide tool failures behind a generic error message.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Tool and Integration Design]]

## Notable quotes
> "Every external integration adds capability, failure modes, and security exposure."

## My reaction
[OPEN] — not yet reviewed by Lin.
