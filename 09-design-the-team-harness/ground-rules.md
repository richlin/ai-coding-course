# Ground Rules and Specifications

## What It Means

- Ground rules define stable project conventions, safety boundaries, and required workflows.
- Specifications define the desired outcome and constraints for a particular change.
- Rules answer “how we work here”; specs answer “what this task must achieve.”

## Why It Matters

- Shared rules reduce inconsistent behavior across engineers, models, and sessions.
- Separating stable conventions from task requirements keeps both easier to maintain.

## Concrete Example

- **Project rule:** Notification changes must preserve tenant isolation, use the existing provider adapter, and run `pnpm test --filter notifications`.
- **Task spec:** Add a user-controlled marketing-email preference with defined default and migration behavior.
- The rule applies to future notification work; the spec applies only to this feature.
- CI enforces tests while prose explains architecture and risk.

## Best Practices

- Keep project rules concise and specific to the repository.
- Put task-specific details in specs or tickets.
- Automate objective rules with tests, linters, hooks, or CI.
- Define which instruction wins when scopes overlap.
- Keep stable conventions separate from task outcomes.
- Link executable enforcement beside the rule.
- Assign owners and review rules after architecture changes.
- Include unusual commands and safety boundaries, not obvious coding advice.

## Common Mistakes

- Do not copy every past task instruction into permanent project rules.
- Do not place changing product requirements in repository rules.
- Do not duplicate CI behavior with conflicting prose.
- Do not leave precedence between user, project, and task instructions ambiguous.
- Do not keep rules with no observable effect.

## Exercise

1. Select one project instruction file and one active spec.
2. Label each statement stable convention, task requirement, executable standard, or unnecessary.
3. Move misplaced statements and link relevant checks.
4. Identify conflicts and state precedence.
5. Test a representative agent task with the cleaned inputs.

Complete the exercise when:

- Short project rules plus a bounded task spec with no duplicated ownership.
- The agent follows shared standards and task criteria without repeated prompting.
