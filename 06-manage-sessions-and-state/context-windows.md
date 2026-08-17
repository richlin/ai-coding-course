# Context Windows and Degradation

## What It Means

- A context window is the limited information a model can consider during one response.
- It contains instructions, conversation, file contents, tool output, and generated text.
- Context can degrade before it is technically full because stale or noisy information competes with current evidence.

## Why It Matters

- Long sessions may lose constraints, repeat work, or follow outdated plans.
- Large files and command output consume space without always improving decisions.

## Concrete Example

- An export task starts with a spec and six files, then accumulates raw logs, rejected plans, full diffs, and repeated tests.
- The window includes all of this plus system instructions and tool schemas, not only visible chat.
- The agent begins forgetting the formula-escaping constraint before the window is full.
- Externalize logs, summarize verified findings, and start the next phase with the current decision and evidence.

## Best Practices

- Keep active goals, decisions, failures, and next steps explicit.
- Summarize large outputs and reference durable files when possible.
- Treat repeated confusion as a signal to compact, hand off, or restart.
- Budget context for implementation and verification, not research alone.
- Keep large output in files and quote only relevant excerpts.
- Track behavior such as recall and repetition alongside token usage.
- Save current state before automatic context management occurs.

## Common Mistakes

- Do not assume a larger context window removes the need to manage information quality.
- Do not count only visible prompt text.
- Do not load every potentially relevant file before searching.
- Do not retain successful command output after recording the result.
- Do not equate available tokens with reliable attention.

## Exercise

1. Inspect a session with substantial tool use.
2. Inventory instructions, messages, files, and tool output occupying context.
3. Label each item active, durable, stale, or noise.
4. Estimate the minimum brief a fresh agent needs for the next action.
5. Start fresh with that brief and compare its summary to the original state.

Complete the exercise when:

- A context inventory and focused continuation brief.
- The fresh agent preserves constraints and evidence without raw history.
