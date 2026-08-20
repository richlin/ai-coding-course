---
title: Non-Determinism
tags: [type/concept]
related: [[Acceptance Checks]], [[Model vs Harness]]
---

# Non-Determinism

The same prompt to a coding agent can produce different implementations across runs — different searches, tool calls, and code — even when the repository and request are identical.

## Sources

1. **Token sampling** — the model assigns probabilities to next tokens and samples; small differences compound across a run.
2. **Provider infrastructure** — requests may be batched across shared hardware; floating-point variations affect close choices.
3. **Context/environment** — a changed conversation, different tool output, or modified file is a different experiment, not evidence of non-determinism.

## The right mental model

Agent output is a **distribution**, not a fixed capability. Most runs land in an acceptable range; occasional runs hit the tails. The tails matter because production workflows eventually encounter them.

One passing run proves the workflow *can* produce acceptable output. It does not prove how often it will.

## Classifying differences between runs

- **Harmless** — different code shape, same behavior (variable names, file layout).
- **Beneficial** — reveals a better option (finds existing middleware instead of writing a custom counter).
- **Acceptance-breaking** — violates a requirement (wrong status code, counter that never resets).

Only acceptance-breaking differences must be eliminated.

## What to do

- Put determinism in the checks ([[Acceptance Checks]]), not in forcing identical implementations.
- Retry once for a bad draw; investigate a pattern (all runs miss the same constraint → fix the prompt/environment).
- Don't interpret short streaks of good/bad runs as trend evidence; repeat a fixed task from clean state with the same checks.

Source: [[Non-Determinism - AI Coding Course]]
