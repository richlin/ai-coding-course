---
title: "Subagents and Parallel Work"
author: AI Coding Course
type: essay
url:
file: 06-scale-the-work/subagents-and-parallel-work.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Subagents and Parallel Work — AI Coding Course

## Summary
A subagent receives a bounded task from a coordinating agent or human; parallel work runs independent tasks at the same time, but only reduces elapsed time when those tasks don't block or overwrite one another. Useful subagent roles — focused research, isolated implementation, test creation, independent review — share a structure: a defined scope, shared facts delivered through durable contracts or files, and a named integration owner who inspects artifacts rather than accepting summaries at face value.

## Key takeaways
- Define each subagent's scope, inputs, expected artifact, and verification before delegating — delegate artifacts, not vague help.
- Give agents shared facts through durable contracts or files, and isolate simultaneous edits with separate branches or worktrees.
- Keep final integration and acceptance with one named owner even when several agents contributed.
- Do not delegate an ambiguous task and expect subagents to independently resolve product or architecture conflicts.
- Do not accept summaries without inspecting the underlying artifacts, and do not parallelize dependent tasks purely for the appearance of speed.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Subagent Delegation]]

## Notable quotes
> "Parallelism reduces elapsed time only when tasks do not block or overwrite one another."

## My reaction
[OPEN] — not yet reviewed by Lin.
