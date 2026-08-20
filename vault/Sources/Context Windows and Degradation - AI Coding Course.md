---
title: Context Windows and Degradation
author: AI Coding Course
type: essay
url:
file: 03-manage-context/context-windows.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Context Windows and Degradation — AI Coding Course

## Summary
A reference-style companion to the smart-zone/dumb-zone article: the context window holds instructions, conversation, files, tool output, and generated text — not just visible chat — and can degrade before it is technically full because stale or noisy content competes with current evidence.

## Key takeaways
- Budget context for implementation and verification, not only research — a task can run out of useful budget before the literal window fills.
- Keep large output in files and quote only relevant excerpts into the conversation; equating available tokens with reliable attention is the mistake to avoid.
- Treat repeated confusion as a signal to compact, hand off, or restart — not as a token-counting problem alone.
- Don't load every potentially relevant file before searching — that consumes budget without necessarily improving the next decision.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Context Window]]
- [[Smart Zone vs Dumb Zone]]

## Notable quotes
> "Do not equate available tokens with reliable attention."

## My reaction
[OPEN] — not yet reviewed by Lin.
