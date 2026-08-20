---
title: Create Codebase Navigation Artifacts
author: AI Coding Course
type: essay
url:
file: 04-specify-and-plan-work/codebase-exploration.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Create Codebase Navigation Artifacts — AI Coding Course

## Summary
Argues exploration findings must be written into durable, repository-visible artifacts — a codebase map (reused across tasks) and a task spec (lives with one task) — rather than left in the conversation, because a new session inherits none of the prior session's discovered paths and evidence. Explicitly ties this to statelessness, durable artifacts vs. auto-memory, and starting context, all already in the vault.

## Key takeaways
- A codebase map is "an entry point, behavior owner, and check" index — not a full description of every file. Use real paths, symbols, and runnable commands; link to deeper docs instead of copying them.
- Update the map when an entry point, behavior owner, flow, or verification command moves; don't update it for an internal refactor that leaves navigation unchanged.
- A map without a spec risks a technically correct edit to the wrong problem; a spec without a map makes every agent rediscover where to work — the two artifacts answer different questions and shouldn't collapse into one file (and shouldn't live in `AGENTS.md`, which is the standing brief, not structure or a single task's requirements).
- Verify both artifacts with a fresh-session test: give a fresh agent only repository instructions + map + spec, and check whether it can name the first file, the behavior owner, the nearby test, the verification command, and any blocking open question without scanning the whole codebase.
- A handoff across a session/tool/owner boundary should link to the map and spec, not duplicate them — the handoff carries current state and next action; the map and spec remain the maintained sources for structure and requirements.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Codebase Map]]
- [[Task Specification]]
- [[Statelessness]]
- [[Durable Artifacts vs Auto-Memory]]
- [[Starting Context]]
- [[Handoff Document]]
- [[Instruction Budget]]

## Notable quotes
> "A map without a spec can lead to a technically correct edit that solves the wrong problem. A spec without a map makes every agent rediscover where to work."

## My reaction
[OPEN] — not yet reviewed by Lin.
