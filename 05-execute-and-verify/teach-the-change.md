# Using `/teach` to Explain a Change

## What It Means

- A teaching workflow asks the agent to explain completed work in terms of behavior, decisions, evidence, and tradeoffs.
- It helps an engineer verify understanding instead of accepting an opaque patch.
- The exact `/teach` command depends on the harness; the learning goal is tool-independent.

## Why It Matters

- Engineers remain responsible for code they merge even when an agent wrote it.
- Explanation can reveal assumptions, unnecessary complexity, or missing verification.

## Concrete Example

- Ask: “Trace a malicious customer name from database row to downloaded CSV.”
- A useful explanation identifies the serialization boundary, escaping rule, tests, and why ordinary CSV quoting was insufficient.
- It also names what was not changed, such as authorization or export size behavior.
- Compare every claim with the diff and test output.

## Best Practices

- Ask what changed, why this design was chosen, and how it was verified.
- Request a walkthrough of the controlling code path.
- Compare the explanation with the actual diff and tests.
- Ask for behavior, rationale, alternatives, and evidence.
- Request a call-path walkthrough for unfamiliar code.
- Ask what could still fail and which checks do not cover it.
- Explain the change back in your own words before merging.

## Common Mistakes

- Do not accept an explanation that merely translates each line into English.
- Do not let the agent omit tradeoffs or rejected alternatives.
- Do not trust file references without opening them.
- Do not confuse a polished explanation with verified correctness.
- Do not merge code you cannot explain at the level required to maintain it.

## Try It

1. Choose a completed change you did not write manually.
2. Ask the agent to explain user behavior, controlling path, design choice, verification, and residual risk.
3. Open every referenced file and test while reading the explanation.
4. Write three follow-up questions about edge cases or alternatives.
5. Explain the change to a peer or in your own notes without using the agent's text.
6. Resolve any claim you cannot substantiate before approval.

## Expected Result

- A concise explanation grounded in actual code and tests.
- You can describe why the change works, what evidence supports it, and what risk remains.