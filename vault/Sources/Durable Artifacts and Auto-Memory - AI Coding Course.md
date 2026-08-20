---
title: Durable Artifacts and Auto-Memory
author: AI Coding Course
type: essay
url:
file: 03-manage-context/durable-memory.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Durable Artifacts and Auto-Memory — AI Coding Course

## Summary
Distinguishes project artifacts (code, tests, specs, tickets, ADRs — shared, reviewable truth) from harness auto-memory (concise, cross-session facts, typically private and behavior-driven). Project artifacts should hold anything the team needs to see and correct; memory should hold only stable, non-sensitive, low-stakes facts.

## Key takeaways
- Store requirements and technical decisions in the repository or issue tracker, not only in agent memory — hidden or outdated memory can silently influence work the team can't see.
- Store only stable, useful, non-sensitive facts in memory (e.g., "prefers concise progress updates"); security requirements or team-critical rules do not belong there.
- Review and remove memory that becomes inaccurate — automatically captured memory is not guaranteed accurate forever.
- Don't duplicate one fact across several stores without a clear source of truth; store each fact where its natural owner maintains it.
- A private preference must not override a project rule.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Durable Artifacts vs Auto-Memory]]
- [[Handoff Document]]
- [[Statelessness]]

## Notable quotes
> "Do not use auto-memory as a replacement for specifications, tests, or project documentation."

## My reaction
[OPEN] — not yet reviewed by Lin.
