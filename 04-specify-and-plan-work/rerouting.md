# Rerouting When Evidence Changes the Destination

## What It Means

- Rerouting means changing the plan when new evidence invalidates the current approach or goal.
- Evidence may come from code, tests, users, production data, dependencies, or security constraints.
- Rerouting is deliberate adaptation, not silent scope drift.

## Why It Matters

- Continuing with a disproven plan wastes time and can create harmful workarounds.
- Agents need explicit permission to stop and surface contradictions.

## Concrete Example

- The approved plan builds a synchronous CSV response for at most 10,000 rows.
- Production evidence shows some customers have 500,000 matching orders and requests time out.
- The assumption about data volume is false, so adding a longer timeout is not the destination.
- A reroute note proposes queued generation, names new product questions, updates non-goals, and pauses implementation for approval.

## Best Practices

- State what evidence changed and which assumption it invalidated.
- Reconfirm the intended outcome with the responsible human.
- Update the spec, tasks, and acceptance criteria before continuing.
- Preserve useful completed work only when it still supports the revised goal.
- Stop at the first decision invalidated by evidence.
- Separate newly discovered facts from the recommended direction.
- Explain cost, discarded work, and migration impact.
- Obtain explicit approval when scope or user behavior changes.

## Common Mistakes

- Do not hide a destination change inside implementation details.
- Do not patch symptoms to preserve a plan disproven by evidence.
- Do not discard valid tests or components merely because the architecture changes.
- Do not let the agent approve a product or risk tradeoff owned by a human.
- Do not keep executing old tickets after the controlling spec changes.

## Exercise

1. Choose a sample or active spec with at least three assumptions.
2. Introduce or discover evidence that invalidates one important assumption.
3. Stop the current plan at the first affected task.
4. Write a reroute note containing old direction, evidence, affected criteria, options, recommendation, discarded work, and required decision.
5. Update the spec and task list only after the owner approves the new destination.
6. Re-evaluate completed work against the revised criteria.

Complete the exercise when:

- A visible, approved destination change with an evidence trail.
- No active ticket or acceptance criterion still points to the superseded plan.
