---
title: Context Window
tags: [type/concept]
related: [[Statelessness]], [[Six Harness Components]], [[Lost in the Middle]]
---

# Context Window

The total tokens a model can see at once: input tokens (system prompt, prior messages, tool results) plus output tokens (the model's response), combined.

## Mechanism

Every model has a hard-coded token limit. Each new message in a session adds to the running total; nothing is removed automatically. Once the limit is reached, requests fail outright or the model produces truncated/incomplete output — there is no graceful degradation at the boundary itself.

## Why bigger isn't simply better

A larger limit does not mean better retrieval. Models struggle to pull specific facts back out of their own context, and attention is uneven across the window — see [[Lost in the Middle]]. Fewer, more relevant tokens tend to outperform more tokens, even when the larger window would technically fit.

## Capacity vs. budget

The window's limit is a capacity — how much text can technically fit. [[Smart Zone vs Dumb Zone|The smart zone]] is a smaller budget inside it — how much of that text the model can actually use well at once. A session can degrade well before the window is technically full, because stale or noisy content competes with current evidence for the same limited attention. Source: [[Context Degradation The Smart Zone and Dumb Zone - AI Coding Course]], [[Context Windows and Degradation - AI Coding Course]]

## Related concepts
- [[Statelessness]] — the context window is where the harness re-supplies everything the stateless model needs each turn; the window's limit caps how much of that state can be resupplied.
- [[Six Harness Components]] — "context quality over quantity" is the practical rule this concept explains the mechanism for.
- [[Lost in the Middle]] — the specific attention-degradation pattern inside the window.
- [[Smart Zone vs Dumb Zone]] — the behavioral budget that sits inside this capacity.

## Sources
- [[What Is The Context Window - Matt Pocock]]
- [[Context Degradation The Smart Zone and Dumb Zone - AI Coding Course]]
- [[Context Windows and Degradation - AI Coding Course]]
