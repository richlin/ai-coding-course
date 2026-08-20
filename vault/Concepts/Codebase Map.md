---
title: Codebase Map
tags: [type/concept]
related: [[Task Specification]], [[Statelessness]], [[Starting Context]], [[Instruction Budget]], [[Source of Truth Mapping]]
---

# Codebase Map

A maintained index of entry points, behavior owners, important flows, and their checks — real paths, symbols, and runnable commands, not a full description of every file.

```text
Task list flow
web/tasks/page.tsx
  -> api/tasks.ts:listTasks
  -> domain/tasks/list-tasks.ts:listTasks
  -> data/tasks.ts:findTasks

Behavior owner: domain/tasks/list-tasks.ts
Relevant tests: test/domain/tasks/list-tasks.test.ts
```

## Why it exists

A new session doesn't inherit the paths, decisions, and evidence an earlier session discovered while exploring — that's [[Statelessness]]. Exploration becomes reusable only when its findings are written into a repository artifact the next session can retrieve, instead of staying in the conversation where the next agent has to repeat the search.

## What it isn't

Not `AGENTS.md` — that's the standing brief (commands, boundaries, rules across tasks); the map describes structure. Not a task spec — the map says where to look, [[Task Specification|the spec]] says what to verify for one change. Collapsing these into one file makes an agent load the wrong detail at the wrong time.

## Maintenance rule

Update the map when a change moves an entry point, behavior owner, major flow, or verification command. Don't update it for an internal refactor that leaves navigation unchanged — the map tracks navigation, not implementation detail.

## Verifying it's useful

Give a fresh agent only repository instructions, the map, and the task spec. It should be able to name the first file to inspect, the code that owns the behavior, the nearby test, and the verification command — from the artifacts alone, without scanning the whole codebase. If it can't, the map has a stale path or an unsupported claim to fix. This is the same fresh-session test used to validate a [[Handoff Document|handoff]].

## Related concepts
- [[Starting Context]] — the map plus the spec together *become* the starting context for the next task, instead of the entire repository or an old transcript.
- [[Instruction Budget]] — the reason this lives in its own file rather than being inlined into `AGENTS.md`: different roles need different loading.
- [[Source of Truth Mapping]] — the map is one instance of this broader discipline, specifically for "where does this behavior live."

## Sources
- [[Create Codebase Navigation Artifacts - AI Coding Course]]
