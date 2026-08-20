---
title: Compaction
tags: [type/concept]
related: [[Smart Zone vs Dumb Zone]], [[Fresh Session]], [[Handoff Document]]
---

# Compaction

Summarizing an existing session so work can continue with less context. Auto-compact is a harness feature that triggers this automatically at a context-pressure threshold.

## What a compacted summary must preserve

Goals, constraints, decisions, evidence, current state, and next actions. A summary that drops one of these silently removes something a later decision depends on — a rejected package proposal reappearing as if still active is the characteristic failure.

## What compaction cannot do

Compaction extends a *healthy* session; it cannot repair a session whose reasoning is already confused, because it summarizes what the session currently believes — including false conclusions. Shortening a wrong belief still leaves it wrong. Check important claims against code and tests before letting them survive a compaction.

## Practical discipline

Save uncommitted state and artifacts before compacting. Compact at a natural phase boundary, not mid-investigation. After auto-compact, restate the current task and verification state rather than assuming recall — review the summary for missing non-goals or security constraints before continuing.

## Related concepts
- [[Smart Zone vs Dumb Zone]] — compaction is the right move for excess history in a healthy task; a [[Fresh Session]] is the right move when the reasoning itself, not just the volume, is the problem.

## Sources
- [[Compacting and Auto-Compact - AI Coding Course]]
- [[Context Degradation The Smart Zone and Dumb Zone - AI Coding Course]]
- [[Choosing Between Clear Compact Handoff and Subagent - AI Coding Course]]
