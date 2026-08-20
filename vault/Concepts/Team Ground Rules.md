---
title: Team Ground Rules
tags: [type/concept]
related: [[Task Specification]], [[Instructions vs Permissions]], [[Six Harness Components]]
---

# Team Ground Rules

Stable, repository-scoped conventions and safety boundaries — commonly stored in `AGENTS.md`/`CLAUDE.md` — that answer "how we work here," kept explicitly distinct from a [[Task Specification|specification]], which answers "what this task must achieve." Scaling this practice from an individual engineer to a team adds shared ownership, consistent scope, and enforceable precedence as requirements.

## Why the rules/spec split matters

Shared ground rules reduce inconsistent behavior across engineers, models, and sessions. Keeping stable conventions separate from one task's requirements keeps both easier to maintain — a rule file that absorbs every past task's instructions grows without bound and stops being read carefully.

## What good team ground rules look like

Concise and specific to the repository, with task-specific detail pushed into specs or tickets instead. Objective rules automated with tests, linters, hooks, or CI, and the executable enforcement linked beside the prose that describes it. Explicit precedence stated for when user, project, and task instructions overlap. Owners assigned, with rules reviewed after architecture changes.

## Common failure

Copying every past task instruction into permanent project rules. Placing changing product requirements inside repository rules instead of a spec. Letting prose duplicate CI behavior in a way that can drift out of sync. Leaving precedence between user/project/task instructions ambiguous. Keeping a rule with no observable effect on behavior.

## Related concepts
- [[Task Specification]] — the per-task counterpart to a ground rule: outcome and constraints for one change vs. standing conventions for the whole repository.
- [[Instructions vs Permissions]] — ground rules are prose instructions; the highest-stakes ones still need a permission or hook behind them to be enforced regardless of model compliance.

## Sources
- [[Scaling Ground Rules and Specifications Across a Team - AI Coding Course]]
