---
title: Integration Checkpoint
tags: [type/concept]
related: [[Dependency and Ownership Mapping]], [[Verifiable Ticket]], [[Acceptance Checks]]
---

# Integration Checkpoint

A defined point, occurring throughout delivery rather than only before release, where completed work from parallel tracks is combined and verified as a whole — contracts, migrations, shared state, end-to-end behavior, and any assumption left unresolved.

## Why it matters

Independently correct changes can still fail once combined. Frequent integration catches incompatibility while each change is still small enough to understand and fix.

## What good checkpoints look like

Criteria defined before parallel work starts, not as a meeting but as pass/fail evidence. Placed after a shared contract lands, after the first end-to-end slice, and before release. The highest-risk contract integrated earliest; production-like data used where risk warrants it.

## Common failure

Waiting for every parallel task to finish before attempting the first integration. Testing components only in isolation. Continuing to accumulate changes after a checkpoint has already failed. Omitting migration and rollback behavior from what gets checked.

## Related concepts
- [[Dependency and Ownership Mapping]] — checkpoints are where the mapped dependencies actually get tested together.
- [[Verifiable Ticket]] — checkpoints combine work from multiple verifiable tickets; each ticket's own acceptance criteria are necessary but not sufficient for integration.

## Sources
- [[Integration Checkpoints - AI Coding Course]]
