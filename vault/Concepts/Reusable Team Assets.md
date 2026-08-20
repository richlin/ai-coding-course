---
title: Reusable Team Assets
tags: [type/concept]
related: [[Skill Design and Testing]], [[Deterministic Scripts]], [[Six Harness Components]]
---

# Reusable Team Assets

Skills, templates, scripts, review rubrics, task commands, and checklists that standardize a workflow the team performs repeatedly, so the team improves one shared workflow instead of re-writing prompts for every task. [[Skill Design and Testing]] is the discipline for one specific asset type; this is the broader category and the decision of which asset type fits a given workflow.

## Choosing the right asset type

Deterministic, mechanically checkable work belongs in a script — see [[Deterministic Scripts]]. Judgment-heavy work that still follows a recognizable pattern belongs in a skill or a rubric. Collapsing the two into one artifact hides which parts of a workflow are actually reliable versus which still require a judgment call.

## What a good asset looks like

Built from observed repetition and failure, not a hypothetical future need. Given an owner, scope, version, and test examples the same way a skill is tested against real cases. Measured by adoption and correction rate — how often it's used and how often its output needs fixing — not by how many assets the team has accumulated.

## Common failure

Creating an asset for a one-time problem. Hiding an important judgment call behind an automatic command that looks deterministic but isn't. Letting a template accumulate optional sections nobody fills in. Leaving a reusable asset untested after the underlying workflow changes, so it silently drifts out of date.

## Related concepts
- [[Skill Design and Testing]] — the design and testing discipline for one asset type; this concept is the broader category it belongs to.
- [[Deterministic Scripts]] — the asset type to reach for when the work is mechanically checkable rather than judgment-heavy.

## Sources
- [[Skills and Reusable Assets - AI Coding Course]]
