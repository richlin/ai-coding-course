---
title: Safe Shipping Pipeline
tags: [type/concept]
related: [[Verification Hierarchy]], [[Small Reversible Increments]], [[Escalation]], [[Six Harness Components]]
---

# Safe Shipping Pipeline

The combination of CI enforcement (shared, non-skippable checks on every change) and safe shipping practice (review, staged rollout, monitoring, rollback) that limits production risk for agent-generated code the same way it limits risk for human-written code.

## Why it matters

Local prompts and checks are easy to skip or configure differently per session — CI is the shared floor no individual session can quietly lower. Production behavior can also reveal failures pre-merge tests structurally cannot reproduce, which is why shipping doesn't end at merge.

## What a good pipeline looks like

Required tests, types, linting, builds, and security checks run in CI, with required local and CI commands kept aligned so a developer or agent can reproduce a CI failure locally. Feature flags or staged rollout separate deployment from release. Rollback and post-release success/abort signals are defined before deployment, not improvised after something breaks.

## Common failure

Weakening CI to merge plausible-looking agent output faster. Deploying an irreversible schema change before the backward-compatible code that reads it. Calling deployment "done" without observing runtime signals. Treating the agent's own summary as release approval.

## Related concepts
- [[Verification Hierarchy]] — CI is where the verification layers actually get enforced as a shared, non-optional gate.
- [[Small Reversible Increments]] — staged rollout and rollback are this property applied to the release step itself, not just the code change.
- [[Escalation]] — review and approval before high-risk deployment steps is escalation applied to the shipping pipeline.

## Sources
- [[CI Enforcement and Safe Shipping - AI Coding Course]]
