# Dependencies, Ownership, and Integration Order

## What It Means

- A dependency is work or a contract that another task requires before it can complete.
- Ownership identifies who is responsible for decisions, delivery, and verification.
- Integration order determines when independently developed changes can safely combine.

## Why It Matters

- Parallel agents can make incompatible assumptions about shared interfaces.
- Undefined ownership causes duplicated work and unresolved decisions.

## Concrete Example

- Define `NotificationPreference` fields and default semantics before API and UI agents work in parallel.
- Assign the backend owner to schema and endpoint behavior, frontend owner to settings interaction, and integration owner to the full user flow.
- UI work uses a checked-in contract or mock matching it.
- Migration lands before code reads new fields; rollout waits for integration checks.

## Best Practices

- Define shared contracts before parallel implementation begins.
- Assign one owner for each ticket and one owner for integration.
- Make dependency direction visible in the tracker or plan.
- Integrate foundations and high-risk contracts early.
- Record decision owners separately from implementers.
- Use machine-readable contracts when available.
- Keep dependency direction acyclic and visible.
- Name one integration owner for cross-ticket outcomes.

## Common Mistakes

- Do not parallelize work that is still negotiating the same interface.
- Do not assign shared ownership with no final decision-maker.
- Do not let mocks drift from the accepted contract.
- Do not merge consumers before required migration compatibility exists.
- Do not confuse task completion with integrated feature completion.

## Try It

1. Choose a feature with at least three tickets.
2. Draw nodes for contracts, migrations, implementations, and end-to-end checks.
3. Add directional dependency arrows.
4. Assign decision, implementation, and integration owners.
5. Identify safe parallel branches and the earliest integration point.
6. Resolve any cycle or ownerless decision.

## Expected Result

- An acyclic dependency and ownership map.
- Parallel work begins only after shared assumptions become explicit contracts.
