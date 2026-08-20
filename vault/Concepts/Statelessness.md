---
title: Statelessness
tags: [type/concept]
related: [[Handoff Document]], [[Harness Engineering]], [[Model vs Harness]]
---

# Statelessness

The property of agent sessions that makes working state non-persistent across session boundaries.

**Mental model: a new session gets artifacts, not history.**

## Mechanism

An agent session builds temporary working state in the conversation context (decisions, file reads, command outputs, interpretations). When the session ends, this state is gone. A new session assembles its context from prompt, repository, instructions, and any explicitly provided artifacts — not from the prior conversation.

## Statelessness vs. context degradation

| | Statelessness | Context degradation |
|---|---|---|
| When | At the session boundary | Inside a long-running session |
| Cause | No cross-session persistence by default | Old plans, logs, and stale assumptions crowd out relevant facts |
| Fix | Handoff documents + durable artifacts | Prune or reorganize context |

Context degradation inside a session has a specific shape: the [[Context Window]] has a hard token limit, and within it attention is uneven — see [[Lost in the Middle]]. A larger context window does not fix this; more tokens can mean worse retrieval, not better. Source: [[What Is The Context Window - Matt Pocock]]

This "within a session" failure mode has its own name and diagnostic — see [[Smart Zone vs Dumb Zone]]. The two are explicitly distinct: restarting fixes degradation because it discards the unreliable working context; only durable artifacts (not restarting) fix statelessness, because a fresh session never had the working history to begin with. Source: [[Context Degradation The Smart Zone and Dumb Zone - AI Coding Course]]

## What survives a session boundary

Only what was placed in a durable artifact before the session ended:

| Artifact | What it preserves |
|---|---|
| Tests | Behavioral requirements |
| Code | Current implementation |
| Ticket/task file | Status, ownership, acceptance criteria |
| ADR | Decision rationale that matters after implementation changes |
| Handoff document | Current state, next action, open questions |

## Rule of thumb before ending a session

Ask: what could the next agent infer incorrectly from the repository alone? Preserve the facts that would change its next decision; put each one in the artifact that should own it; leave the handoff as a map.

Source: [[Statelessness - AI Coding Course]]
