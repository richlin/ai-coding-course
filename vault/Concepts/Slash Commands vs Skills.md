---
title: Slash Commands vs Skills
tags: [type/concept]
related: [[Skill Design and Testing]], [[Six Harness Components]], [[Model vs Harness]]
---

# Slash Commands vs Skills

The same `/` prefix can invoke two different mechanisms — the prefix alone doesn't tell you which one.

## The distinction

**Built-in command** — supplied and implemented by the harness itself. Usually performs a product or session action directly (e.g., `/diff` opens the harness's diff view). Availability and behavior are harness-specific and cannot be redefined by the user.

**Skill** — supplied by the harness, a plugin, a team, or the user. Loads task-specific instructions, references, and optional scripts for the model to follow. Can be invoked explicitly or load automatically when a request matches its description.

The same name can mean different things across harnesses: Codex implements `/review` as a built-in working-tree review action; Claude Code exposes `/review` as an alias for a prompt-based skill. Visible action is similar; the underlying mechanism differs.

## Why it matters

You cannot redefine how a built-in command computes its result — that's harness logic. You can write a skill that tells an agent how your team reviews a specific kind of change. Knowing which one you're dealing with tells you whether to file a harness feature request or write a skill.

## Related concepts
- [[Skill Design and Testing]] — how to build the skill side of this distinction well.

## Sources
- [[Use Harness Commands to Control a Session - AI Coding Course]]
