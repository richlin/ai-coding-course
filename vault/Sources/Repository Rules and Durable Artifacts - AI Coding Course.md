---
title: Repository Rules and Durable Artifacts
author: AI Coding Course
type: essay
url:
file: 04-specify-and-plan-work/repository-rules.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Repository Rules and Durable Artifacts — AI Coding Course

## Summary
A synthesis lesson placing `AGENTS.md`-style repository rules alongside the other durable artifacts (specs, tests, tickets, ADRs, handoffs) an agent needs — all giving humans and agents a shared source of truth that survives model changes, session resets, and team handoffs. Mostly reinforces concepts already in the vault ([[Instruction Budget]], [[Durable Artifacts vs Auto-Memory]], [[Harness Engineering]]) rather than introducing a new mechanism.

## Key takeaways
- Store each fact near the code or workflow it governs, and prefer an executable check over prose whenever a standard can be automated.
- Don't document a standard CI already enforces differently, and don't rely on a private user rule for team-critical behavior.
- A concrete exercise: list ten facts an agent needs for a normal change, classify each as rule/spec/test/ADR/ticket/temporary context, and check for duplicates or conflicts across scopes.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Instruction Budget]]
- [[Durable Artifacts vs Auto-Memory]]
- [[Harness Engineering]]

## Notable quotes
> "Durable decisions survive model changes, session resets, and team handoffs."

## My reaction
[OPEN] — not yet reviewed by Lin.
