---
title: Rerouting
tags: [type/concept]
related: [[Specification Lifecycle]], [[Compliance Bias]], [[Task Specification]]
---

# Rerouting

Deliberate adaptation — changing the plan when new evidence invalidates the current approach or goal — as distinct from silent scope drift.

## Mechanism

Evidence can come from code, tests, users, production data, dependencies, or security constraints. Rerouting stops work at the *first* decision the new evidence invalidates, rather than patching a symptom to keep the disproven plan alive (e.g., adding a longer timeout when the real problem is that a volume assumption was false).

## The reroute note

A reroute note separates what's newly known from what's recommended: it states what evidence changed and which assumption it invalidated, names the affected acceptance criteria, lists options, gives a recommendation, and states the cost of discarded work and migration impact. Implementation pauses until the responsible human approves the new destination — the agent surfaces the contradiction and the tradeoff; it does not decide a product or risk tradeoff on its own authority.

## What to preserve

Discard work only when it no longer supports the revised goal — a changed architecture doesn't automatically invalidate valid tests or components built under the old one. Once the destination changes and is approved, update the spec, tasks, and acceptance criteria before continuing, and re-evaluate already-completed work against the revised criteria; don't keep executing old tickets against a spec that no longer applies.

## Related concepts
- [[Specification Lifecycle]] — rerouting is the trigger; updating the spec (rather than archiving or silently ignoring it) is the usual consequence.
- [[Compliance Bias]] — the failure mode rerouting guards against is the inverse problem: an agent that keeps agreeably executing a plan evidence has already disproven, rather than surfacing the contradiction.

## Sources
- [[Rerouting When Evidence Changes the Destination - AI Coding Course]]
