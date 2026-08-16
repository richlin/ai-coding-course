# User-Level Versus Project-Level Configuration

## What It Means

- User-level configuration follows one engineer across projects.
- Project-level configuration is shared with contributors to a specific repository.
- Scope determines who receives an instruction and where it is maintained.

## Why It Matters

- Personal preferences should not silently become team requirements.
- Project conventions must be available to every human and agent working in the repository.

## Concrete Example

- **User scope:** Prefer concise explanations and ask before opening external links.
- **Project scope:** Use `pnpm`, run package-focused tests, and never edit generated clients.
- **Task scope:** Export order CSV with current filters and no new dependency.
- Project correctness must not depend on one engineer's private settings.

## Best Practices

- Put personal communication and editor preferences at user scope.
- Put build commands, architecture constraints, and review standards at project scope.
- Prefer the narrowest scope that reaches everyone who needs the rule.
- Put shared configuration under version control.
- State precedence when scopes can conflict.
- Keep task instructions out of permanent configuration.
- Review private settings for accidental project assumptions.

## Common Mistakes

- Do not depend on one engineer's private configuration for repository correctness.
- Do not impose personal tone preferences on the team.
- Do not store secrets in either scope.
- Do not repeat project rules in every task prompt.
- Do not let a broad user rule override repository-specific constraints.

## Try It

1. Gather ten instructions from user configuration, repository files, and recent prompts.
2. Label each user, project, task, or unnecessary.
3. Identify duplicates and conflicts and choose the authoritative scope.
4. Move one instruction to the correct scope.
5. Test from a fresh session with and without project context.

## Expected Result

- A scoped configuration map with explicit authority.
- Team-critical rules apply to every contributor without private setup.
