---
title: Permission Boundaries
tags: [type/concept]
related: [[Instructions vs Permissions]], [[Harness Engineering]], [[Six Harness Components]], [[Approval Policy]]
---

# Permission Boundaries

The organizing principle for agent permissions: **grant access by consequence, not by trust level**.

The useful question is not "Do I trust this agent?" It is "What can this specific operation change, and how hard would that change be to undo?"

## Consequence tiers

| Tier | Examples | Key risk |
|---|---|---|
| Read | File reads, documentation | Sensitive content entering context, logs, or later tool calls |
| Local write | File edits in a version-controlled working tree | Generated files, local databases, untracked data need extra care |
| Network access | `npm install`, `curl` | Downloads change lockfiles; outbound requests send data off-machine |
| External write | `git push`, PR creation, ticket update, message send | Git cannot restore; visible to others immediately |
| Destructive/privileged | Delete data, alter infrastructure, deploy, spend money | Potentially irreversible; may expose credentials |

## Where human approval is most valuable

At transitions between tiers. Constant prompts for routine reads train reflexive approval. A prompt before a production deployment gives the reviewer a meaningful decision.

## Permissions ≠ sandboxing

Permissions decide whether Claude Code invokes a tool. Sandboxing limits what happens inside the process after the tool starts. Both together are stronger than either alone.

## Merging across scopes

Permission rules defined at different [[Configuration Scope|scopes]] (user, project, local) merge into one combined policy rather than the higher scope replacing the lower one — see [[Settings Merge Behavior]]. When a tool call matches more than one rule, `deny` is evaluated before `ask`, then `allow`; the first match decides. Source: [[Choose User-Level or Project-Level Configuration - AI Coding Course]]

## Escalation as the human-in-the-loop mechanism

[[Escalation]] is the practice-level counterpart to this tier model: at a consequence-tier boundary, the right move is often to return the decision to a human rather than to grant broader standing permission just to avoid a focused approval step. Source: [[Reviewing Changes Security Boundaries and Escalation - AI Coding Course]]

[[Approval Policy]] turns this tier model into a concrete team-scale matrix — which actions run automatically, which merely notify, which require explicit approval, and which are prohibited — scored by impact, reversibility, and confidence. Source: [[Permissions and Human Approval - AI Coding Course]]

Source: [[Permissions and Tool Execution - AI Coding Course]]
