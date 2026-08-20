---
title: Instructions vs Permissions
tags: [type/concept]
related: [[Permission Boundaries]], [[Harness Engineering]], [[Model vs Harness]]
---

# Instructions vs Permissions

Two mechanisms that look similar but operate differently and cannot substitute for each other.

## The distinction

**Instructions** — guidance the model receives in its context (e.g., "do not read `.env`"). The model must choose to follow them. A sufficiently confused or misled model may not.

**Permissions** — rules the harness enforces before executing a tool call. A deny rule prevents the harness from completing the action even if the model requests it. The model's compliance is irrelevant.

## Why it matters

"Do not deploy" in a system prompt asks the model to behave. A denied deployment tool prevents the harness from carrying out the action regardless of what the model says.

Use instructions to shape behavior within the space of permitted actions. Use permissions to enforce the boundary of that space.

## Practical implications

- Sensitive files (`.env`, credentials) that must never be read → deny rule, not instruction.
- Style preferences, ordering constraints, output format → instructions are sufficient.
- External writes, deployments, pushes → permissions + human approval, not just instructions.

## Instructions don't resolve by precedence

Settings resolve by [[Configuration Scope|scope precedence]] — one winning value per key. Prose instruction files (`CLAUDE.md`/`AGENTS.md`) don't: every discovered file concatenates into context (broadest to most specific), and a more specific file does not delete a broader one. Two contradictory prose rules can both enter context, and the model may pick between them inconsistently — that's a reason to remove the duplicate or enforce the invariant with a permission, hook, or script instead of relying on "the closer file wins." Source: [[Choose User-Level or Project-Level Configuration - AI Coding Course]]

Source: [[Permissions and Tool Execution - AI Coding Course]], [[Harnesses Agents and Models - AI Coding Course]]
