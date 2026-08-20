---
title: Active Partnership
tags: [type/concept]
related: [[Compliance Bias]], [[Implementation vs Evaluation Task]], [[Frame Reset]]
---

# Active Partnership

A multi-turn interaction pattern where the user and coding agent share investigative work before committing to a solution. Contrasts with a one-way command model where the user specifies a change and the agent executes.

## How it works

1. User explains the outcome (not a proposed solution).
2. Agent inspects the repository for relevant facts.
3. Agent asks questions whose answers could materially change the design—and waits.
4. User supplies context the agent cannot discover (user reports, business constraints, tradeoffs).
5. Agent compares candidate solutions against the combined evidence before recommending.

Each turn contributes something the other side lacks. The agent reads code; the user reads the business context.

## What it is not

- The agent as equal decision-maker. The user still owns the decision.
- Blanket clarification. Questions should target facts that could change the result. Unnecessary questions add friction. ([Clarify When Necessary](https://aclanthology.org/2025.findings-naacl.306/))
- Listing assumptions. An agent asked to "list assumptions" may produce a tidy list and continue with the original proposal. Ask instead which premises could be false and require the agent to check the ones that are checkable.

## Useful opening prompt

> Work with me as an active engineering partner. Start by inspecting the repository for facts relevant to the outcome. Tell me what you can establish from the code, then ask me the questions whose answers could materially change the design. Wait for my answers before comparing solutions. Treat any implementation I suggest as a candidate, and support your recommendation with code, tests, measurements, or primary documentation.

Source: [[Compliance Bias - AI Coding Course]]
