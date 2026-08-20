---
title: Vibe Coding vs Agentic Engineering
tags: [type/concept]
related: [[Acceptance Checks]], [[Implementation vs Evaluation Task]], [[Total Cost of AI Development]], [[Lifecycle Compression]]
---

# Vibe Coding vs Agentic Engineering

A spectrum describing how much verification surrounds an AI coding loop, not a difference in the underlying model or tools.

## The distinction

**Vibe coding** — casual, ad-hoc, prompt-driven development with no formal specs and no automated evals. Fast and cheap to start; disposable if wrong.

**Agentic engineering** — the same kind of agent loop wrapped in formal specifications, automated evals, and CI/CD gates. Slower and costlier to start; cheaper per feature once running.

Both use the same class of underlying tooling. What differs is whether [[Acceptance Checks]] and evaluation gates exist between "agent produced output" and "output ships."

## Cost curve

- Vibe coding: low upfront cost, expensive running cost — token burn, maintenance, security cleanup accumulate later.
- Agentic engineering: higher upfront investment, lower marginal cost per feature.
- A 3-10x cost advantage for agentic engineering is cited but flagged by the source as illustrative, not empirically measured. [OPEN]

See [[Total Cost of AI Development]] for the fuller cost accounting this maps onto.

## Related concepts
- [[Acceptance Checks]] — the mechanism that operationalizes "verification" on the agentic-engineering end of the spectrum.
- [[Implementation vs Evaluation Task]] — a per-task version of the same casual-vs-rigorous framing.
- [[Lifecycle Compression]] — explains why verification becomes the bottleneck that this spectrum is really about.

## Sources
- [[The New Software Lifecycle - Addy Osmani]] — introduces the spectrum and the cost-curve claim.
