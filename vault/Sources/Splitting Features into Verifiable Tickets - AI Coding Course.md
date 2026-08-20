---
title: "Splitting Features into Verifiable Tickets"
author: AI Coding Course
type: essay
url:
file: 06-scale-the-work/verifiable-tickets.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Splitting Features into Verifiable Tickets — AI Coding Course

## Summary
A verifiable ticket delivers one coherent, user-visible outcome with explicit acceptance criteria and is small enough to implement, review, and check in one focused unit of work. Argues for vertical slicing — tickets that cut through the minimal layers needed to prove one behavior — over horizontal tickets split by technical layer ("create all database models," "build APIs," "make UI"), none of which alone proves anything works.

## Key takeaways
- Write tickets around outcomes, not file types or team boundaries — "a signed-in user can disable marketing email; the persisted choice prevents the next marketing send" is verifiable on its own.
- Split tickets that hide multiple unrelated "and" clauses, and name non-goals explicitly to protect each ticket's boundary.
- Include dependencies, likely ownership, and verification commands in the ticket, and keep shared groundwork only when a slice truly requires it.
- Do not create a horizontal ticket where no behavior can be verified until every other layer is also done.
- Do not size tickets solely by estimated coding time, and do not hide several channels or user roles inside one ticket.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Verifiable Ticket]]

## Notable quotes
> "Small tickets limit context, merge, and rollback risk."

## My reaction
[OPEN] — not yet reviewed by Lin.
