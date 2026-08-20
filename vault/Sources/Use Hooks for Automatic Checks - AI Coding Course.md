---
title: Use Hooks for Automatic Checks
author: AI Coding Course
type: essay
url:
file: 02-configure-agent-harness/use-hooks-for-automatic-checks.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Use Hooks for Automatic Checks — AI Coding Course

## Summary
Explains hooks as code attached to a harness lifecycle event (event → matcher → structured input → handler → outcome), so a reaction doesn't depend on the model remembering to trigger it. Covers scope placement, a worked Claude Code example, four-layer verification, and matching hook cost to event frequency.

## Key takeaways
- A hook closes the gap between "the instructions describe the desired behavior" and "something actually causes it to happen".
- Event timing matters: a pre-action hook can block the action; a post-action hook can only report or follow up, not undo.
- Verification is four separate checks: settings parse → hook is registered (`/hooks`) → debug log shows it fired → observable state is actually right. Passing an earlier check doesn't prove a later one.
- Match hook cost to event frequency: cheap checks on frequent events (per-edit formatting), fuller checks on rarer events (pre-push test suite, CI).
- Hooks should report or make safe, local, reviewable corrections — not silently publish, touch production data, or approve a consequential action.
- A Git hook and a Claude Code hook are adjacent but different mechanisms, owning different lifecycles.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Hooks]]
- [[Deterministic Scripts]]
- [[Six Harness Components]]

## Notable quotes
> "A predictable trigger does not make a consequential side effect safe."

## My reaction
[OPEN] — not yet reviewed by Lin.
