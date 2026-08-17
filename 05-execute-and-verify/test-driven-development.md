# Test-Driven Development

## What It Means

- Test-driven development follows a short cycle: write a failing test, make it pass, then simplify safely.
- The failing test proves the test can detect the missing or broken behavior.
- Tests become executable acceptance criteria and regression protection.

## Why It Matters

- Agents can generate implementations that look correct but miss edge cases.
- A focused failing test gives the agent a precise target and stopping condition.

## Concrete Example

- **Red:** Add a test expecting input `=IMPORTXML(...)` to become a literal CSV value; observe the unsafe output fail.
- **Green:** Prefix dangerous values using the project's chosen escaping rule and run only the helper tests.
- **Refactor:** Extract a clearly named predicate if it improves readability, then keep all tests green.
- Add endpoint-level coverage only after the unit behavior is established.

## Best Practices

- Start with one behavior and the cheapest appropriate test level.
- Observe the test fail for the expected reason.
- Write only enough code to pass, then improve clarity while keeping it green.
- Make the red failure prove the missing behavior, not a broken fixture.
- Test public behavior and meaningful boundaries.
- Keep the cycle short enough to understand each failure.
- Run the test before and after the implementation change.

## Common Mistakes

- Do not write tests after implementation and assume they would have caught the original defect.
- Do not skip observing red because the failure seems obvious.
- Do not test private implementation details when behavior is stable.
- Do not write many tests before making the first one pass.
- Do not change the test merely to accept incorrect implementation output.

## Exercise

1. Select one missing behavior with a small public test surface.
2. Write one test name that states input and expected outcome.
3. Run it and confirm it fails for the intended reason.
4. Ask the agent for the smallest implementation that can pass it.
5. Run the focused test and inspect the diff.
6. Refactor only if clarity improves, then rerun the same test and relevant suite.

Complete the exercise when:

- Captured red and green outputs showing the test detects the behavior change.
- A focused implementation with regression protection, not a test tailored to existing code.
