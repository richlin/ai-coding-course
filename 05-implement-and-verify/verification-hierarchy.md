# Tests, Types, Linting, Builds, and Runtime Checks

## What It Means

- **Runtime or behavior checks** show whether users receive the intended outcome.
- **Tests** repeatedly check selected behavior and failure cases.
- **Type checks** catch incompatible values and interfaces before runtime.
- **Linting** enforces selected correctness and style rules.
- **Builds** prove the project can produce its expected artifact.
- **Diff review** reveals unintended scope and changes that automated checks may miss.

## Why It Matters

- Each check detects different classes of failure.
- Passing a weak check does not prove stronger user behavior.

## Concrete Example

- **Unit test:** Dangerous CSV prefixes are escaped while normal values remain unchanged.
- **Endpoint test:** The export enforces organization filters and returns correct headers.
- **Type check:** Serializer and route contracts remain compatible.
- **Lint/build:** Repository standards and production bundling succeed.
- **Runtime check:** Download a sample CSV and inspect literal content.
- **Diff review:** Confirm no authorization or unrelated formatting changes slipped in.

## Best Practices

- Run the narrowest behavior-specific check first.
- Expand to broader tests, types, lint, and build as risk increases.
- Inspect the final diff even when automated checks pass.
- Choose checks based on changed behavior and risk.
- Run focused checks immediately after edits, then broaden.
- Record commands and relevant results for reviewers.
- Include negative and security behavior where applicable.

## Common Mistakes

- Do not treat a successful build or lint run as proof that the feature works.
- Do not run only the broad suite and lose the causal signal of a focused test.
- Do not accept passing tests that never observed the original failure.
- Do not skip runtime behavior for UI, integration, or environment-sensitive changes.
- Do not ignore a suspicious diff because automation passes.

## Exercise

1. Choose one recent change and list its acceptance criteria and risks.
2. Inventory available unit, integration, end-to-end, type, lint, build, runtime, and review checks.
3. Map each check to failures it can and cannot detect.
4. Order checks from cheapest discriminating signal to broadest confidence.
5. Run the sequence and record any criterion with no supporting evidence.
6. Add the smallest missing check.

Complete the exercise when:

- A verification matrix showing why each command or observation exists.
- Every important acceptance criterion is supported by evidence at an appropriate layer.
