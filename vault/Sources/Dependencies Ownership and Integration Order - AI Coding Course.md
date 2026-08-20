---
title: "Dependencies, Ownership, and Integration Order"
author: AI Coding Course
type: essay
url:
file: 06-scale-the-work/dependencies-and-ownership.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Dependencies, Ownership, and Integration Order — AI Coding Course

## Summary
Defines the three coordination primitives that let multiple agents work on the same feature without colliding: dependency (what must exist first), ownership (who decides, delivers, and verifies), and integration order (when independently developed changes can safely combine). Argues that parallel agents left to infer shared interfaces on their own will make incompatible assumptions, so contracts and owners must be explicit before parallel work starts.

## Key takeaways
- Define shared contracts (e.g. a data model's fields and default semantics) before parallel implementation begins, not during it.
- Assign one owner per ticket and a separate named owner for cross-ticket integration — shared ownership with no final decision-maker causes duplicated work and unresolved decisions.
- Keep dependency direction acyclic and visible in the tracker or plan; integrate foundations and high-risk contracts earliest.
- Do not parallelize work that is still negotiating the same interface, and do not let UI mocks drift from the accepted contract.
- Task completion is not the same as integrated feature completion — merging consumers before required migration compatibility exists breaks this distinction.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Dependency and Ownership Mapping]]

## Notable quotes
> "Parallel agents can make incompatible assumptions about shared interfaces."

## My reaction
[OPEN] — not yet reviewed by Lin.
