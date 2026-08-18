# Intent, Assumptions, Constraints, and Non-Goals

## What It Means

- **Intent** explains the user or business outcome the work should produce.
- **Assumptions** are beliefs treated as true until evidence confirms or rejects them.
- **Constraints** limit acceptable solutions, such as compatibility, security, or scope.
- **Non-goals** state what the task deliberately will not solve.

## Why It Matters

- Agents fill gaps when requirements are ambiguous, often differently from the requester.
- Clear boundaries prevent scope drift and unrelated refactoring.

## Concrete Example

- **Request:** “Let users export orders.”
- **Intent:** Finance users can reconcile filtered orders in a spreadsheet.
- **Assumptions:** CSV is acceptable; exports contain at most 10,000 rows; existing authorization rules apply.
- **Constraints:** Preserve active filters, use UTC timestamps, escape spreadsheet formulas, and add no background-job system.
- **Non-goals:** Scheduled exports, PDF output, and exporting another organization's orders.
- This boundary is specific enough to plan while leaving implementation choices open.

## Best Practices

- Describe the outcome before prescribing implementation details.
- Surface uncertain assumptions so they can be checked early.
- Write non-goals for nearby work that is tempting but unnecessary.
- Verify risky assumptions before planning.
- Distinguish policy constraints from technical preferences.
- Name the user and decision the outcome supports.

## Common Mistakes

- Do not confuse implementation preferences with the actual outcome or constraint.
- Do not hide an unresolved product decision inside an assumption.
- Do not write “out of scope” without naming the tempting adjacent behavior.
- Do not allow the agent to expand a small feature into platform work.

## Exercise

1. Choose a vague request from your backlog.
2. Identify the user and the decision or task the feature supports.
3. Write one intent statement, three assumptions, three constraints, and three non-goals.
4. Mark each assumption as verified or requiring an answer.
5. Ask a peer or fresh agent to name two plausible interpretations still allowed by the boundary.
6. Revise only where those interpretations would cause incorrect work.

Complete the exercise when:

- A one-page task boundary that prevents major scope drift.
- Every unresolved assumption has an owner or next check.
