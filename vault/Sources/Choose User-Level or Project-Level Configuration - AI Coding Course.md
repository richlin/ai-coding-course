---
title: Choose User-Level or Project-Level Configuration
author: AI Coding Course
type: essay
url:
file: 02-configure-agent-harness/choose-configuration-scope.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Choose User-Level or Project-Level Configuration — AI Coding Course

## Summary
Separates two questions that get conflated when a Claude Code setting misbehaves: reach (which sessions/people receive a config) and authority (which source wins on conflict). Covers the four durable scopes, precedence order, per-shape merge behavior (scalar vs. array vs. permission), and how prose instruction files (`CLAUDE.md`) concatenate rather than resolve by precedence.

## Key takeaways
- Choose scope by reach; diagnose a conflict by authority — they are different questions.
- Four scopes: managed, user, project, local; precedence for ordinary settings is managed > command-line > local project > shared project > user.
- Scalar values: highest-priority source that defines the key wins. Arrays: concatenate and dedupe. Permission arrays: merge, then evaluate deny before ask before allow.
- Project correctness must not depend on a private user/local file.
- `CLAUDE.md`/instruction files are a different system from `settings.json`: all discovered files concatenate (broadest to most specific); a more specific file does not delete a broader one, so two contradictory prose rules can both enter context.
- A task prompt is the current assignment, not a durable configuration layer or an enforceable security policy.
- Keep secrets out of checked-in configuration and instruction files regardless of scope.

## Open questions it raises
- [OPEN] — none stated explicitly; this is a procedural/reference lesson.

## Concepts touched
- [[Configuration Scope]]
- [[Settings Merge Behavior]]
- [[Instructions vs Permissions]]
- [[Permission Boundaries]]

## Notable quotes
> "This is precedence, not permission for a private preference to redefine a team requirement."

## My reaction
[OPEN] — not yet reviewed by Lin.
