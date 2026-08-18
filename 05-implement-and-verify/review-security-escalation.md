# Reviewing Changes, Security Boundaries, and Escalation

## What It Means

- Review checks correctness, regression risk, maintainability, security, and scope.
- Security boundaries protect credentials, user input, sensitive data, dependencies, and external systems.
- Escalation returns a decision to a human when impact is high or evidence is insufficient.

## Why It Matters

- Fluent code can still contain authorization gaps, unsafe defaults, or hidden behavior changes.
- Agents should not make irreversible or policy-sensitive decisions alone.

## Concrete Example

- Review finds that CSV values beginning with `=` can execute formulas, and that the endpoint forgot organization scoping.
- The formula issue can be fixed and tested locally.
- The correct retention and audit policy for exports is a product and security decision, so implementation pauses for the accountable owners.
- Approval includes the proposed behavior, evidence, risk, and decision needed rather than a generic “is this okay?”

## Best Practices

- Review the diff and behavior, not only the agent's summary.
- Trace untrusted input to storage, execution, and output boundaries.
- Escalate destructive actions, production access, unclear requirements, and accepted risk.
- State the evidence and decision needed when escalating.
- Review by risk: authorization, data exposure, injection, state changes, then maintainability.
- Trace untrusted data across input, transformation, storage, and output.
- Separate fixable findings from accepted-risk decisions.
- Make escalation ownership and deadline explicit.

## Common Mistakes

- Do not grant broader permissions merely to avoid a focused approval step.
- Do not review only the files the agent mentions in its summary.
- Do not treat validation as authorization.
- Do not let the implementing agent accept security or policy risk.
- Do not escalate without a clear question and supporting evidence.

## Exercise

1. Select an agent-generated diff that handles input, permissions, or data.
2. Compare it with the spec and list changed trust boundaries.
3. Trace one untrusted value and one authorization decision through the code.
4. Record correctness, security, regression, complexity, and scope findings by severity.
5. For each finding, choose fix, test, accept, or escalate and name the owner.
6. Write one escalation containing evidence, options, recommendation, and requested decision.

Complete the exercise when:

- A review report ordered by risk with concrete file or behavior evidence.
- Human-owned decisions are explicit and not silently made by the agent.
