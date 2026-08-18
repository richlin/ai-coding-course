# Review and Hand Off the Work

## What It Means

- Review evaluates correctness, scope, maintainability, security, and regression risk.
- A final handoff describes delivered behavior, evidence, decisions, remaining risks, and operational next steps.
- The reviewer should use the spec and actual artifacts rather than the agent's confidence.

## Why It Matters

- Completion claims are not a substitute for independent evaluation.
- A clear handoff lets another engineer maintain, merge, or ship the result.

## Concrete Example

- Independent review traces account ownership, data deletion, retained audit records, session revocation, repeated requests, and UI confirmation.
- Findings are ordered by severity and cite behavior or files.
- The final handoff links the spec, diff, tests, policy decision, rollout considerations, residual risks, and owner.
- “Files changed: service, route, component” is insufficient because it does not explain behavior or evidence.

## Best Practices

- Review the diff by risk and behavior.
- Run or inspect the required verification independently.
- Link the spec, commits, tests, and relevant decisions.
- State unresolved concerns and who owns them.
- Use a fresh reviewer where anchoring risk is high.
- Review against criteria and trust boundaries.
- Re-run critical checks independently.
- Separate resolved findings from accepted residual risk.

## Common Mistakes

- Do not write a handoff that says only what files changed.
- Do not review only the agent's stated scope.
- Do not bury high-severity findings below a summary.
- Do not mark a risk accepted without an accountable human.
- Do not hand off without exact verification state.

## Exercise

1. Give a peer or fresh agent the spec, repository, and diff without implementation chat.
2. Request severity-ordered correctness, security, regression, complexity, and test-gap findings.
3. Reproduce or disprove every material finding.
4. Fix accepted defects and rerun affected checks.
5. Write a final handoff with delivered behavior, decisions, artifacts, checks, rollout, residual risks, and owners.
6. Ask the receiver to state whether it is ready to merge or ship and why.

Complete the exercise when:

- An independent review with evidence and resolved disposition.
- A handoff enabling an accountable engineer to make the next delivery decision.
