---
title: Verifying Information Against Primary Sources
author: AI Coding Course
type: essay
url:
file: 04-specify-and-plan-work/primary-sources.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Verifying Information Against Primary Sources — AI Coding Course

## Summary
A model's recalled API knowledge may be outdated, incomplete, or mixed across library versions. Source-driven work checks the project's actual installed version against official, version-matched documentation before committing an implementation choice to it.

## Key takeaways
- Check the project's actual dependency version (package.json/lockfile) before trusting recalled API behavior — don't ask the model to remember current docs when it can retrieve and verify them.
- Prefer official version-matched documentation over tutorials/snippets; verify publication date and applicable version, since docs for a newer major version can mislead.
- Use source code or tests when official prose is ambiguous; don't assume a popular tutorial reflects secure defaults.
- Record the verified conclusion and its applicability (version, link, consequence) in the spec or test — don't rely on the conversation retaining the documentation, and don't paste large copyrighted docs when a concise decision + link suffices.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Primary Source Verification]]
- [[Non-Determinism]]

## Notable quotes
> "Do not ask the model to remember current documentation when it can retrieve and verify it."

## My reaction
[OPEN] — not yet reviewed by Lin.
