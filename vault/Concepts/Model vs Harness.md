---
title: Model vs Harness
tags: [type/concept]
related: [[Harness Engineering]], [[Six Harness Components]], [[Instructions vs Permissions]]
---

# Model vs Harness

The foundational distinction in agentic coding systems.

```
agent = model + harness
```

## What each does

**Model** — a trained neural network that receives tokens and predicts the next token. It does not read files, run commands, browse the web, or remember prior sessions. Everything that looks like planning or reasoning is prediction.

**Harness** — the software around the model. It assembles instructions and context, offers tools, checks permissions, executes approved actions, returns results to the model, and decides when to call the model again.

**Agent** — the running loop the harness creates by repeatedly calling the model, executing tools, and feeding results back.

One visible agent task (e.g., "add rate limiting") may involve dozens of model requests orchestrated by the harness.

## Why the distinction matters

Failure diagnosis depends on it:

- Model saw the relevant code but chose a poor design → stronger model or higher effort may help.
- Harness never supplied the authentication architecture → changing models leaves the defect in place; fix the context.
- Tool couldn't run → fix the tool or permission, not the model.

"The model is bad at this" is a specific claim that is often false when the actual problem is in the harness.

## Rough proportions

One estimate puts the split at roughly 10% model, 90% harness (instructions, tools, MCP servers, orchestration logic, guardrails, observability) — consistent with most failures tracing to configuration rather than model limitation. Source: [[The New Software Lifecycle - Addy Osmani]]

## The harness is where team encoding lives

The model is usually supplied to you. The harness is where you specify which rules apply, what evidence enters context, which actions are available, where humans must approve, and what proves the result is acceptable.

Source: [[Harnesses Agents and Models - AI Coding Course]], [[Model Selection - AI Coding Course]]
