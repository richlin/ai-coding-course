# Writing Feature and Bug-Fix Specifications

## What It Means

- A feature spec describes the desired behavior, users, boundaries, and acceptance criteria.
- A bug-fix spec describes current behavior, expected behavior, reproduction steps, and regression protection.
- A useful spec gives enough direction to make decisions without dictating every line of code.

## Why It Matters

- Specifications make hidden assumptions reviewable before code is generated.
- They survive session boundaries and coordinate humans and agents around the same target.

## Concrete Example

- A useful CSV-export spec contains: user problem, current filter behavior, data and permission constraints, CSV rules, non-goals, acceptance criteria, and open questions.
- A useful bug spec says: “Exporting a customer name beginning with `=` creates an executable spreadsheet formula,” includes a sample record, current CSV output, safe expected output, and a regression test requirement.
- Neither spec needs a line-by-line implementation plan before repository research.

## Best Practices

- Include context, goals, non-goals, requirements, acceptance criteria, and open questions.
- For bugs, require a reproducible example before choosing a fix.
- Link relevant code and decisions instead of pasting an entire repository into the spec.
- Keep requirements separate from a proposed design.
- Include examples where formats or edge cases are easy to misunderstand.
- Assign owners to open questions that block implementation.
- Update accepted changes rather than leaving decisions only in comments.

## Common Mistakes

- Do not write a long solution description before confirming the actual problem.
- Do not hide acceptance criteria inside paragraphs.
- Do not include every brainstormed idea as a requirement.
- Do not describe a bug without reproducible input and observed output.
- Do not let the spec become stale after an approved requirement change.

## Try It

1. Select a small feature or reproducible bug.
2. Create sections for context, goal, non-goals, requirements, examples, acceptance criteria, and open questions.
3. Link the nearest code and test anchors.
4. Remove implementation details that are not true constraints.
5. Ask a peer or fresh agent to produce a plan from only the spec and repository.
6. Record and resolve ambiguities before implementation.

## Expected Result

- A spec short enough to review in one sitting and complete enough to plan safely.
- No blocking decision is left for the implementing agent to invent silently.
