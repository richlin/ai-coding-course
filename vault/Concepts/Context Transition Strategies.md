---
title: Context Transition Strategies
tags: [type/concept]
related: [[Compaction]], [[Fresh Session]], [[Handoff Document]], [[Smart Zone vs Dumb Zone]]
---

# Context Transition Strategies

Four actions that all reduce pressure on one context, but solve four different problems — picking the wrong one either preserves confusion or loses task state.

## The four options

| Action | Solves | Wrong use |
|---|---|---|
| [[Fresh Session|Clear / fresh session]] | Task changed, or reasoning is badly degraded | Restarting merely to dodge an unclear requirement |
| [[Compaction]] | Same healthy task, excess raw history | Compacting when the active reasoning is already wrong |
| [[Handoff Document|Handoff]] | Transfer across a person, harness, repository, or ownership boundary | Handing off raw history without current status |
| Subagent | Delegate a bounded task while the main session keeps coordination | Using a subagent as extra context space for a task that isn't actually well-scoped |

## Subagent delegation, specifically

A subagent needs a defined input, output, scope, and verification stated *before* delegation — not discovered after. Integration ownership stays with the parent/coordinating session; the parent validates the receiving context before allowing further edits. A subagent is isolation for a bounded question (e.g., "compare official CSV security guidance"), not a way to avoid deciding what the task actually is.

## The common thread

Save durable state before any of the four transitions, regardless of which one applies. Each is keyed to a different need — continuity (compact), recovery (fresh), transfer (handoff), or isolated delegation (subagent) — so the first question is which need you actually have, not which action feels available.

## Sources
- [[Choosing Between Clear Compact Handoff and Subagent - AI Coding Course]]
