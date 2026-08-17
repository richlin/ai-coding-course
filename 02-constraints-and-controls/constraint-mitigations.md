# How Harness Controls Mitigate Constraints

## What It Means

- Harness controls reduce known agent risks; they do not remove the risks completely.
- Compliance bias is reduced by active challenge, explicit alternatives, and human review.
- Statelessness is reduced by durable artifacts such as specs, tickets, tests, and handoffs.
- Context degradation is reduced by focused context, pruning, compaction, and fresh sessions.
- Non-determinism is reduced by precise goals, repeatable checks, and multiple evaluated attempts.

## Why It Matters

- Each failure needs a specific response instead of a generic request to “be more careful.”
- Controls make reliable behavior part of the system rather than dependent on one prompt.

## Concrete Example

- **Compliance failure:** The agent adds Redis without evidence. **Control:** require assumptions, repository evidence, and alternatives before dependency changes.
- **State failure:** A new session forgets the chosen store. **Control:** preserve the decision in a ticket or ADR and behavior in tests.
- **Context failure:** A long session forgets a constraint. **Control:** maintain a current-state brief and restart on degradation signals.
- **Variation failure:** Runs implement different semantics. **Control:** test exact status, window, reset, and bypass behavior.

## Best Practices

- Name the observed failure before choosing a control.
- Prefer executable controls when behavior can be tested automatically.
- Place controls as early as practical: prevent before detect, and detect before production.
- Combine controls for high-risk tasks, such as a spec, restricted permissions, tests, and approval.
- Assign owners and review dates to controls requiring maintenance.

## Common Mistakes

- Do not add controls indiscriminately; unnecessary rules and context create noise.
- Do not answer every failure with another prompt sentence.
- Do not rely on human review for issues a focused test can detect.
- Do not add approval gates without showing the evidence needed to decide.
- Do not keep controls after the workflow they govern changes.

## Exercise

1. Select one failed, slow, or heavily corrected agent task.
2. Write the first observable failure rather than the final symptom.
3. Classify its primary constraint.
4. Propose one preventive control and one detective control.
5. Choose the smallest control that catches the issue early.
6. Re-run or simulate the task and record whether the control changes the outcome.

Complete the exercise when:

- A trace from failure to constraint to control to evidence.
- One validated control with an owner and review condition.
