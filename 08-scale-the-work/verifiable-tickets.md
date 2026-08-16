# Splitting Features into Verifiable Tickets

## What It Means

- A verifiable ticket delivers one coherent outcome with explicit acceptance criteria.
- It is small enough to implement, review, and check in one focused unit of work.
- Vertical tickets usually include the minimal layers required for one user-visible behavior.

## Why It Matters

- Small tickets limit context, merge, and rollback risk.
- Independent evidence allows the team to integrate with confidence.

## Concrete Example

- Weak tickets: “Create all database models,” “Build APIs,” and “Make UI.” None proves user behavior alone.
- Better first ticket: “A signed-in user can disable marketing email; the persisted choice prevents the next marketing send.”
- Its slice includes minimal schema, endpoint, delivery check, UI control, and focused tests.
- Push notification support remains a separate outcome.

## Best Practices

- Write tickets around outcomes rather than file types or team boundaries.
- Include dependencies, non-goals, likely ownership, and verification.
- Split tickets that contain multiple unrelated “and” clauses.
- Include one observable user or system outcome.
- Keep shared groundwork only when a slice truly requires it.
- Name non-goals to protect boundaries.
- Make each ticket safe to review and revert.

## Common Mistakes

- Do not create horizontal tickets such as “build all models” when no behavior can be verified until much later.
- Do not create a ticket for every file.
- Do not hide several channels or user roles in one ticket.
- Do not omit integration behavior from criteria.
- Do not size tickets solely by estimated coding time.

## Try It

1. Select a feature currently split by technical layer.
2. Identify two or three user-visible outcomes.
3. Rewrite tickets vertically around those outcomes.
4. Add criteria, non-goals, dependencies, and verification commands.
5. Confirm each ticket leaves the system usable.
6. Ask a reviewer whether any ticket can be split without losing a coherent outcome.

## Expected Result

- Vertical tickets independently demonstrating useful behavior.
- No ticket waits for all other layers before it can be verified.
