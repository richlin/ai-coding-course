# Killing Bloat and Pruning

## What It Means

- Context bloat is information that no longer helps the current task.
- Pruning removes or summarizes stale plans, duplicate output, irrelevant files, and resolved discussion.
- The goal is a smaller, higher-signal working set.

## Why It Matters

- Irrelevant information consumes attention and may reintroduce rejected directions.
- Focused context improves navigation, reasoning, and handoff quality.

## Concrete Example

- Keep: approved export criteria, chosen query service, current diff, failing formula-escape test, and next hypothesis.
- Summarize: earlier exploration that proved the list UI does not own filtering.
- Remove: full successful test logs, duplicate file reads, rejected package proposal, and resolved naming discussion.
- Preserve externally: raw logs or research needed for audit, but do not keep them active in conversation.

## Best Practices

- Keep the active goal, latest decisions, current diff, failures, and next check.
- Summarize completed investigation instead of retaining raw output.
- Remove instructions that duplicate stronger project rules.
- Preserve decisions with reasons, not only conclusions.
- Replace repeated raw evidence with a link and concise finding.
- Mark what changed since the last summary.
- Ask whether each item affects the next two decisions.

## Common Mistakes

- Do not prune evidence that explains a decision or is needed to reproduce a failure.
- Do not summarize away exact error messages or reproduction inputs still under investigation.
- Do not retain raw output merely because collecting it was expensive.
- Do not remove constraints after they become familiar.
- Do not keep both an old and current plan active.

## Exercise

1. Select a session with at least 20 interactions or substantial tool output.
2. Create `Keep`, `Summarize`, `Externalize`, and `Remove` lists.
3. Produce a one-page brief with goal, constraints, decisions, evidence, current state, open questions, and next action.
4. Start a fresh session using only the brief and repository.
5. Ask it to explain the current hypothesis and reproduce the latest failure.
6. Restore only information whose absence materially blocks the task.

Complete the exercise when:

- A brief significantly smaller than the original context.
- The fresh session can reproduce the failure and continue without reviving rejected work.
