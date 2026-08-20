---
title: Configuration Scope
tags: [type/concept]
related: [[Settings Merge Behavior]], [[Instructions vs Permissions]], [[Permission Boundaries]], [[Six Harness Components]]
---

# Configuration Scope

Two separate questions get conflated when a setting doesn't behave as expected.

## The distinction

**Reach** — which sessions and people can receive this configuration? Determined by where it's placed: managed (org-wide), user (`~/.claude/settings.json`, follows you across repos), project (`.claude/settings.json`, shared with every contributor), local (`.claude/settings.local.json`, this machine only).

**Authority** — when more than one scope defines the same setting, which source wins? Determined by documented precedence, not by which file happens to load first or last.

## Practical rule

Choose scope by reach: use the narrowest scope that still reaches everyone who depends on the configuration. Diagnose a conflict by authority: list every source that defines the setting, then apply the harness's precedence or merge rule.

Project correctness must not depend on a private user or local file — if every contributor needs it, it belongs in project or managed scope.

## Related concepts
- [[Settings Merge Behavior]] — what happens once you know which source wins: replace, merge, or documented exception.
- [[Instruction Budget]] — the equivalent scope question for prose instructions (`CLAUDE.md`/`AGENTS.md`), which concatenate rather than resolve by precedence.

## Sources
- [[Choose User-Level or Project-Level Configuration - AI Coding Course]]
