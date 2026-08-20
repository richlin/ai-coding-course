---
title: "Using Issue Trackers as Durable Task Memory"
author: AI Coding Course
type: essay
url:
file: 06-scale-the-work/issue-trackers.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Using Issue Trackers as Durable Task Memory — AI Coding Course

## Summary
An issue tracker stores task goals, ownership, status, dependencies, decisions, and evidence outside any single agent session, acting as a stable coordination unit for both humans and agents once work spans more than one session. Distinguishes the tracker's role (describing work state) from the repository's (source of truth for code and tests) — session history is temporary and hard for a team to inspect, so durable ticket state is what prevents duplicate work and unclear ownership.

## Key takeaways
- Keep each ticket bounded and independently verifiable; link commits, PRs, tests, and handoffs instead of copying them into the ticket.
- Update status, decisions, blockers, and links as work changes — chat must never hold newer status than the tracker.
- Close a ticket only when acceptance evidence is linked, not when implementation merely looks complete.
- Do not use one giant issue as a running transcript for an entire project, and do not create tickets with no owner or verification path.
- Do not duplicate an entire spec into every child ticket — link the shared contract instead.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Issue Tracker as Durable Memory]]

## Notable quotes
> "The tracker describes work state; the repository remains the source of truth for code and tests."

## My reaction
[OPEN] — not yet reviewed by Lin.
