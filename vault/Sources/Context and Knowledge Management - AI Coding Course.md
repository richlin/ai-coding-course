---
title: "Context and Knowledge Management"
author: AI Coding Course
type: essay
url:
file: 07-design-the-team-harness/knowledge-management.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Context and Knowledge Management — AI Coding Course

## Summary
Distinguishes context management (selecting the information needed for the current decision) from knowledge management (preserving reliable information for future work), across sources that include code, tests, docs, tickets, decisions, memory, and external documentation. The organizing move is naming one source of truth per kind of fact and retrieving it on demand, rather than injecting a permanent documentation dump that goes stale.

## Key takeaways
- Name a source of truth for requirements, code behavior, decisions, and task state, and define precedence for when sources conflict.
- Keep durable knowledge close to the system it describes, and load it on demand through search and tools instead of holding it permanently in context.
- Assign ownership and review dates to manually maintained knowledge, and keep sensitive data out of general agent context.
- Do not create a large knowledge base without a freshness and retrieval strategy, and do not copy code behavior into prose that will drift from it.
- Do not treat all sources as equally authoritative, and do not retrieve a broad document when a symbol or section actually answers the question.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Source of Truth Mapping]]

## Notable quotes
> "Agents need current, authoritative information without receiving every available document."

## My reaction
[OPEN] — not yet reviewed by Lin.
