# Updating, Retaining, or Discarding a Specification

## What It Means

- A spec is a living decision artifact while the work is active.
- It should be updated when accepted requirements, constraints, or decisions change.
- It should be retained when it explains durable behavior or important tradeoffs.
- It can be archived or removed when it is temporary, superseded, and no longer useful.

## Why It Matters

- A stale spec can mislead future agents more than having no spec.
- Durable rationale prevents teams from repeating old debates or reversing deliberate choices.

## Concrete Example

- During CSV export, research shows exports may contain 500,000 rows rather than 10,000.
- The accepted design changes from synchronous download to a queued export with an expiration policy.
- Update the feature spec and acceptance criteria, write an ADR if the queue is a lasting architecture choice, and mark the old synchronous plan superseded.
- After delivery, retain user-visible behavior and rationale but archive temporary investigation notes.

## Best Practices

- Record why a meaningful requirement changed.
- Keep code, tests, tickets, and specs consistent.
- Mark superseded documents clearly and link to the replacement.
- Assign an owner and status to active specs.
- Review specs when code behavior or policy changes.
- Preserve rationale for expensive-to-reverse decisions.
- Let tests and code own details that documentation would merely duplicate.

## Common Mistakes

- Do not preserve every planning note as permanent project truth.
- Do not delete historical rationale when a decision is superseded.
- Do not update code while leaving acceptance criteria knowingly false.
- Do not keep multiple active specs for the same behavior.
- Do not treat a merged spec as automatically correct forever.

## Try It

1. Select a spec for shipped or substantially changed work.
2. Compare its requirements and examples with current tests and behavior.
3. Label every section `current`, `superseded`, `durable rationale`, or `temporary history`.
4. Update current behavior, link superseding decisions, and archive temporary history.
5. Ask the code owner to confirm the source of truth for remaining details.

## Expected Result

- One clearly active specification with no contradictory successor.
- Durable rationale remains discoverable while stale instructions no longer guide agents.
