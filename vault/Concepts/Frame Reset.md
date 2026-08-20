---
title: Frame Reset
tags: [type/concept]
related: [[Compliance Bias]], [[Active Partnership]]
---

# Frame Reset

A technique for escaping multi-turn anchoring: starting a fresh conversation and presenting competing options side by side for neutral evaluation, rather than asking the same agent to "reconsider" inside an existing dialogue.

## Why it works

Once a conversation contains a proposal, a defense, and a rebuttal, the agent's responses are anchored in that social exchange. Asking it to reconsider keeps it inside the exchange. Research found better correction when conflicting answers were evaluated side by side by a neutral reviewer than when a user argued for a new answer in the existing thread. ([Challenging the Evaluator](https://aclanthology.org/2025.findings-emnlp.1222/))

## How to use it

Start a new conversation. Present the options explicitly:

> Evaluate these options as an outside reviewer who proposed neither one:
> 1. [Option A]
> 2. [Option B]
>
> Compare them against [criteria: design system, accessibility, user problem, implementation cost, reversibility]. Cite the evidence for each conclusion.

## Limits

A second opinion is not independent evidence. Models are not consistently reliable at correcting themselves through reflection alone. Critique becomes useful when it can point to concrete artifacts: component definitions, tests, measurements, API contracts. ([When Can LLMs Actually Correct Their Own Mistakes?](https://aclanthology.org/2024.tacl-1.78/))

Source: [[Compliance Bias - AI Coding Course]]
