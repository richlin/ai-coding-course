# Context Visibility

## What It Means

- Context visibility shows how much information a session has accumulated and what sources are included.
- Some harnesses expose token usage, attached files, active instructions, or compaction events.
- Visibility is an indicator of context pressure, not a direct measurement of answer quality.

## Why It Matters

- Rising context use can warn that old information is crowding the active task.
- Engineers can intervene before the session loses important constraints or becomes repetitive.

## Concrete Example

- A session begins with the export spec and six files but later accumulates 2,000 lines of logs, three rejected plans, and repeated file reads.
- The status indicator shows high context use, while behavior shows the agent asking questions already answered.
- Save the current decision, diff, failing test, and next step, then compact or start fresh.
- High usage is a warning; repeated constraint loss is the deciding evidence.

## Best Practices

- Watch context usage during long investigations and implementations.
- Recheck the active goal and constraints after compaction.
- Use behavior changes, not percentage alone, to decide when to restart.
- Learn which inputs your harness counts, including tool output and hidden instructions.
- Check context after attaching large files or command output.
- Keep a current-state artifact independent of the status indicator.
- Reconfirm constraints after automatic compaction.

## Common Mistakes

- Do not assume a session is healthy simply because unused context space remains.
- Do not interpret token percentage as a universal quality score.
- Do not wait for automatic compaction without saving critical state.
- Do not ignore repeated searches or forgotten decisions at low reported usage.
- Do not optimize token count while removing decision-critical evidence.

## Try It

1. Start a task with a written goal and three constraints.
2. Record context usage after initial research, after the first edit, and after test output.
3. At each point, ask the agent to restate the goal, constraints, current hypothesis, and next check.
4. Note repetition, omissions, stale plans, and unexplained changes.
5. Intervene using pruning, compaction, or a fresh session.
6. Measure whether constraint recall and next-action quality improve.

## Expected Result

- A task timeline connecting context pressure with observable behavior.
- Personal intervention signals based on evidence, not one percentage threshold.
