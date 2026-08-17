# Context Degradation

## What It Means

- Context quality can decline as a session accumulates old plans, noisy output, and obsolete assumptions.
- Relevant facts compete with irrelevant details for the agent's attention.
- A large context window does not guarantee that every detail will influence the answer equally.

## Why It Matters

- Agents may forget constraints, repeat work, or follow an outdated direction late in a session.
- Adding more text can reduce quality when it hides the controlling evidence.

## Concrete Example

- Early in a session, the agent correctly chooses the repository's existing limiter.
- After large logs, rejected designs, and several edits, it proposes a second limiter and forgets the “no new dependencies” constraint.
- The window may still have capacity, but the working context has degraded.
- A focused brief with the goal, accepted decision, current diff, failing test, and next action restores signal.

## Best Practices

- Keep the active goal, constraints, current decision, and latest evidence visible.
- Save raw logs in files and include only relevant excerpts.
- Remove or clearly mark superseded plans.
- Maintain a short current-state summary during long work.
- Use behavioral symptoms, not context percentage alone, to trigger a fresh session.

## Common Mistakes

- Do not respond to every failure by adding more context; improve relevance first.
- Do not assume every token receives equal attention.
- Do not leave rejected approaches beside the current plan without labels.
- Do not compact a confused session and expect unsupported conclusions to become correct.
- Do not wait for the context window to be completely full before intervening.

## Exercise

1. Select a long session containing at least one changed decision.
2. Label its content `active`, `durable reference`, `superseded`, `raw evidence`, or `noise`.
3. Create a fresh brief with only goal, constraints, current decision, relevant files, latest evidence, and next check.
4. Ask separate fresh sessions to propose the next action from the full history and focused brief.
5. Compare constraint recall, correctness, and time to a useful action.

Complete the exercise when:

- A smaller brief preserving every decision-relevant fact.
- Evidence showing whether focused context improved the next decision.
