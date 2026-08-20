---
title: Implementation vs Evaluation Task
tags: [type/concept]
related: [[Compliance Bias]], [[Active Partnership]]
---

# Implementation vs Evaluation Task

Two structurally different ways to frame a task for a coding agent. Choosing the wrong frame silences the agent at the wrong moment.

## The distinction

| | Implementation task | Evaluation task |
|---|---|---|
| What is already decided? | The solution (e.g., "make the button red"). | Only the outcome (e.g., "people must find the Save button"). |
| What gets investigated? | How to apply the change without regressions. | Why the problem exists and which solutions address it. |
| What can the reasoning change? | Implementation details only. | The proposed solution, diagnosis, or approach. |
| What counts as success? | The change works without breaking existing behavior. | The chosen change solves the problem without introducing new ones. |

## When each is appropriate

**Implementation task** — the team has already made and reviewed the decision. The agent's job is safe execution, not re-litigation.

**Evaluation task** — a proposal still needs investigation. The agent should inspect relevant code and evidence, ask material questions, and compare options before committing to a solution.

## The failure mode

Using an implementation task frame when the decision still needs evaluation. The agent executes polished, correct code that makes the proposal look finished—but none of that work validates the underlying reasoning.

Source: [[Compliance Bias - AI Coding Course]]
