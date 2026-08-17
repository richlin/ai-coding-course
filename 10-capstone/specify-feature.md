# Specify a Realistic Feature

## What It Means

- Select a feature that is meaningful enough to require judgment but small enough to complete and verify.
- Produce a spec with intent, assumptions, constraints, non-goals, acceptance criteria, and open questions.
- Identify the executable goal commands before implementation.

## Why It Matters

- The capstone tests whether you can turn an ambiguous request into controlled engineering work.
- A realistic feature exposes tradeoffs that isolated concept exercises cannot.

## Concrete Example

- **Feature:** A signed-in user can permanently delete their own account from settings.
- **Intent:** Meet user-control and retention obligations without support intervention.
- **Constraints:** Re-authenticate, prevent cross-user deletion, preserve required audit records, remove sessions, and provide clear irreversible-action confirmation.
- **Non-goals:** Administrator deletion, account suspension, or organization deletion.
- **Criteria:** Correct user data is removed or retained per policy, unauthorized attempts fail, active sessions end, and repeated requests are safe.

## Best Practices

- Choose an existing repository with working tests or checks.
- Keep the feature to one coherent user outcome.
- Review the spec before asking an agent to plan or edit.
- Choose a feature with real boundaries but limited surface area.
- Get policy and product decisions from accountable owners.
- Include failure, authorization, and rollback or irreversibility behavior.
- Pair every criterion with a verification method.

## Common Mistakes

- Do not choose a feature so large that decomposition becomes the entire capstone.
- Do not let the agent invent retention or legal policy.
- Do not specify only the happy path.
- Do not prescribe architecture before codebase research.
- Do not start while blocking questions remain ownerless.

## Exercise

1. Select a feature touching at least two files and one meaningful boundary.
2. Write context, intent, users, assumptions, constraints, non-goals, examples, criteria, and open questions.
3. Add one happy path, one authorization case, one failure case, and one regression criterion.
4. Attach a check to every criterion.
5. Ask a peer or fresh agent to plan from the spec and list ambiguities.
6. Resolve blocking questions with the correct owner and revise the spec.

Complete the exercise when:

- A reviewable feature spec with no silent policy decision.
- Every acceptance criterion has observable evidence and an owner where judgment remains.
