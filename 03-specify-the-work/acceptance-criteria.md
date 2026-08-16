# Acceptance Criteria and Goal Commands

## What It Means

- Acceptance criteria describe observable conditions that must be true when work is complete.
- A goal command is an executable check, such as a focused test, build, or lint command.
- Good criteria cover behavior and important failure cases, not implementation details alone.

## Why It Matters

- The agent needs a stopping condition that is stronger than “the code looks finished.”
- Shared criteria reduce disagreements during review.

## Concrete Example

- **Criterion:** Export contains only orders matching the current date and status filters.
- **Criterion:** A user without `orders:export` receives `403` and no file is generated.
- **Criterion:** Values beginning with `=`, `+`, `-`, or `@` are escaped to prevent spreadsheet formula execution.
- **Goal commands:** `npm test -- orders-export` and `npm run typecheck`.
- “Export works correctly” is not acceptable because it does not define rows, authorization, format, or failure behavior.

## Best Practices

- Write criteria as specific, testable statements.
- Include at least one negative or error case when relevant.
- Pair each criterion with the cheapest check that could disprove it.
- Cover happy path, boundary, authorization, and failure behavior.
- Describe observable behavior without over-specifying private implementation.
- Use exact examples for formats, status codes, and limits.

## Common Mistakes

- Do not use vague criteria such as “works well,” “is robust,” or “looks good.”
- Do not write criteria that only restate implementation tasks.
- Do not omit negative cases for permissions and untrusted input.
- Do not choose a broad full-suite command when a focused check can guide the first increment.

## Try It

1. Choose one bounded feature.
2. Write one happy-path, one boundary, one authorization or error, and one regression criterion.
3. Rewrite each as an observable `Given/When/Then` statement or equivalent precise sentence.
4. Attach the cheapest automated or manual check to each criterion.
5. Ask a fresh agent to identify any term that cannot be measured.
6. Replace vague terms and run any existing goal command.

## Expected Result

- Four criteria that two reviewers would evaluate the same way.
- Every criterion has a named verification method.
