# Reasoning Effort

Effort is a separate control from [model selection](model-selection.md). Choosing a stronger model changes the model itself. Raising effort gives the selected model more room for internal reasoning within each model request, if the provider and harness expose that control.

That internal reasoning is not the same thing as the answer you see. A reasoning model can generate hidden reasoning tokens while it breaks down the problem, compares approaches, and checks its first idea. Effort guides that work rather than assigning an exact token count: a simple request may use little reasoning even when the setting is high.

Higher effort therefore does not directly request a longer visible answer. The prompt or a separate verbosity setting controls that. The accounting is provider-specific, but [OpenAI, for example, counts hidden reasoning tokens as output usage](https://developers.openai.com/api/docs/guides/reasoning) even though they do not appear in the answer. Higher effort can therefore increase output-token usage and cost without producing more visible text.

Effort is not an agent iteration setting either. The harness decides when to call the model, run a tool, return the result, and call the model again. Effort applies inside those model requests. It may indirectly lead the model to inspect more evidence or choose more verification steps, but it does not prescribe a fixed number of tool calls or model calls.

Think of effort as time at the whiteboard, not as an intelligence upgrade. More time helps when the problem rewards careful reasoning. It does not teach the model facts it never learned, reveal files it was never shown, grant missing permissions, or repair a vague requirement.

## Effort Changes Latency

Higher effort usually makes a model request take longer because the model can spend more tokens on internal reasoning. That delay is useful when careful analysis improves the result. It is pure overhead when the task is mechanical or a deterministic check can settle it.

Favor lower effort while searching, formatting, or working through a tight edit-test loop. Accept the longer wait for a difficult root-cause analysis, design review, or safety-sensitive decision where the first plausible answer may be wrong.

The useful setting is not the highest one available. It is the lowest effort that produces reliable work for the task.

## When to Use Low, Medium, or High Effort

The labels vary by provider and harness, but the practical split is similar:

- **Low effort** is enough for finding a symbol, summarizing a file, formatting content, changing a well-isolated function, or running a known command. The answer is easy to check, so extended reasoning buys little.
- **Medium effort** is a sensible default for ordinary coding. The model needs to understand some surrounding code, make a few decisions, and verify the change, but it is following an established design.
- **High effort** helps with ambiguous bugs, cross-file behavior, architecture, concurrency, security, and migration planning. These problems often punish the first plausible answer.
- **Very high or xhigh effort** should be reserved for genuinely difficult reasoning where a mistake is expensive. It should not be the default setting for routine work just because it is available.

For example, adding another handler that copies an existing pattern is probably a medium-effort task. Deciding whether that handler is safe to retry across a distributed system may be a high-effort task even if the final code change is one line.

## Know When More Effort Will Not Help

If a model fails, raising effort is only one possible response. First identify the kind of failure.

- If it overlooked a constraint that was already in context, more effort or a stronger model may help.
- If it chose the first solution without considering alternatives, more effort may help.
- If it never saw the relevant file, give it the file.
- If "done" was never defined, clarify the requirement.
- If it could not run a command, fix the tool or permission problem.
- If the context is full of irrelevant history, reduce or reorganize the context.
- If a deterministic check can settle the question, run the check instead of asking the model to think longer.

Repeatedly increasing effort in response to a context problem only produces a slower, more expensive guess.
