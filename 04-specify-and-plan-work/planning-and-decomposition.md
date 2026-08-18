# Plan Mode and Task Decomposition

## What It Means

- Plan mode separates investigation and decision-making from code changes.
- Decomposition divides a large outcome into small, ordered, independently verifiable tasks.
- Dependencies determine which tasks must happen first and which can run in parallel.

## Why It Matters

- Planning exposes unknowns before they become expensive edits.
- Smaller tasks reduce context load, review difficulty, and rollback cost.

## Concrete Example

- **Task 1:** Add and test a CSV-escaping helper using malicious spreadsheet prefixes.
- **Task 2:** Add an authorized export endpoint using existing order filters and the helper.
- **Task 3:** Add the export control to the filtered order view and verify download behavior.
- The dependency order is helper, endpoint, then UI. Each task leaves testable behavior and can be reviewed separately.

## Best Practices

- Inspect relevant code and existing patterns before proposing tasks.
- Give every task acceptance criteria and a verification step.
- Prefer vertical slices that produce working behavior.
- Start implementation once the plan resolves the important unknowns.
- Put high-risk assumptions and contracts early.
- Keep tasks small enough for one focused session.
- Name likely files as navigation help, not as an inflexible mandate.
- Add integration checkpoints after related slices.

## Common Mistakes

- Do not let planning become speculative architecture for requirements that do not exist.
- Do not split solely by frontend, backend, and tests when no task delivers behavior.
- Do not create tickets titled “implement feature.”
- Do not parallelize tasks that are still deciding a shared contract.
- Do not continue planning after the next safe increment and check are clear.

## Exercise

1. Choose a feature touching at least two layers.
2. Draw its dependency graph using components or contracts, not filenames alone.
3. Split it into vertical tasks with one observable outcome each.
4. Add acceptance criteria, dependencies, likely files, and a verification command to every task.
5. Split any task requiring more than one focused session or containing unrelated “and” clauses.
6. Mark safe parallel work and an integration checkpoint.

Complete the exercise when:

- An ordered set of independently verifiable tasks with no hidden dependency.
- Another engineer can select the next unblocked task without asking for the original conversation.
