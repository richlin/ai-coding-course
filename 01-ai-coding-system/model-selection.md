# Model Selection

## What a Model Is

Names such as "Claude Sonnet" and "GPT-5" identify model families. A versioned name identifies a particular release within a family. A model takes tokens in and predicts tokens out, once per request to the model provider. On their own, models cannot do anything agentic. They cannot read a file, run a command, browse the web, or remember what happened yesterday.

Everything that feels like an agent working comes from the harness around the model. The harness gives the model instructions and context, offers it tools, runs the tools it chooses, returns the results, and calls the model again. Reading a repository, editing three files, running the tests, noticing a failure, and fixing it may involve dozens of model requests stitched together by the harness.

That distinction matters when something goes wrong. "The model is bad at this" is a specific claim. The same model may perform very differently when it has better instructions, the right files in context, useful tools, or a test result it can react to.

Model choice still matters. Better context does not turn a lightweight model into a top-tier reasoning model. It just prevents the harness from wasting whatever capability the model has.

## Choosing a Model

Model providers usually ship a family of models rather than one model for every job. The largest tier is generally the most capable, but also slower and more expensive. Smaller tiers trade some reasoning ability for speed and price. The exact names change; the tradeoff does not.

The tempting default is to use the strongest model for everything. That works, but it is a little like assigning a staff engineer to every variable rename. At the other extreme, always choosing the cheapest model creates work that looks inexpensive until someone has to review and repair it three times.

Anthropic's familiar Haiku, Sonnet, and Opus tiers are a useful example of this tradeoff. Pick the tier based on the hard part of the task:

- **Claude Haiku is the lightweight model:** Good for search, extraction, formatting, boilerplate, and small edits that follow an obvious pattern. These tasks have narrow boundaries and cheap checks.
- **Claude Sonnet is the general coding model:** A good default for normal feature work: reading several files, following existing conventions, implementing a clear requirement, and running focused tests.
- **Claude Opus is the heavyweight reasoning model:** Worth using for architecture, unfamiliar debugging, migrations, security-sensitive work, and changes that cross several systems. These tasks require judgment, not just code generation.
- **Deterministic tool instead of a model:** Use a formatter to format, a compiler to type-check, a test runner to test, and a calculator to calculate. A model does not add value merely by sitting in the middle.

### What Makes a Task Hard for a Model?

Renaming twenty fields may be easy; changing one authorization condition may require understanding the whole security model.

A task usually needs a stronger model when several of these are true:

- The request is ambiguous, and a reasonable person could interpret it more than one way.
- The answer depends on behavior spread across many files or services.
- There are several plausible solutions with different long-term consequences.
- The model has to keep many constraints in mind at the same time.
- There is no quick test that proves the answer is right.
- A mistake could expose data, corrupt state, break compatibility, or cause an outage.
- The codebase or domain is unfamiliar enough that the obvious answer may be wrong.

The opposite also holds. A bounded change with a good test suite is friendly to smaller models because the harness can give them fast, objective feedback. If the model misses something, the test points directly at the problem.

### You Can Switch Models Mid-Task

One session does not have to use one model from beginning to end. A harness may let you use a heavyweight model to understand the problem and write the plan, then hand mechanical edits to a faster model. If the tests uncover a subtle failure, the harness can route that debugging step back to the stronger model.

This works especially well when the handoff is concrete. "Implement steps 2–5 from this reviewed plan and run these tests" is a much easier lightweight-model task than "figure out how to migrate this service."

Switching models is less useful when every step depends on a large, fragile mental model of the system. In that case, the time spent rebuilding context can erase the savings.

## Model Choice Changes Latency

A lightweight model usually returns each response faster. That makes it a good fit for search, formatting, and a tight edit-test loop. A heavyweight model takes longer per response, so using one for every routine step can make an interactive session drag.

Per-response speed is not the whole story. A lightweight model can still be the slow choice if it needs three repair passes. A heavyweight model can finish the task sooner when its first implementation survives tests and review.

Choose the least expensive model that has been reliable on similar work. Optimize for the shortest dependable path to an accepted result, not the fastest first token.
