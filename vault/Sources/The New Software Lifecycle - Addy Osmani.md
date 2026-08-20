---
title: The New Software Lifecycle
author: Addy Osmani
type: article
url: https://addyosmani.com/blog/new-sdlc-vibe-coding/
file:
date: 2026-06-16
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# The New Software Lifecycle — Addy Osmani

## Summary
Argues that AI agents compress implementation from weeks to hours while requirements, architecture, and verification remain judgment-intensive — shifting the SDLC bottleneck to specification and verification quality. Frames the model/harness split (~10%/90%) as the reason most agent failures are configuration problems, not model limitations, and places "vibe coding" and "agentic engineering" on a spectrum defined by how much verification surrounds the same underlying loop.

## Key takeaways
- "An agent is a model plus a harness" — roughly 10% model, 90% harness (instructions, tools, MCP servers, orchestration, guardrails, observability). Most agent failures trace to harness configuration, not the model.
- Two teams improved results by touching only the harness: Terminal Bench 2.0 ranking moved from outside the top 30 to top 5 by harness changes alone; a LangChain experiment added 13.7 benchmark points via system prompt and middleware changes.
- Context is a cost decision: static context (loaded every turn) is reliable but expensive; dynamic context (loaded on-demand) is cheaper per interaction but depends on the agent finding it when needed.
- Verification is the axis that separates "vibe coding" (casual, disposable, no formal checks) from "agentic engineering" (specs, automated evals, CI/CD gates). Output evaluation (is the result correct) and trajectory evaluation (was the reasoning path sound) are distinct checks.
- The SDLC compresses unevenly: implementation collapses from weeks to hours; requirements, architecture, and verification stay judgment-intensive. This raises the relative importance of specification and verification.
- Vibe coding has low upfront cost but expensive running cost (token burn, maintenance, security cleanup); agentic engineering inverts that curve — higher upfront investment, lower marginal cost per feature. Osmani cites a 3-10x cost advantage for agentic engineering but describes it as illustrative, not empirically measured.
- The "80% problem": agents reach initial functionality fast, but edge cases and system-integration seams remain hard — models typically lack enough context for the last-mile implementation details.
- Adoption context (early 2026): 85% of professional developers use AI coding agents regularly, 51% daily, 41% of new code AI-generated.
- Anthropic case study: agents built a working C compiler in Rust over two weeks under human oversight.
- Experienced developers can measure 19% slower on some tasks once verification time is counted — a caveat against assuming agents are always faster end-to-end.

## Open questions it raises
- How do teams close the 80% problem — the gap between fast initial functionality and finished, integrated, edge-case-safe code?
- What are the long-term maintenance costs and failure patterns of AI-generated codebases once the initial velocity gain has been banked?
- Is the 3-10x agentic-engineering cost advantage measurable in a real team's data, or does it hold only illustratively?

## Concepts touched
- [[Model vs Harness]]
- [[Harness Engineering]]
- [[Six Harness Components]]
- [[Total Cost of AI Development]]
- [[Acceptance Checks]]
- [[Implementation vs Evaluation Task]]
- [[Vibe Coding vs Agentic Engineering]]
- [[Output vs Trajectory Evaluation]]
- [[The 80% Problem]]
- [[Lifecycle Compression]]
- [[Conductor vs Orchestrator Modes]]

## Notable quotes
> "An agent is a model plus a harness."

## My reaction
[OPEN] — not yet reviewed by Lin.
