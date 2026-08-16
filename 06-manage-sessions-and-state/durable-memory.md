# Durable Artifacts and Auto-Memory

## What It Means

- Durable artifacts are project records such as code, tests, specs, tickets, and decision documents.
- Auto-memory stores selected facts across sessions, often based on harness behavior.
- Project artifacts should hold shared truth; memory should hold concise preferences or recurring context.

## Why It Matters

- Important decisions must remain visible, reviewable, and correctable by the team.
- Hidden or outdated memory can influence work without engineers knowing why.

## Concrete Example

- **Test:** CSV formulas must be escaped.
- **ADR:** Large exports use queued jobs because synchronous requests exceed platform limits.
- **Ticket:** Endpoint work is complete; UI integration is next.
- **Project rule:** Use `pnpm` and do not edit generated clients.
- **User memory:** The engineer prefers concise progress updates. Security requirements do not belong in private memory.

## Best Practices

- Store requirements and technical decisions in the repository or issue tracker.
- Store only stable, useful, non-sensitive facts in agent memory.
- Review and remove memory that becomes inaccurate.
- Store facts where their owners naturally maintain them.
- Keep memory short, stable, and non-sensitive.
- Make team-critical information visible in the repository or tracker.
- Define expiration or review for facts likely to change.

## Common Mistakes

- Do not use auto-memory as a replacement for specifications, tests, or project documentation.
- Do not store secrets, customer data, or temporary failures in memory.
- Do not duplicate one fact across several stores without a source of truth.
- Do not let private preference override project rules.
- Do not assume automatically captured memory is accurate forever.

## Try It

1. Collect ten facts from an active project and session.
2. Classify each as code, test, spec, ticket, ADR/docs, project rule, user memory, or temporary context.
3. Name the owner and expected lifetime of each durable fact.
4. Move one misplaced fact to its proper source of truth.
5. Delete or correct one stale memory or duplicate.

## Expected Result

- A state-location table with ownership and lifetime.
- No critical shared behavior depends only on chat or private memory.
