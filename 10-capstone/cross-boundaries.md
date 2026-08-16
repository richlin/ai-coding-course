# Cross a Session Boundary or Delegate a Task

## What It Means

- Continue the capstone through a fresh session, compaction, handoff, or bounded subagent task.
- Preserve goals, decisions, current state, evidence, and next steps across the boundary.
- The receiving agent should not need hidden conversation history.

## Why It Matters

- Real work often exceeds one conversation or involves several contributors.
- This step tests whether project state is durable and transferable.

## Concrete Example

- After backend account deletion passes focused tests, hand UI work to a fresh session.
- The artifact includes spec link, endpoint contract, changed files, exact passing commands, remaining UI criteria, security warning, and next code anchor.
- Alternatively, delegate a read-only subagent to review retention behavior while the main session keeps implementation ownership.
- The receiver restates state and performs one read-only check before editing.

## Best Practices

- Choose the transition that matches the actual coordination need.
- Save a portable artifact before switching contexts.
- Give delegated work explicit scope, output, and verification.
- Compare the receiver's understanding with the source state before editing.
- Cross at a meaningful phase or ownership boundary.
- Transfer verified state and unresolved risk separately.
- Give delegated tasks explicit non-goals and output format.
- Retain one integration owner.

## Common Mistakes

- Do not transfer only a task title and expect the receiver to reconstruct decisions safely.
- Do not hand off raw conversation history.
- Do not omit uncommitted changes or failed checks.
- Do not delegate a policy decision with no human owner.
- Do not allow parallel agents to edit the same files.

## Try It

1. Choose compact, fresh session, handoff, or subagent for a real capstone boundary.
2. Explain why that strategy fits continuity, recovery, transfer, or isolation.
3. Prepare goal, constraints, decisions, artifacts, changes, checks, risks, and next action.
4. Give the artifact to the receiver without the original conversation.
5. Require a state summary and read-only validation before edits.
6. Record missing or misleading information and revise the artifact.

## Expected Result

- The receiver takes a correct next action without hidden history.
- The transition artifact is portable, concise, and grounded in repository evidence.
