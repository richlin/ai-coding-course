# Repository Rules and Durable Artifacts

The [`AGENTS.md` introduction](../01-ai-coding-system/ground-rules.md) explains how a harness loads a repository's standing brief. This chapter places that brief alongside the other durable artifacts an agent needs while it works.

## What It Means

- Repository rules, often stored in `AGENTS.md` or a harness-specific equivalent, describe project-specific commands, conventions, boundaries, and workflows.
- Durable artifacts include specs, tests, tickets, architecture decisions, and handoffs stored outside a chat.
- These artifacts give future humans and agents a shared source of truth.

## Why It Matters

- Agents otherwise rediscover conventions or apply generic patterns that do not fit the project.
- Durable decisions survive model changes, session resets, and team handoffs.

## Concrete Example

- **Project rule:** “Use `pnpm`; run `pnpm test --filter <package>` after a package edit; database writes go through services; do not edit generated clients.”
- **Spec:** “CSV export preserves current filters and escapes spreadsheet formulas.”
- **Test:** Proves another organization cannot export these orders.
- **ADR:** Explains why exports are generated synchronously below 10,000 rows.
- Each fact lives where the team expects to maintain it.

## Best Practices

- Keep rules short, current, and specific to the repository.
- Store facts near the code or workflow they govern.
- Prefer executable checks over prose when a standard can be automated.
- Put rules under version control and assign ownership.
- Include exact project commands and unusual boundaries.
- Link deeper documentation rather than duplicating it.
- Review rules after tooling or architecture changes.

## Common Mistakes

- Do not turn repository instructions into a large handbook of obvious or conflicting advice.
- Do not store task-specific requirements as permanent rules.
- Do not document a standard that CI enforces differently.
- Do not rely on a private user rule for team-critical behavior.
- Do not leave generated-file or migration boundaries implicit.

## Exercise

1. List ten facts an agent needs for a normal repository change.
2. Classify each as rule, spec, test, ADR/documentation, ticket, or temporary context.
3. Locate its current source and check for duplicates or conflicts.
4. Move or rewrite one fact that is stored at the wrong scope.
5. Run any executable check associated with that fact.
6. Ask a fresh agent where it would look for the same information.

Complete the exercise when:

- A source-of-truth map with no critical convention dependent on private knowledge.
- At least one rule is shortened, automated, relocated, or removed.
