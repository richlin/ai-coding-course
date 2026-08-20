---
title: What Is The Context Window?
author: Matt Pocock
type: article
url: https://www.aihero.dev/what-is-the-context-window
file:
date:
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# What Is The Context Window? — Matt Pocock

## Summary
Defines the context window as input and output tokens combined, notes every model has a hard token limit, and explains why bigger context windows don't straightforwardly mean better results — retrieval quality degrades as the window fills and attention is uneven across it (the "lost in the middle" problem).

## Key takeaways
- The context window is input tokens (system prompt, user messages) plus output tokens (model response), combined. Every model has a hard-coded limit on how many tokens it can see at once; exceeding it causes API errors or truncated/incomplete output.
- Token usage grows with every message added to a conversation — nothing shrinks automatically.
- "Lost in the middle": early and late messages in a long history get more attention from the model; content in the middle gets comparatively less. This gets worse as the context window fills.
- Larger context windows do not guarantee better performance. Models struggle to retrieve information from their own context and suffer attention degradation in the middle. Fewer, more relevant tokens in context tends to produce better results than more tokens.

## Open questions it raises
- [OPEN] — none stated explicitly; the article makes claims rather than posing unresolved questions.

## Concepts touched
- [[Context Window]]
- [[Lost in the Middle]]
- [[Statelessness]]
- [[Six Harness Components]]

## Notable quotes
> "the messages at the start of the history have quite a big impact on the output, and the ones at the end do too, but the stuff in the middle the LLM pays a bit less attention to"
> "you'll definitely still get better results from using fewer tokens in the context"

## My reaction
[OPEN] — not yet reviewed by Lin.
