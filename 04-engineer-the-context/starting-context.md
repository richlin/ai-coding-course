# Starting Context

## What It Means

- Starting context is the information an agent receives before beginning a task.
- It usually includes the goal, constraints, repository instructions, current state, relevant files, and known failures.
- Good starting context is sufficient for the first decision without trying to explain the entire system.

## Why It Matters

- Early assumptions shape every later search, plan, and edit.
- Missing constraints create rework, while excessive context hides important facts.

## Concrete Example

- **Goal:** Export currently filtered orders as a safe CSV.
- **Include:** Approved spec, export route or nearest analogous route, filter query builder, authorization middleware, one neighboring endpoint test, and repository commands.
- **Do not include yet:** Every order-related file, unrelated UI screenshots, old rejected proposals, or full CI logs.
- **First question:** Which existing code owns filtered order retrieval and permission checks?
- This gives the agent enough to search intelligently without prescribing an unverified design.

## Best Practices

- Start with the task, definition of done, and current evidence.
- Include repository rules and the nearest relevant code or test.
- Let the agent search outward as new questions arise.
- State the current repository and branch state.
- Include exact acceptance criteria and the first verification command.
- Label assumptions and known failures.
- Prefer links and paths when tools can retrieve the content.

## Common Mistakes

- Do not paste the whole repository or a long conversation when a focused brief and file references are enough.
- Do not omit project instructions and then correct generic conventions later.
- Do not present an outdated plan as current state.
- Do not include a proposed solution without the outcome it must satisfy.
- Do not ask the agent to “explore” without a concrete anchor or question.

## Try It

1. Choose a task that has a named behavior or failing check.
2. Write no more than ten bullets covering goal, criteria, constraints, current state, anchor, relevant artifacts, known evidence, and first check.
3. Label each bullet as fact, assumption, or question.
4. Remove any bullet that cannot affect the first decision.
5. Give the brief to a fresh agent and ask for its first hypothesis and three files to inspect.
6. Add context only if a missing fact blocks that decision.

## Expected Result

- A brief short enough to scan in one minute.
- A fresh agent identifies a plausible controlling path without requesting a repository dump.
