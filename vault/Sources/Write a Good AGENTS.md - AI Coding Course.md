---
title: Write a Good AGENTS.md
author: AI Coding Course
type: essay
url:
file: 02-configure-agent-harness/write-project-instructions.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Write a Good AGENTS.md — AI Coding Course

## Summary
Treats a standing instruction file's size as a cost decision: every loaded rule consumes context on every task. Gives a ~100-150 line ceiling, a belongs/doesn't-belong list, "triggered breadcrumb" links instead of blanket doc-loading, and a three-level (personal/repository/subtree) placement scheme, plus how Codex and Claude Code differ in loading these files.

## Key takeaways
- `AGENTS.md`/`CLAUDE.md` records durable project rules across tasks/sessions; a task prompt is the current assignment, not the same kind of artifact.
- Keep each instruction file within ~100-150 lines; treat 150 as a ceiling, not a target — a complete 30-line file beats a padded 100-line one.
- Test every line against: "does an agent need this before its first decision on most tasks in this scope?" If not, move it to a subtree file, a skill, or a linked doc with a clear trigger.
- Belongs: purpose, commands the agent can't safely guess, boundaries on generated files/migrations/dependencies, conventions where the wrong pattern causes rework, stable verification expectations, triggered links. Doesn't belong: task-specific acceptance criteria, tutorials, generic advice, rules already enforced by tooling, secrets, stale facts.
- Codex loads one file per directory root→cwd, closer file wins on conflict, `AGENTS.override.md` replaces same-directory `AGENTS.md`; it does not load descendant instructions unless started in that subtree. Claude Code uses `CLAUDE.md` and can import `AGENTS.md` via `@AGENTS.md`.
- Three levels: personal (`~/.codex/AGENTS.md`), repository, subtree (e.g. `services/payments/AGENTS.md`) — place each rule at the narrowest scope where it stays useful.
- Generated instruction files are drafts: review every line, remove discoverable facts and rules likely to go stale.

## Open questions it raises
- [OPEN] — none stated explicitly; references cited studies on measured effect of context files rather than posing new questions.

## Concepts touched
- [[Instruction Budget]]
- [[Six Harness Components]]
- [[Harness Engineering]]
- [[Configuration Scope]]

## Notable quotes
> "Generated instruction files are drafts, not finished rules."

## My reaction
[OPEN] — not yet reviewed by Lin.
