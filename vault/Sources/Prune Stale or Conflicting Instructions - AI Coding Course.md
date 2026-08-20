---
title: "Prune Stale or Conflicting Instructions"
author: AI Coding Course
type: essay
url:
file: 06-scale-the-work/prune-instructions.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Prune Stale or Conflicting Instructions — AI Coding Course

## Summary
Instruction pruning removes standing guidance (AGENTS.md/CLAUDE.md rules, user preferences, repository conventions) that has become outdated, duplicated, or contradictory — distinct from pruning a single session's context. Argues agents cannot reliably resolve hidden priority conflicts between rules, and that a smaller instruction set makes the constraints that remain easier to follow.

## Key takeaways
- Review instructions after major workflow, tooling, or architecture changes — old instructions preserve practices the codebase may have already replaced.
- When two rules conflict (e.g. a user rule says "always use npm" while the repository rule says "use pnpm"), merge duplicates and state explicit precedence rather than leaving both in force.
- Keep executable enforcement (lint rules, CI checks) synchronized with the prose that describes it, and assign one source of truth per convention.
- Test whether removing a rule changes behavior before deciding to keep it; prefer specific, observable guidance over broad quality slogans.
- Do not keep adding exceptions to a weak rule when it should be rewritten or deleted, and do not retain a rule just because it took effort to write.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Instruction Pruning]]

## Notable quotes
> "Agents cannot reliably resolve hidden priority conflicts."

## My reaction
[OPEN] — not yet reviewed by Lin.
