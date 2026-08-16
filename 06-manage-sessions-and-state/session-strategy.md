# Choosing Between Clear, Compact, Handoff, and Subagent

## What It Means

- **Clear or fresh session:** Reset when the task changes or reasoning is badly degraded.
- **Compact:** Continue the same healthy task with a shorter summary.
- **Handoff:** Transfer work across a person, harness, repository, or ownership boundary.
- **Subagent:** Delegate a bounded task while the main session retains coordination.

## Why It Matters

- These actions solve different problems even though all reduce pressure on one context.
- Choosing the wrong action can preserve confusion or lose task state.

## Concrete Example

- **Compact:** Same export task, sound reasoning, excessive raw history.
- **Clear/fresh:** Implementation direction changed and old assumptions keep resurfacing.
- **Handoff:** Move completed backend export work to the frontend owner.
- **Subagent:** Ask a bounded researcher to compare official CSV security guidance while the main session retains implementation ownership.

## Best Practices

- Use compact for continuity, clear for separation, handoff for transfer, and subagents for isolation.
- Save durable state before any transition.
- Define a subagent's input, output, scope, and verification before delegation.
- Choose based on continuity, transfer, isolation, or recovery needs.
- Save durable state before every transition.
- Keep integration ownership in the parent task.
- Validate the receiving context before allowing edits.

## Common Mistakes

- Do not use a subagent merely as extra context space for an unclear task.
- Do not compact when the active reasoning is already wrong.
- Do not clear when another owner needs a portable record.
- Do not hand off raw history without current status.
- Do not delegate decisions lacking a defined owner.

## Try It

1. Collect four transition scenarios from real or sample work.
2. For each, identify whether continuity, recovery, transfer, or isolated delegation is needed.
3. Choose compact, fresh, handoff, or subagent.
4. Write required input, expected output, and validation for the transition.
5. Explain why each alternative is weaker.

## Expected Result

- A decision table usable during future context transitions.
- Every strategy is tied to a distinct coordination need.
