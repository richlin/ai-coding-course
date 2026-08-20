# Prune Stale or Conflicting Instructions

## What It Means

- Instruction pruning removes guidance that is outdated, duplicated, unused, or contradictory.
- Conflicts occur when two rules prescribe different actions for the same situation.
- A smaller instruction set makes important constraints easier to follow.

## Why It Matters

- Agents cannot reliably resolve hidden priority conflicts.
- Old instructions preserve practices that the codebase may have already replaced.

## Concrete Example

- A user rule says “always use npm,” while the repository rule says “use pnpm.”
- An old project rule requires full tests after every edit, while the current workflow requires focused tests per increment and full CI before merge.
- Keep the repository package-manager rule, narrow the user preference, and update the test rule to match executable workflow.

## Best Practices

- Review instructions after major workflow or architecture changes.
- Merge duplicates and state explicit precedence when overlap is necessary.
- Remove advice that does not change observable behavior.
- Keep executable enforcement synchronized with prose.
- Assign one source of truth for each convention.
- Review instructions after tooling and architecture changes.
- Test whether removing a rule changes behavior.
- Prefer specific, observable guidance over broad quality slogans.

## Common Mistakes

- Do not keep adding exceptions to a weak rule when the rule should be rewritten or deleted.
- Do not retain rules because they took effort to write.
- Do not merge contradictory wording without deciding precedence.
- Do not leave obsolete command examples.
- Do not prune rationale still needed for human judgment.

## Exercise

1. Collect all instruction sources affecting one repository.
2. Group statements by topic and highlight conflicts or duplicates.
3. Mark each keep, automate, merge, update, move, or remove.
4. Apply one cleanup and run a representative task before and after it.
5. Confirm required behavior remains and context becomes smaller.

Complete the exercise when:

- A shorter instruction set with explicit precedence and current commands.
- Removed guidance causes no loss of required behavior.
