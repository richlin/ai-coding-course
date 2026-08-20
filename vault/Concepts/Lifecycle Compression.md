---
title: Lifecycle Compression
tags: [type/concept]
related: [[Total Cost of AI Development]], [[Vibe Coding vs Agentic Engineering]], [[The 80% Problem]]
---

# Lifecycle Compression

The software development lifecycle does not compress evenly under AI-assisted development.

## Mechanism

Implementation — turning a decided design into code — collapses from weeks to hours because it is the step agents are best at automating. Requirements gathering, architecture decisions, and verification do not compress at the same rate, because they depend on judgment about business trade-offs, unstated constraints, and consequence — the things a model cannot fully perceive from the repository alone.

## Consequence

As implementation gets cheap, the bottleneck moves upstream and downstream: to writing a specification precise enough for an agent to execute against, and to verifying that what it produced actually matches intent. Speed gained in implementation is void if requirements were wrong or verification is skipped — hence [[Vibe Coding vs Agentic Engineering]]'s core distinction is about how much of that verification work happens at all.

## Related concepts
- [[Total Cost of AI Development]] — this is the structural reason verification remains a real cost even as token costs fall.
- [[The 80% Problem]] — a specific instance of judgment-intensive work resisting compression.

## Sources
- [[The New Software Lifecycle - Addy Osmani]]
