---
title: Research Plan Implement Verify Loop
tags: [type/concept]
related: [[Acceptance Checks]], [[Time to Accepted Result]], [[Task Decomposition]]
---

# Research Plan Implement Verify Loop

The practical operating cycle for one development increment: research the requirement/code/constraints, plan a small change plus the check that could disprove it, implement the smallest complete edit that tests the plan, verify by running the check and updating the plan from the result.

## The discipline

Stop researching once a falsifiable, local hypothesis can be stated — not once the whole area is understood. Put verification *in* the plan before editing starts, not as an afterthought; define the cheapest discriminating check up front. Keep one active hypothesis visible, and separate research findings from implementation decisions so a wrong hypothesis doesn't get silently baked into the diff.

## Why a failed check should change belief, not just trigger more code

If a check fails, the useful response is often to revise the hypothesis (e.g., "the library already handles quoting, just not this prefix case") rather than to write more code against the original, now-suspect belief. Preserve evidence from failed checks as well as passing ones — a failed run is information, not noise to discard once the next attempt passes.

## Common failure

Running research, editing, and testing as three large, disconnected phases instead of a tight loop. Editing while the controlling code path is still ambiguous. Broadening tests before the focused check passes, or adding unrelated cleanup during implementation — both blur which change the verification result is actually about.

## Related concepts
- [[Acceptance Checks]] — the "check that could disprove the plan" this loop puts before editing is exactly this concept's discipline applied per-increment.
- [[Time to Accepted Result]] — a tight, hypothesis-driven loop is what keeps this metric from ballooning on repeated correction cycles.

## Sources
- [[Research Plan Implement Verify - AI Coding Course]]
