---
title: Total Cost of AI Development
tags: [type/concept]
related: [[Time to Accepted Result]], [[Reasoning Effort]], [[Model vs Harness]]
---

# Total Cost of AI Development

The full cost of AI-assisted development is not the provider token bill. The useful calculation includes:

**Total cost = model tokens + engineer time + tool execution + retries + review cycles + consequence of wrong answers**

## Why the full picture matters

The cheapest model request is not necessarily the cheapest way to finish a task. A low-cost model that needs repeated correction can consume more tokens and more engineering time than a stronger model that succeeds on the first pass.

The agentic loop is often the dominant cost component: each failed pass consumes both tokens and human attention.

## Cost scales with consequence

A wrong variable name in internal documentation is cheap to fix. A subtle authorization bug, irreversible migration, or broken public API can consume days of recovery and harm users.

**The size of the diff is a poor proxy for risk.** Renaming a hundred private variables may be reversible and cheap. Changing one boolean in an access-control path may warrant the most careful workflow available.

## Vibe coding vs agentic engineering cost curves

[[Vibe Coding vs Agentic Engineering]] describes matching cost curves: vibe coding has low upfront cost but expensive running cost (token burn, maintenance, security cleanup accumulate later); agentic engineering inverts this — higher upfront investment, lower marginal cost per feature. A cited 3-10x cost advantage for agentic engineering is illustrative, not empirically measured. [OPEN] Source: [[The New Software Lifecycle - Addy Osmani]]

## Escalation limits

More model capability or higher reasoning effort cannot:
- Reveal a file that was never provided
- Repair a broken tool
- Decide an unstated requirement
- Fix a context full of irrelevant history

Fixing the source of the failure is usually cheaper than paying for a more elaborate guess.

Source: [[Cost - AI Coding Course]]
