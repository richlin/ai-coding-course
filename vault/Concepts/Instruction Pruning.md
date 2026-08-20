---
title: Instruction Pruning
tags: [type/concept]
related: [[Context Pruning]], [[Harness Engineering]], [[Instructions vs Permissions]], [[Harness Retrospective]]
---

# Instruction Pruning

Removing standing guidance — AGENTS.md/CLAUDE.md rules, user preferences, repository conventions — that has become outdated, duplicated, or contradictory. Distinct from [[Context Pruning]], which sorts one active session's content; this operates on the durable instruction files that shape every session.

## Why it matters

Agents cannot reliably resolve hidden priority conflicts between rules — if a user rule says "always use npm" while the repository rule says "use pnpm," something has to make that conflict explicit rather than leaving both in force. Old instructions also preserve practices the codebase may have already replaced. A smaller instruction set makes the constraints that remain easier to actually follow.

## What good pruning looks like

Reviewing instructions after major workflow, tooling, or architecture changes. Merging duplicates and stating explicit precedence where overlap is necessary. Keeping executable enforcement (lint, CI) synchronized with the prose describing it. Assigning one source of truth per convention. Testing whether removing a rule changes behavior before deciding to keep it.

## Common failure

Adding exceptions to a weak rule instead of rewriting or deleting it. Retaining a rule because it took effort to write. Merging contradictory wording without deciding precedence. Leaving obsolete command examples in place. Pruning away rationale still needed for human judgment calls.

## Related concepts
- [[Context Pruning]] — same instinct (cut what no longer helps), different scope: one session's content vs. the standing instruction set that shapes every session.
- [[Harness Engineering]] — instructions are one of the harness components this pruning discipline keeps trustworthy.
- [[Harness Retrospective]] — a retrospective is often what surfaces the stale or contradictory rule that pruning then removes.

## Sources
- [[Prune Stale or Conflicting Instructions - AI Coding Course]]
