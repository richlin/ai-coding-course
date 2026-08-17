# Smart Zone and Dumb Zone

## What It Means

- The **smart zone** is the part of a session where goals, evidence, and constraints remain clear.
- The **dumb zone** is a practical label for degraded behavior such as repetition, forgotten constraints, and unexplained inconsistency.
- The boundary is behavioral and varies by task, model, and context quality.

## Why It Matters

- Continuing after clear degradation can produce more output while reducing useful progress.
- Recognizing the transition helps engineers compact, hand off, or start fresh at the right time.

## Concrete Example

- **Smart-zone behavior:** The agent remembers CSV security requirements, searches only relevant code, and predicts what each test will establish.
- **Dumb-zone signals:** It rereads the same route, proposes a rejected package, forgets organization filtering, and changes code before understanding a failure.
- Save current evidence and move to a fresh context instead of repeatedly correcting each symptom.

## Best Practices

- Watch for repeated searches, stale plans, contradictory edits, and missed instructions.
- Save current state before intervening.
- Choose compaction for a healthy task with excess history and a fresh session for confused reasoning.
- Define observable degradation signals before long work.
- Check whether corrections persist across the next two actions.
- Preserve state before any reset.
- Treat the terms as a practical heuristic, not a property of the model.

## Common Mistakes

- Do not use context percentage as the only boundary between smart and dumb zones.
- Do not insult or argue with the agent when context management is the issue.
- Do not continue because substantial work has already happened in the session.
- Do not compact unsupported assumptions into the next context.
- Do not restart without a verified state summary.

## Exercise

1. Review two long sessions: one effective and one degraded.
2. Identify at least five observable differences in search, recall, planning, editing, or verification.
3. Choose three degradation signals that another engineer could recognize.
4. Pair each with `prune`, `compact`, `fresh session`, or `handoff` and explain why.
5. Apply the rule during the next long task and record the result.

Complete the exercise when:

- A harness-specific intervention checklist with observable signals.
- A recovery action that preserves verified state and improves the next decision.
