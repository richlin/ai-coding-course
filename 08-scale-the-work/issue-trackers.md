# Using Issue Trackers as Durable Task Memory

## What It Means

- An issue tracker stores task goals, ownership, status, dependencies, decisions, and evidence outside agent sessions.
- Tickets act as stable coordination units for humans and agents.
- The tracker describes work state; the repository remains the source of truth for code and tests.

## Why It Matters

- Session history is temporary and difficult for a team to inspect.
- Durable task state prevents duplicate work and unclear ownership.

## Concrete Example

- A parent issue defines notification-preference outcomes and rollout.
- Child tickets cover contract/defaults, email preference end to end, push preference, settings UI, and migration monitoring.
- Each ticket links its spec, owner, branch or PR, dependencies, commands, and current blockers.
- Agents update durable ticket state instead of relying on separate chat histories.

## Best Practices

- Keep each ticket bounded and independently verifiable.
- Update status, decisions, blockers, and links as work changes.
- Link commits, pull requests, tests, and handoffs instead of copying them.
- Use consistent status and dependency fields.
- Keep decisions in the issue or linked decision record.
- Update tickets at handoff and integration boundaries.
- Close only when acceptance evidence is linked.

## Common Mistakes

- Do not use one giant issue as a transcript for an entire project.
- Do not create tickets with no owner or verification.
- Do not let chat contain newer status than the tracker.
- Do not duplicate entire specs in every child ticket.
- Do not mark implementation complete before integration evidence exists.

## Exercise

1. Choose a feature requiring at least three slices.
2. Create a parent issue with outcome, non-goals, global criteria, and risks.
3. Create child tickets with owner, dependencies, local criteria, and verification.
4. Link shared contracts rather than copying them.
5. Ask a fresh agent which ticket is unblocked and why.
6. Correct any ambiguity in status or dependency fields.

Complete the exercise when:

- A tracker where another engineer can identify current state and next work.
- Every completed ticket links reviewable evidence.
