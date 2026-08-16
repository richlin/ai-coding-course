# The Observe, Decide, Act, Verify Loop

## What It Means

- **Observe:** Read the request, relevant code, instructions, and current tool output.
- **Decide:** Form a small hypothesis and choose the next useful action.
- **Act:** Search, edit, run a command, or ask a focused question.
- **Verify:** Check whether the action produced the intended behavior.
- The loop repeats until the acceptance criteria are satisfied or a human decision is required.

## Why It Matters

- Long, unchecked action sequences allow one wrong assumption to corrupt later work.
- Verification turns an agent's plausible claim into engineering evidence.
- Small loops make failures easier to localize and reverse.

## Concrete Example

- **Observe:** The login route lacks a limiter, but another route uses `createRateLimiter()`.
- **Decide:** Reuse that helper with login-specific settings instead of adding a dependency.
- **Act:** Add the middleware and one focused test for the limit response.
- **Verify:** Run the focused auth test. If it fails because test state leaks, inspect setup before changing production code.
- **Repeat:** Add the reset-window case only after the first increment passes.

## Best Practices

- Give the agent observable acceptance criteria before it starts acting.
- Prefer one focused edit followed by one focused check.
- Require the agent to update its hypothesis when new evidence disagrees with it.
- State the expected result before running a command.
- Keep each action small enough that one check can evaluate it.

## Common Mistakes

- Do not treat “implementation complete” as verification; inspect behavior, tests, or another relevant signal.
- Do not allow several unrelated edits before the first check.
- Do not rerun a failed command unchanged without explaining what new evidence the retry provides.
- Do not preserve a hypothesis after the evidence disproves it.

## Try It

1. Select a change that fits in one or two files.
2. Write one acceptance criterion and one command that can falsify success.
3. Ask the agent to state its observation and hypothesis before editing.
4. Allow one focused edit, then run the chosen command.
5. Record how the result changed the next decision.

## Expected Result

- A four-part log showing observation, decision, action, and verification.
- The check either proves the criterion or produces evidence for the next loop.
