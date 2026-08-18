# Write an Effective Task Prompt

By the end of this lesson, you will be able to give a coding agent enough direction to start useful work without trying to describe every implementation detail yourself.

## A Prompt Defines the Current Job

A task prompt is the instruction for one run of work. It tells the agent what outcome you want, why it matters, and which boundaries apply now. The harness combines that prompt with project rules, repository context, tool results, and later feedback.

This makes a task prompt different from a project rule. “Add an export button to the orders page” belongs in the prompt. “Use `pnpm` and ask before adding a dependency” belongs in the repository's standing instructions because it applies to many tasks.

A useful starting prompt contains four things:

```text
outcome + relevant context + constraints + evidence of completion
```

For example:

```text
Add CSV export to the existing orders page so support staff can download
the currently filtered results. Preserve the page's active filters and
authorization checks. Do not add a dependency. Add focused tests and run
the repository checks that cover the changed code.
```

The agent can now inspect the repository to find the page, filter state, authorization path, CSV patterns, and available checks. The prompt establishes the destination without guessing those coordinates.

## State Outcomes Before Implementation Ideas

Tell the agent what must become true before prescribing how to code it. An implementation idea can be useful evidence, but it may also be based on an incomplete view of the repository.

Compare these prompts:

> Add a `CsvExportService`, use library X, and call it from a new `/api/export` route.

> Let an authorized support user export the orders visible under the page's current filters. Reuse existing project patterns and do not add a dependency.

The first prompt commits to an architecture before exploration. The second gives the agent room to discover that the repository already has an export helper or that downloads use background jobs. If a specific route or library is genuinely required, state the reason as a constraint.

## Include Context the Repository Cannot Reveal

An agent can search code, but it cannot infer an unrecorded product decision. Put business intent, recent incidents, external deadlines, rejected choices, and non-obvious limits in the prompt or link to their source.

Do not paste a large file inventory or explain code the agent can inspect directly. Point it toward a useful starting location when you know one, then let exploration establish the actual change surface.

## Make Completion Observable

“Make it robust” gives the agent no finish line. Describe behavior that a reviewer or check can observe:

- The export contains only orders visible under the active filters.
- A user without export permission receives the existing authorization response.
- CSV cells that begin with spreadsheet formula characters are escaped.
- Focused tests pass, followed by the repository's required checks.

These conditions are lightweight acceptance criteria. For a larger or uncertain change, move them into a specification and ask the agent to plan before implementation.

## Adjust the Prompt to the Size of the Work

A one-file copy change may need one sentence. A cross-service feature needs more context, explicit non-goals, acceptance criteria, and probably a separate specification. Prompt length should follow uncertainty and risk, not a fixed template.

When the agent can safely discover a missing detail, let it. When different answers would produce materially different products or security boundaries, resolve the decision before implementation.

## Exercise

1. Choose a real task you could give an agent this week.
2. Write its outcome in one sentence without naming an implementation.
3. Add one piece of context the repository cannot reveal.
4. Add the constraints that would change the solution.
5. Add two or three observable completion conditions.
6. Remove file lists, generic quality words, and implementation guesses the agent can replace through exploration.

Complete the exercise when another engineer can read the prompt and agree on what success looks like without being forced into an unverified design.
