# Handoffs Between Sessions, Tools, Repositories, and People

## What It Means

- A handoff is a portable record that lets another agent or person continue the work.
- It includes the objective, current state, decisions, evidence, changed files, unresolved questions, and next steps.
- Handoffs are useful when changing harnesses, repositories, owners, or branches of work.

## Why It Matters

- The receiver cannot rely on hidden conversation history.
- A good handoff prevents repeated investigation and accidental reversal of decisions.

## Concrete Example

- A handoff states: export endpoint complete; formula escaping and authorization tests pass; UI remains; files changed; exact commands run; one open product question about filename; next action is inspect the existing download-button pattern.
- It links the spec and ticket rather than copying them.
- A fresh receiver can continue without knowing how many failed attempts preceded the final design.

## Best Practices

- Write for a reader with repository access but no prior conversation.
- Separate verified facts from assumptions and recommendations.
- Include exact checks already run and their results.
- Link durable artifacts instead of copying large content.
- Lead with current state and next action.
- Include exact failures that remain unresolved.
- Separate verified facts, decisions, assumptions, and recommendations.
- Update the handoff if work continues after it is written.

## Common Mistakes

- Do not write a chronological conversation summary; organize information for the next decision.
- Do not omit changed files or uncommitted work.
- Do not say “tests pass” without commands and scope.
- Do not hide blockers or risk to make progress look cleaner.
- Do not make the receiver rediscover links already known.

## Try It

1. Pause a task after one verified increment.
2. Write sections for objective, current state, decisions, changed files, checks, unresolved issues, and next action.
3. Link specs, tickets, diffs, and decision records.
4. Give the handoff to a fresh agent with repository access.
5. Ask it to identify missing information and propose the next check.
6. Revise only where the receiver is wrong or blocked.

## Expected Result

- A portable handoff that enables a correct next action.
- The receiver does not need the original chat transcript.
