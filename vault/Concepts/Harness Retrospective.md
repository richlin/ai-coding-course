---
title: Harness Retrospective
tags: [type/concept]
related: [[Instruction Pruning]], [[Skill Design and Testing]], [[Debugging Loop]], [[Six Harness Components]]
---

# Harness Retrospective

Converting an observed outcome — a failure, a near miss, a costly retry, or an unusually successful run — into a change to specs, tests, rules, skills, tools, or memory, so the whole team benefits from what one task revealed instead of re-learning it on the next similar task.

## The core discipline

Separate a one-time mistake from a recurring system weakness before reacting. Target the improvement at the earliest point where the failure could have been prevented or detected — often a template, a missing test fixture, or an ambiguous rule, not a new prompt reminder repeated by hand each time.

## What a good retrospective produces

One small, measurable control rather than a pile of new instructions. An assigned owner and review date. A preserved example of the failure the control addresses, so its purpose is legible later. A before/after comparison against representative future tasks, with the control revised or removed if it doesn't hold up.

## Common failure

Turning every isolated mistake into a permanent rule. Blaming an individual agent run before inspecting the system that produced it. Adding a control with no baseline or success measure. Keeping an ineffective control because it looks rigorous. Studying only failures and never the efficient successes.

## Related concepts
- [[Instruction Pruning]] — retrospectives are often where a stale or redundant instruction gets identified for removal.
- [[Skill Design and Testing]] — a retrospective's control is frequently a new or revised skill, which then needs the same test discipline as any other skill.

## Sources
- [[Feeding Lessons Back into the Harness - AI Coding Course]]
