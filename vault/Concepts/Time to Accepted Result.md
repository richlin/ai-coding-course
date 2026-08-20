---
title: Time to Accepted Result
tags: [type/concept]
related: [[Total Cost of AI Development]], [[Non-Determinism]], [[Acceptance Checks]]
---

# Time to Accepted Result

The useful latency metric for AI-assisted development: the time from starting a task to the moment the change has passed required checks and a reviewer is willing to keep it.

Contrasts with narrower metrics:
- **Time to first token** — measures model responsiveness, not task completion.
- **Time per response** — measures one model request, not the end-to-end path.

## Components

- Model + effort selection → latency per request
- Tool execution time (repository searches, builds, tests)
- Sequential dependencies (dependent steps must wait for earlier results)
- Failed attempts → correction, rerun, and review cycles
- Human review time

## Optimization implications

A lightweight model can be the slower choice if it needs three repair passes. A heavyweight model can finish sooner when its first implementation survives tests and review.

**Run independent checks in parallel; keep dependent steps sequential.** A test that relies on generated code cannot start before the code exists — skipping that dependency may look faster while producing evidence about the wrong state.

**Define the stopping point before starting.** Without a stopping rule, an agent can keep polishing or exploring after the useful work is complete. The [[Research Plan Implement Verify Loop]] operationalizes this per increment: put the disproving check into the plan before editing, so "done" is the check passing, not a feeling that the code looks finished. Source: [[Research Plan Implement Verify - AI Coding Course]]

Source: [[Cost - AI Coding Course]]
