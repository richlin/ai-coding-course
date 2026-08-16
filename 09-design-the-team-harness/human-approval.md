# Permissions and Human Approval

## What It Means

- Permissions define what data and actions an agent can access.
- Human approval reserves consequential decisions or operations for an accountable person.
- Approval boundaries should depend on impact, reversibility, confidence, and policy.

## Why It Matters

- Autonomous execution can amplify a mistake quickly.
- Clear boundaries let teams delegate routine work without delegating unacceptable risk.

## Concrete Example

- Local notification code and tests run automatically.
- Adding a provider SDK requires dependency approval.
- Changing consent defaults requires product, legal, and security approval.
- Rotating production credentials or enabling a new channel requires an operator to review scope, evidence, and rollback.

## Best Practices

- Grant least privilege and expand access for specific tasks.
- Require approval for destructive, production, financial, legal, or sensitive-data actions.
- Show approvers the proposed action, expected effect, evidence, and rollback.
- Log important approvals and outcomes.
- Define approval policy by impact and reversibility.
- Show exact proposed action and target environment.
- Give approvers relevant tests, risks, and rollback.
- Expire approvals when the action or evidence changes.

## Common Mistakes

- Do not add approval to every minor step; excessive prompts encourage careless approval.
- Do not request approval with vague summaries.
- Do not reuse approval for materially changed commands.
- Do not let the implementing agent approve its own accepted risk.
- Do not treat notification as approval.

## Try It

1. List ten actions from local edit through production rollout.
2. Score impact, reversibility, sensitivity, and confidence.
3. Classify each automatic, notify, approve, or prohibited.
4. Define the evidence and owner required for every approval.
5. Simulate one request and reject it if scope or rollback is unclear.

## Expected Result

- A risk-based approval matrix with named owners.
- Approval requests contain enough evidence for an accountable decision.
