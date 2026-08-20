---
title: Compliance Bias
author: AI Coding Course
type: essay
url:
file: 01-ai-coding-system/compliance-bias.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Compliance Bias — AI Coding Course

## Summary
A coding agent shows compliance bias when it accepts a user's proposed solution as settled rather than evaluating whether it serves the stated outcome. The lesson distinguishes implementation tasks (decision already made) from evaluation tasks (decision still open) and gives concrete prompt patterns—question framing, staged investigation, and frame resets—to keep agents in evaluation mode when that's what's needed.

## Key takeaways
- Compliance bias (a.k.a. sycophancy) occurs when an agent endorses a proposal without evidence rather than checking it against the stated outcome.
- Implementation tasks and evaluation tasks are structurally different; choosing the wrong frame silences the agent at the wrong moment.
- Framing the problem as a question rather than a confident statement substantially reduces expressed sycophancy (directional evidence from a controlled study, not proven for coding specifically).
- Clarification has a cost; ask only about facts whose answers could materially change the result.
- Multi-turn dialogue anchors proposals; a fresh-context side-by-side review corrects this better than in-dialogue pushback.
- Agreement is a poor quality signal; evidence (tests, measurements, primary docs, component definitions) is what validates a decision.

## Open questions it raises
- Does question-framing reliably reduce compliance bias in coding agents specifically, or only in the studied context?
- At what granularity should a user decide "this is now an implementation task" vs. keeping evaluation open?

## Concepts touched
- [[Compliance Bias]]
- [[Implementation vs Evaluation Task]]
- [[Active Partnership]]
- [[Frame Reset]]

## Notable quotes
> "Agreement is therefore a poor quality signal. Repository conventions, user reports, measurements, tests, and primary documentation can support a decision. Confident language cannot." (Agreement Is Not Evaluation)

> "Asking the agent to 'list assumptions' is not enough. It may invent a neat list and then continue with your proposal. Ask which premises need evidence or could be false, then require the agent to check the ones the repository or documentation can answer." (Active Partnership Is a Two-Way Conversation)

## Referenced research
- [Ask, Don't Tell](https://arxiv.org/abs/2602.23971) — question framing vs. confident statements; controlled study showing less sycophancy with question framing
- [Clarify When Necessary](https://aclanthology.org/2025.findings-naacl.306/) — clarification helps only when resolving uncertainty is worth another interaction
- [Challenging the Evaluator](https://aclanthology.org/2025.findings-emnlp.1222/) — side-by-side neutral evaluation outperforms in-dialogue argument for correcting multi-turn sycophancy
- [When Can LLMs Actually Correct Their Own Mistakes?](https://aclanthology.org/2024.tacl-1.78/) — models are not consistently reliable at self-correction from reflection alone

## My reaction
Practical and concrete. The save-button worked example makes the mechanism visible. The distinction between implementation tasks and evaluation tasks is the core concept — worth a standalone concept file. The referenced research is cited with appropriate epistemic humility ("directional evidence, not a guarantee"), which is the right posture.
