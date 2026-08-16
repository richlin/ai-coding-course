# Tools and Integrations

## What It Means

- Tools let agents read, search, edit, test, browse, and interact with external systems.
- Integrations connect the harness to repositories, issue trackers, documentation, CI, and other services.
- Tool design includes inputs, outputs, permissions, error handling, and observability.

## Why It Matters

- Reliable tools ground agents in real state and make actions verifiable.
- Every external integration adds capability, failure modes, and security exposure.

## Concrete Example

- File search and reads inspect notification code.
- A structured issue tool reads task state; a docs tool retrieves provider references.
- Local test tools verify behavior; CI reports broader checks.
- Production deployment and provider configuration are write integrations requiring explicit approval and audit.

## Best Practices

- Add a tool only for a clear workflow need.
- Prefer structured inputs and outputs over free-form command construction.
- Expose useful failures so agents can recover safely.
- Restrict write access and sensitive data by default.
- Prefer typed, narrow operations over unrestricted shell access.
- Return actionable errors and stable identifiers.
- Separate read and write capabilities.
- Log consequential external actions without exposing secrets.

## Common Mistakes

- Do not add many overlapping tools that make action selection ambiguous.
- Do not expose production writes for local implementation tasks.
- Do not return huge unstructured payloads when fields can be selected.
- Do not hide tool failures behind generic messages.
- Do not add an integration without ownership and credential rotation.

## Try It

1. Inventory every tool available for one workflow.
2. Record purpose, input, output, data reached, permission level, owner, and failure signal.
3. Remove overlap or define a preferred tool.
4. Separate read from write operations and add approvals where needed.
5. Run one success and one controlled failure case per critical tool.

## Expected Result

- A minimal tool catalog with clear permissions and diagnostics.
- High-impact writes require explicit evidence and approval.
