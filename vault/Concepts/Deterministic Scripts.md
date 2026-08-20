---
title: Deterministic Scripts
tags: [type/concept]
related: [[Hooks]], [[Acceptance Checks]], [[Six Harness Components]]
---

# Deterministic Scripts

The right mechanism when an operation can be fully specified as inputs, steps, output, and exit status — no model judgment required.

## What makes a script useful

- Clear contract: which arguments/files/env values it accepts, what it prints, what success/failure exit codes mean, whether it touches state outside the working tree.
- Actionable errors: identify the specific failure (e.g., source file and unresolved link target), not just "check failed".
- Safe to rerun: the same inputs should produce the same result, with no hidden partial writes.
- One implementation, many callers: a command, a hook, and CI should all invoke the same script rather than keeping parallel versions of the same rule.

## How it differs from adjacent mechanisms

A script differs from a command because it shouldn't depend on model judgment. It differs from a [[Hooks|hook]] because it doesn't decide *when* it runs — a person, command, hook, or CI job can all trigger the same script.

## Consequential actions still need a gate

Deterministic behavior does not make a consequential action safe to run automatically. A script that can change production data or contact an external system still needs an explicit approval boundary outside itself.

## Related concepts
- [[Acceptance Checks]] — "use the cheapest check that can observe the failure" is the same doctrine; a deterministic script is the cheapest-check option whenever correctness doesn't require judgment.

## Sources
- [[Write Deterministic Scripts - AI Coding Course]]
