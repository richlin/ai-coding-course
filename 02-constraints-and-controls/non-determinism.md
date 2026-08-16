# Non-Determinism

## What It Means

- The same prompt can produce different reasoning, code, and tool choices on different runs.
- Small changes in context or model configuration can change the result.
- Variation is useful for exploring options but risky when work must be repeatable.

## Why It Matters

- One successful attempt does not prove that a workflow is reliable.
- Generated code must satisfy stable checks even when the generation process varies.

## Concrete Example

- Three agents receive the same rate-limiting request.
- One reuses middleware, one installs a package, and one writes a custom counter.
- Stable criteria still require the same behavior: limit after five failures, return `429`, reset after ten minutes, and preserve unrelated auth behavior.
- Tests and review decide acceptability; identical prompting cannot guarantee identical code.

## Best Practices

- Make behavior deterministic through acceptance criteria, tests, types, and linters.
- Use variation deliberately to explore designs, then converge through evidence.
- Reset the repository and environment before comparative runs.
- Use the same rubric for every attempt.
- Re-evaluate workflows after changing model, effort, tools, or instructions.

## Common Mistakes

- Do not try to eliminate all variation with a longer prompt; control outcomes with verification.
- Do not accept the best of several attempts without understanding why others failed.
- Do not compare runs against different repository states.
- Do not treat one passing sample as proof of reliability.
- Do not force identical formatting when only behavior matters.

## Try It

1. Choose a bounded task with at least three objective acceptance criteria.
2. Reset the repository to the same state before every run.
3. Use the same model, prompt, tools, and effort for three independent runs.
4. Save each diff, tool sequence, test result, elapsed time, and review findings.
5. Classify variation as harmless, beneficial, or acceptance-breaking.
6. Add one check for the most important unacceptable variation.

## Expected Result

- A three-run comparison showing what varies and what remains stable.
- Acceptance checks that reject bad outcomes without requiring identical code.
