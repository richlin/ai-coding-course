---
title: Durable Artifacts vs Auto-Memory
tags: [type/concept]
related: [[Handoff Document]], [[Statelessness]], [[Harness Engineering]]
---

# Durable Artifacts vs Auto-Memory

Two different places persistent facts can live, with different audiences and different failure modes if used for the wrong kind of fact.

## The distinction

**Durable artifacts** — code, tests, specs, tickets, ADRs. Shared, reviewable, correctable by the team. Anything the team needs to see, question, or fix belongs here.

**Auto-memory** — a harness feature that stores selected facts across sessions, typically private and populated by observed behavior. Should hold only stable, low-stakes, non-sensitive facts — a preference for concise updates, not a security requirement.

## Why the boundary matters

Hidden or outdated memory can influence work without the team knowing why — a private memory entry isn't visible for review the way a ticket or ADR is. Automatically captured memory is also not guaranteed to stay accurate; it needs the same review-and-correct discipline as any other fact, but nobody but its owner is positioned to give it that review.

## Practical rule

Store each fact where its natural owner maintains it, and only in one place — don't duplicate a fact across a ticket and memory without a clear source of truth. A private preference must never override a project rule; if that happens, the rule wasn't actually enforced at the right layer (see [[Instructions vs Permissions]] for the general version of this failure).

## Related concepts
- [[Handoff Document]] — the artifact that should carry a session's durable facts forward instead of memory.
- [[Statelessness]] — the reason durable artifacts exist at all; memory only covers what the harness chooses to retain, not what the team requires to persist.

## Sources
- [[Durable Artifacts and Auto-Memory - AI Coding Course]]
