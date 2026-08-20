---
title: Issue Tracker as Durable Memory
tags: [type/concept]
related: [[Handoff Document]], [[Durable Artifacts vs Auto-Memory]], [[Statelessness]]
---

# Issue Tracker as Durable Memory

Storing task goals, ownership, status, dependencies, decisions, and evidence in an issue tracker rather than in agent session history, so both humans and agents have a stable coordination unit that outlives any single session.

## Division of labor

The tracker describes work state — what's decided, who owns it, what's blocked. The repository remains the source of truth for code and tests. Neither substitutes for the other.

## Why it matters

Session history is temporary and hard for a team to inspect. Durable ticket state is what prevents duplicate work and unclear ownership once work spans more than one session or more than one agent.

## What good tracker use looks like

Bounded, independently verifiable tickets. Commits, PRs, tests, and handoffs linked rather than copied in. Status, decisions, and blockers updated as work changes, so chat never holds newer information than the tracker. Tickets closed only when acceptance evidence is linked.

## Common failure

One giant issue used as a running transcript for an entire project. Tickets with no owner or verification path. Chat holding status the tracker doesn't have. Entire specs duplicated into every child ticket instead of linked.

## Related concepts
- [[Handoff Document]] — a handoff hands off current state at a session boundary; the tracker holds durable state across the whole task's life.
- [[Durable Artifacts vs Auto-Memory]] — the tracker is one form of durable artifact, specifically for task coordination.

## Sources
- [[Using Issue Trackers as Durable Task Memory - AI Coding Course]]
