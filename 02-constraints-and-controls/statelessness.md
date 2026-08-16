# Statelessness

## What It Means

- An agent usually starts a new session without the working state from previous sessions.
- Important decisions may exist only in conversation unless they are saved externally.
- Built-in memory can help, but it is selective and should not be treated as a complete project record.

## Why It Matters

- Lost decisions cause repeated research, inconsistent implementation, and avoidable mistakes.
- Long tasks cannot depend on one conversation remaining available forever.

## Concrete Example

- Session 1 decides that rate-limit state must use the existing Redis client and that internal health traffic is exempt.
- If those decisions remain only in chat, Session 2 may add an in-memory store and rate-limit health checks.
- A ticket stores acceptance criteria, an ADR stores a lasting architecture decision, tests encode the exemption, and a handoff records current progress.
- The new session continues from those artifacts without the original transcript.

## Best Practices

- Store behavior in tests, current implementation in code, task state in tickets, and durable rationale in decision records.
- Record completed checks with their exact commands and relevant outcomes.
- Write handoffs for the next decision, not as chronological chat summaries.
- Mark assumptions and unresolved questions explicitly.
- Keep the codebase and issue tracker as shared sources of truth.

## Common Mistakes

- Do not assume the next agent will infer the full history from the current code.
- Do not place durable project facts only in private agent memory.
- Do not copy an entire conversation into a ticket; extract decisions and evidence.
- Do not write “tests pass” without naming the command and scope.
- Do not let a stale handoff override newer code, tests, or tickets.

## Try It

1. Pause an active task after at least one decision and one verification command.
2. Record the goal, acceptance criteria, decisions, files changed, checks run, open questions, and next action.
3. Link durable artifacts instead of pasting their contents.
4. Start a fresh session with only repository access and the handoff.
5. Ask the new agent to summarize state and propose the next command before editing.
6. Add only information whose absence caused a wrong or blocked decision.

## Expected Result

- A fresh agent reconstructs the current state and next step without the original conversation.
- Durable facts live in team-visible artifacts rather than only in the handoff.
