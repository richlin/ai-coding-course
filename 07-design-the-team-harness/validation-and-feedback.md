# Validation, Observability, and Feedback

## What It Means

- Validation checks whether outputs satisfy predefined goals and constraints.
- Observability exposes actions, tool results, failures, costs, and runtime outcomes.
- Feedback uses those signals to choose the next action or improve the harness.

## Why It Matters

- A team cannot improve agent workflows it cannot observe or evaluate.
- Fast generation without feedback can move quickly in the wrong direction.

## Concrete Example

- Validate notification preference behavior with tests and CI.
- Observe agent tool failures, retries, review findings, usage cost, and time to verified completion.
- After rollout, observe delivery attempts, provider errors, unsubscribe events, and preference violations.
- A repeated authorization review finding becomes a test or skill update.

## Best Practices

- Define success signals before enabling a workflow.
- Capture tool failures, verification results, approvals, and relevant cost or latency.
- Review failed and successful tasks for patterns.
- Convert recurring failures into tests, controls, or clearer boundaries.
- Tie every signal to a decision or owner.
- Capture baseline before changing the harness.
- Separate workflow quality from product runtime quality.
- Review successful outliers as well as failures.

## Common Mistakes

- Do not collect large volumes of logs without decisions they are meant to support.
- Do not measure output volume as productivity.
- Do not optimize token cost while ignoring correction time.
- Do not collect sensitive prompts or code without policy and controls.
- Do not add a metric with no threshold or response.

## Exercise

1. Choose one recurring agent workflow.
2. Define success, failure, cost, latency, review, and runtime signals.
3. Name source, owner, threshold, and response for each.
4. Capture a baseline over representative tasks.
5. Change one harness control and compare outcomes.
6. Automate one low-risk response to a clear signal.

Complete the exercise when:

- A small signal-to-decision table rather than a log wish list.
- Evidence that one harness change improves or fails to improve outcomes.
