---
title: Verifiable Ticket
tags: [type/concept]
related: [[Task Decomposition]], [[Task Specification]], [[Small Reversible Increments]]
---

# Verifiable Ticket

A ticket that delivers one coherent, user-visible outcome with explicit acceptance criteria, sized to be implemented, reviewed, and checked as one focused unit — a vertical slice through the minimal layers required for that one behavior, not a horizontal slice by technical layer.

## Vertical vs. horizontal

Horizontal tickets ("create all database models," "build APIs," "make UI") never prove behavior on their own — nothing is verifiable until every layer is done. A vertical ticket like "a signed-in user can disable marketing email; the persisted choice prevents the next marketing send" is verifiable by itself, even though it touches schema, endpoint, delivery check, and UI.

## Why it matters

Small, vertical tickets limit context, merge, and rollback risk. Independent evidence per ticket is what lets a team integrate with confidence instead of discovering incompatibility only at the end.

## What good tickets look like

Written around outcomes, not file types or team boundaries. Split wherever an "and" clause hides a second, unrelated outcome. Include dependencies, non-goals, likely ownership, and verification commands. Keep shared groundwork only when a slice truly requires it.

## Common failure

Creating a ticket for every file. Sizing tickets solely by estimated coding time. Hiding several channels or user roles inside one ticket. Omitting integration behavior from acceptance criteria.

## Related concepts
- [[Task Decomposition]] — decomposition is the general splitting discipline; a verifiable ticket is what one resulting piece should look like.
- [[Task Specification]] — the spec defines the boundary; the ticket is the unit that gets implemented and verified against it.

## Sources
- [[Splitting Features into Verifiable Tickets - AI Coding Course]]
