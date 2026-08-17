# Debugging and Recovery

## What It Means

- Debugging is the process of reproducing, localizing, explaining, fixing, and guarding a failure.
- Recovery restores a known-good state after a wrong edit, failed command, or invalid assumption.
- Evidence narrows the cause; guesses only create more possibilities.

## Why It Matters

- Agents can quickly generate several plausible fixes without identifying the root cause.
- A reproducible failure provides a stable target for both diagnosis and verification.

## Concrete Example

- **Reproduce:** Export a record whose customer name begins with `=` and inspect the raw CSV.
- **Localize:** Call the serialization helper directly; if unsafe output remains, the UI and download transport are not the cause.
- **Explain:** CSV quoting protects commas and quotes but does not prevent spreadsheet formula interpretation.
- **Fix:** Escape dangerous leading characters at the data-to-CSV boundary.
- **Guard:** Add helper and endpoint regression tests using realistic malicious inputs.

## Best Practices

- Reproduce the smallest failing case before editing.
- Change one variable at a time.
- Explain why the fix addresses the observed cause.
- Add regression protection and rerun the original reproduction.
- Save the exact input, environment, and observed output.
- Narrow one boundary at a time.
- Distinguish root cause from trigger and symptom.
- Return to a known-good checkpoint after speculative edits.

## Common Mistakes

- Do not stack speculative fixes until the symptom disappears.
- Do not debug from an error summary when exact output is available.
- Do not change production code before confirming reproduction.
- Do not confuse correlation with the code path causing the defect.
- Do not declare recovery until the original reproduction and regression checks pass.

## Exercise

1. Choose a reproducible failure and save exact setup, input, command, and output.
2. Ask the agent for three plausible causes and the cheapest check distinguishing them.
3. Run only that check and eliminate unsupported causes.
4. Repeat until one causal explanation fits the evidence.
5. Add a failing regression test, make the smallest fix, and rerun the original reproduction.
6. Remove any speculative edits that did not contribute to the fix.

Complete the exercise when:

- A cause-and-evidence chain that another engineer can reproduce.
- A minimal fix plus a regression test that fails without it.
