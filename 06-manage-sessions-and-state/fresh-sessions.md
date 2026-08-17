# Fresh Sessions and Clearing Context

## What It Means

- A fresh session starts with no active conversation history.
- Clearing removes the current context and requires you to provide a new starting brief.
- Fresh sessions are useful when the task changes or the existing reasoning has become unreliable.

## Why It Matters

- Old assumptions can anchor an agent even after the direction changes.
- A clean session lets you select only the evidence relevant to the next phase.

## Concrete Example

- Research for export security is complete, but the session has three abandoned designs and repeated confusion.
- Save the approved design, current diff, focused test results, and next task in a handoff.
- Start a fresh implementation session that reads those artifacts and repository rules.
- Use a separate fresh session for independent review so it is not anchored by implementation discussion.

## Best Practices

- Save work, decisions, failures, and next steps before clearing.
- Start the new session from durable artifacts rather than memory.
- Use a new session for a distinct task, independent review, or recovery from deep confusion.
- Start fresh at clear phase or ownership boundaries.
- Preserve verified state before clearing.
- Give the new session a concrete first action.
- Keep independent review context separate from implementation rationale initially.

## Common Mistakes

- Do not clear first and reconstruct important state afterward from memory.
- Do not restart merely to avoid resolving an unclear requirement.
- Do not paste the entire old transcript into the new session.
- Do not omit the current branch, diff, or failed check.
- Do not assume “fresh” means free of repository instructions or durable decisions.

## Exercise

1. Choose an active task at a phase boundary or with degraded reasoning.
2. Save code and write goal, constraints, decisions, evidence, open questions, and next action.
3. Clear or open a fresh session.
4. Provide only the brief and durable artifact links.
5. Ask it to restate state and run one read-only check before editing.
6. Compare its understanding with the saved state.

Complete the exercise when:

- The fresh session resumes from verified state without replaying history.
- Any missing information is identified before code changes.
