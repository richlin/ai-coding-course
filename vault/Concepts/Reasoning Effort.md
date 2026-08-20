---
title: Reasoning Effort
tags: [type/concept]
related: [[Total Cost of AI Development]], [[Model vs Harness]], [[Time to Accepted Result]]
---

# Reasoning Effort

A separate control from model selection that adjusts how much internal reasoning the selected model performs per request.

**Analogy:** time at the whiteboard, not an intelligence upgrade.

## What it is and isn't

- **Is:** More room for hidden token reasoning within a model request; useful when the problem rewards careful analysis.
- **Is not:** A model upgrade (you're still using the same model). Not an agent iteration control (the harness controls that). Not a way to reveal missing files or repair vague requirements.

## Cost implication

Hidden reasoning tokens count as output usage (provider-specific) even though they don't appear in the visible answer. Higher effort can raise token cost without producing more visible text.

## Practical tiers

| Effort | When to use |
|---|---|
| Low | Search, format, isolated edit, known command |
| Medium | Ordinary coding — implement a clear requirement, understand surrounding context |
| High | Ambiguous bugs, cross-file behavior, concurrency, security, migration planning |
| Very high | Genuinely expensive mistakes only — not the default for routine work |

## Failure-mode diagnosis

Raising effort only helps if the failure was: overlooked constraint already in context, or failure to consider alternatives. It won't help if: file was missing, requirement was vague, tool was broken, context was full of irrelevant history, or a deterministic check could settle the question.

Source: [[Reasoning Effort - AI Coding Course]]
