# Codebase Exploration

## What It Means

- Exploration finds the code that controls the requested behavior before editing begins.
- A concrete anchor can be a failing test, error message, route, symbol, UI text, or nearby implementation.
- Searches, call sites, tests, and version history reveal how the system currently works.

## Why It Matters

- The first matching file may only register or forward behavior rather than control it.
- Editing without tracing ownership often creates duplicate logic or fixes the wrong layer.

## Concrete Example

- Start from the “Export CSV” button, then trace its click handler to the API client and route.
- Search the route's query service to find the function that actually applies organization and date filters.
- Inspect a neighboring download endpoint and its tests for response headers and authorization patterns.
- Stop exploring once you can state: “The query service controls rows; the route controls authorization and CSV response; this test is the cheapest discriminator.”

## Best Practices

- Start from the most concrete symptom or named symbol.
- Search broadly once, then read narrowly around the controlling path.
- Inspect a neighboring test or implementation before inventing a new pattern.
- Search symbols and exact UI or error text before reading large directories.
- Distinguish registration and forwarding code from behavior-owning code.
- Use references or call sites to confirm ownership.
- State a falsifiable hypothesis before the first edit.

## Common Mistakes

- Do not map the entire repository before making a small local change.
- Do not edit the first file containing the search term.
- Do not rely on folder names as proof of runtime ownership.
- Do not read implementation without checking neighboring tests.
- Do not keep exploring after one small edit and check can answer the remaining question.

## Exercise

1. Choose a visible behavior, error, route, or failing test.
2. Search its exact text or symbol and select the closest entry point.
3. Follow calls or references until reaching code that computes, validates, or mutates the behavior.
4. Find one neighboring implementation and one relevant test.
5. Write a one-sentence hypothesis naming the controlling code and expected check.
6. Confirm it with the cheapest read-only or executable action.

Complete the exercise when:

- A short path from symptom to behavior owner to verifying test.
- Enough evidence to justify one focused edit without a repository-wide map.
