---
title: Context Visibility
tags: [type/concept]
related: [[Smart Zone vs Dumb Zone]], [[Context Window]]
---

# Context Visibility

The harness-exposed indicators of how much a session has accumulated (token usage, attached files, active instructions, compaction events) — a warning signal about context pressure, not a direct measurement of answer quality.

## Why the distinction matters

Rising usage warns that old information may be crowding the active task; it doesn't confirm the output has actually degraded. Conversely, unused space remaining doesn't mean the session is healthy — a noisy, low-signal session can degrade at low reported usage. The percentage is an indicator to act on, not a score to optimize.

## Practical use

Watch usage during long investigations, but let behavior — repeated questions already answered, forgotten constraints — be the deciding evidence, not the number alone. Keep a current-state artifact independent of the status indicator, and reconfirm constraints after automatic compaction rather than trusting that the indicator reset means the state is fine.

## Related concepts
- [[Smart Zone vs Dumb Zone]] — visibility tooling is how you'd notice the drift; it doesn't by itself tell you which zone you're in.

## Sources
- [[Context Visibility - AI Coding Course]]
