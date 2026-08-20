---
title: Statelessness
author: AI Coding Course
type: essay
url:
file: 01-ai-coding-system/statelessness.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Statelessness — AI Coding Course

## Summary
Explains what is lost at a session boundary and how to preserve the facts that matter using durable artifacts and a handoff document. The mental model: a new session gets artifacts, not history. Statelessness at the boundary is distinct from context degradation inside a long-running session.

## Key takeaways
- Session memory (conversation context) does not carry over to a new session; only artifacts placed in the repository do.
- The useful mental model: `new session gets artifacts, not history`.
- Statelessness ≠ context degradation: statelessness is a boundary condition; degradation is an in-session problem.
- Each important fact belongs in the artifact designed to govern future work: tests for behavior, code for implementation, tickets for status/acceptance, ADRs for rationale, handoffs for current state.
- A handoff should contain: goal, decision + rationale, files changed, checks run, open questions, next action. Not a diary of every file opened.
- Rule of thumb before ending a session: what could the next agent infer incorrectly from the repo alone?

## Open questions it raises
- What belongs in a handoff vs. in a durable artifact (e.g., when does a rationale belong in the handoff vs. an ADR)?

## Concepts touched
- [[Statelessness]]
- [[Handoff Document]]
- [[Harness Engineering]]

## Notable quotes
> "The useful mental model is simple: a new session gets artifacts, not history." (Where the State Goes)

> "Before ending a session, ask what the next agent could infer incorrectly from the repository alone. Preserve the facts that would change its next decision, put each one in the artifact that should own it, and leave the handoff as a map." (Exercise: Cross the Session Boundary)

## My reaction
The artifact taxonomy (tests → behavior, code → implementation, ticket → status, ADR → rationale, handoff → current state) is actionable and maps cleanly onto real team workflows. The cross-session exercise at the end is unusually practical.
