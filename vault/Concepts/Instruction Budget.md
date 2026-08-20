---
title: Instruction Budget
tags: [type/concept]
related: [[Six Harness Components]], [[Harness Engineering]], [[Context Window]], [[Lost in the Middle]]
---

# Instruction Budget

Every rule loaded into a standing instruction file (`AGENTS.md`, `CLAUDE.md`) consumes context on every task, whether or not that task needs it — so the file's size is a cost decision, not just an organization decision.

## The rule of thumb

Keep a standing instruction file within roughly 100-150 lines; treat that as a ceiling, not a target. Ask of every line: "does an agent need this before its first decision on most tasks in this scope?" If not, move it closer to where it's actually needed — a subtree instruction file, a skill loaded only for matching work, or a linked doc fetched only when triggered.

```text
AGENTS.md -> docs/typescript.md          (read for TypeScript changes)
          -> release skill               (loaded only for release work)
```

"For TypeScript changes, read `docs/typescript.md`" is a triggered breadcrumb. "Read every file in `docs/`" just relocates the same context cost.

## What belongs vs. what doesn't

Belongs: project purpose, commands the agent can't safely guess, boundaries around generated files/migrations/dependencies, conventions where the wrong pattern causes real rework, stable verification expectations, links with a clear trigger.

Doesn't belong: a task's definition of done (that's the task prompt's job — see [[Assignment Gap]]), long architecture tutorials, generic advice, rules already enforced by a formatter/linter/CI, secrets, and anything likely to go stale.

## Why the ceiling matters mechanically

This isn't just tidiness — it's the same token-cost logic as [[Context Window]] and [[Lost in the Middle]]: an always-loaded file competes for the same limited, unevenly-attended space as everything else in context. A padded 100-line file can crowd out or bury the one rule that actually matters for this task.

## Related concepts
- [[Six Harness Components]] — this is the concrete size/placement discipline for the "Ground rules & specs" component.
- [[Harness Engineering]] — duplicate or drifting instructions across prompts, skills, and docs is the ownership failure mode this budget is meant to prevent.

## Sources
- [[Write a Good AGENTS.md - AI Coding Course]]
