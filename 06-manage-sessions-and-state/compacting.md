# Compacting and Auto-Compact

## What It Means

- Compaction summarizes an existing session so work can continue with less context.
- Auto-compact is a harness feature that performs this step when context pressure reaches a threshold.
- A compacted summary should preserve goals, constraints, decisions, evidence, current state, and next actions.

## Why It Matters

- Compaction extends a healthy session without carrying every raw interaction forward.
- Poor summaries can silently remove details that later decisions depend on.

## Concrete Example

- Before compaction, record: export goal, accepted CSV escaping rule, changed files, passing helper test, failing endpoint test, and next hypothesis.
- After auto-compact, verify all six facts remain and that a rejected package proposal is not presented as active.
- If the summary preserves confusion instead of evidence, begin a fresh session from a corrected handoff.

## Best Practices

- Save important artifacts and code changes before compaction.
- Review the resulting summary for missing constraints and unresolved questions.
- Restate the current task and verification state after auto-compaction.
- Compact at a natural phase boundary.
- Preserve exact commands and unresolved failures.
- Distinguish decisions from explored alternatives.
- Review generated summaries before continuing edits.

## Common Mistakes

- Do not compact a confused session and expect the summary to repair its reasoning.
- Do not compact before saving uncommitted state and evidence.
- Do not accept a summary that omits non-goals or security constraints.
- Do not preserve raw chronology instead of current state.
- Do not continue immediately after auto-compact without checking recall.

## Try It

1. Pause at the end of research or one implementation increment.
2. Write ten bullets covering goal, constraints, decisions, files, changes, checks, failures, questions, and next action.
3. Compact the session using your harness.
4. Compare the generated summary with the ten bullets.
5. Correct omissions, then ask the agent to predict the next check and expected result.

## Expected Result

- A verified compacted summary that supports the next phase.
- No rejected direction is mistaken for an active decision.
