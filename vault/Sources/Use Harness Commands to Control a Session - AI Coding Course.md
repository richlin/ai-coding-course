---
title: Use Harness Commands to Control a Session
author: AI Coding Course
type: essay
url:
file: 02-configure-agent-harness/use-commands-for-repeatable-work.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Use Harness Commands to Control a Session — AI Coding Course

## Summary
Distinguishes built-in slash commands (harness-implemented session/product actions) from skills (model-guided packaged workflows), noting the shared `/` prefix does not indicate which mechanism is in play, and that the same command name can mean different things across harnesses.

## Key takeaways
- A slash command is not a shell command: `/diff` asks the harness to act; `git diff` asks the shell to run a program.
- Useful starter commands across Codex/Claude Code: `/model`, `/permissions`, `/status`, `/diff`, `/review`, `/compact`, `/clear`.
- Built-in commands are harness-specific and cannot be redefined by the user; skills can be authored by the harness, a plugin, a team, or the user, and can auto-load on a matching request.
- Same name, different mechanism: Codex's `/review` is a built-in action; Claude Code's `/review` is an alias for a skill.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Slash Commands vs Skills]]
- [[Skill Design and Testing]]

## Notable quotes
> "A name shared by two harnesses does not guarantee identical behavior."

## My reaction
[OPEN] — not yet reviewed by Lin.
