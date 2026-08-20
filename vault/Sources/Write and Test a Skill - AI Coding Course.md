---
title: Write and Test a Skill
author: AI Coding Course
type: essay
url:
file: 02-configure-agent-harness/write-and-test-a-skill.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Write and Test a Skill — AI Coding Course

## Summary
Short reference on packaging a recurring workflow as a skill (trigger, evidence, steps, verification) and proving it works by testing normal, edge, and non-triggering cases rather than trusting well-written prose.

## Key takeaways
- A skill should define when to activate, what evidence to gather, ordered steps, and how to verify completion.
- Testing checks behavior change on representative tasks, not whether the prose reads well.
- Worked example: an `export-security-review` skill triggers on CSV/spreadsheet/bulk-export changes, checks authorization/tenant isolation/formula injection/sensitive fields/limits/logging/tests, and should not trigger for internal JSON serialization with no user download.
- Common mistakes: vague "do everything well" skills, missing non-trigger examples, hardcoding commands that vary by repo, trusting untested prose, letting a review skill silently edit code.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Skill Design and Testing]]
- [[Slash Commands vs Skills]]

## Notable quotes
> "Untested instructions may sound good while adding no reliable behavior."

## My reaction
[OPEN] — not yet reviewed by Lin.
