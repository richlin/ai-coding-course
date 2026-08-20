---
title: Compliance Bias
tags: [type/concept]
related: [[Implementation vs Evaluation Task]], [[Active Partnership]], [[Frame Reset]]
---

# Compliance Bias

A coding agent shows compliance bias when it accepts a user's proposed solution as the requirement—and executes it—rather than checking whether the proposal actually serves the stated outcome. The agent completes the work correctly at the code level while the underlying decision remains unevaluated.

The same behavior is called *sycophancy* in the broader LLM research literature. Compliance bias is the engineering-context framing: the cost is not hurt feelings but shipped code that solves the wrong problem.

## Mechanism

The agent's training optimizes for producing responses the user finds satisfying. When a user states a proposal confidently, the agent reads agreement as the satisfying response. Evaluation—pushing back, asking questions, exposing weaknesses—risks producing a less immediately satisfying output.

## Observable signal

- Agent agrees, implements the change, then agrees again when asked to reverse it.
- Phrases like "You are absolutely right" appear regardless of whether the user was right.
- The agent produces a polished artifact (updated code, tests, documentation) that implicitly endorses the proposal's reasoning without checking the evidence.

## Countermeasures

1. **Question framing** — present the problem as an open question, not a conclusion. Directional evidence shows this reduces sycophancy in controlled settings. ([Ask, Don't Tell](https://arxiv.org/abs/2602.23971))
2. **Staged investigation** — ask the agent to inspect the repository and ask material questions before any implementation is proposed.
3. **Frame reset** — start a fresh conversation for important decisions; present candidates side by side for neutral evaluation. ([Challenging the Evaluator](https://aclanthology.org/2025.findings-emnlp.1222/))
4. **Evidence requirement** — explicitly ask the agent to support conclusions with code, tests, measurements, or primary documentation, not with confident language.

## What agreement cannot prove

Agreement is not evidence. Whether the agent agrees or disagrees cannot tell you whether a design decision is correct. What can support a decision: repository conventions, measurements, test results, user reports, API contracts, primary documentation.

## A wide assignment gap invites this

A compressed prompt with a large [[Assignment Gap]] leaves more room for the agent's guess to quietly stand in for an unevaluated decision — the agent fills the gap fluently rather than flagging what's missing. Closing the gap up front is a countermeasure alongside question framing and staged investigation. Source: [[Write an Effective Task Prompt - AI Coding Course]]

Source: [[Compliance Bias - AI Coding Course]]
