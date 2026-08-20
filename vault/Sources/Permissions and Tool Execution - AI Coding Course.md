---
title: Permissions and Tool Execution
author: AI Coding Course
type: essay
url:
file: 01-ai-coding-system/permissions-and-tools.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Permissions and Tool Execution — AI Coding Course

## Summary
Explains how tool calls translate model text into real side effects, why permissions and instructions are not interchangeable, and how to configure and think about permission boundaries in Claude Code. The organizing principle: grant access by consequence, not by trust level.

## Key takeaways
- A tool call is where text becomes an action: the harness executes the tool if permitted, then returns output to the model.
- Instructions shape model behavior; deny rules prevent the harness from executing the action even if the model requests it.
- Permission boundaries ordered by consequence: read → local write → network access → external write → destructive/privileged.
- Human approval is most valuable at transitions between these categories; constant prompts for routine reads train reflexive approval.
- Permissions and sandboxing solve different problems — both together are stronger than either alone.
- Before approving a tool call, review working directory, full arguments, credentials in scope, and expected side effects — not just the command name.
- Start narrow (reads + scoped edits + required checks); expand when the agent reaches a concrete need.

## Open questions it raises
- none new beyond those raised by the six-component harness lesson

## Concepts touched
- [[Instructions vs Permissions]]
- [[Permission Boundaries]]
- [[Harness Engineering]]

## Notable quotes
> "Instructions and permissions play different roles here. A repository instruction can tell the model not to read `.env`, but that is guidance the model must follow. A deny rule prevents the harness from completing the read even if the model asks." (A Tool Call Is Where Text Becomes an Action)

> "The useful question is not 'Do I trust this agent?' It is 'What can this specific operation change, and how hard would that change be to undo?'" (Grant Access by Consequence)

## My reaction
The "grant by consequence, not trust" reframe is the key insight. The sandboxing distinction — permissions decide whether to invoke a tool; sandboxing limits what happens after it starts — is subtle but important for practitioners configuring production agents.
