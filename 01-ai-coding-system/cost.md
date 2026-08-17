# Cost

The model provider's bill is the easiest cost to see, but it is not the whole cost of AI-assisted development. A useful calculation also includes the engineer's time, tool execution, retries, review, and the consequences of accepting a wrong answer.

The cheapest model request is not necessarily the cheapest way to finish a task. A low-cost model that needs repeated correction can consume more tokens and more engineering time than a stronger model that succeeds on the first pass. Likewise, an expensive model is wasteful when a formatter, compiler, test runner, or smaller model can settle the work reliably.

The target is the least expensive setup that reliably handles the task's uncertainty and consequences.

## Direct Model Cost

Providers commonly charge for input and output tokens, sometimes at different rates. Input includes the instructions, conversation history, repository context, and tool results sent with a request. Output can include both the visible answer and provider-specific reasoning tokens that are not shown to the user.

Two controls influence that bill:

- [Model selection](model-selection.md) changes the price and capability of each request.
- [Reasoning effort](effort.md) can increase the internal reasoning performed by models that support it, which can increase output-token usage even when the visible answer stays short.

The harness also affects cost. An agentic task may involve many model requests as the harness reads files, runs tools, returns results, and asks the model what to do next. Large repeated context and unnecessary iterations can matter more than the price of one response.

## Time Is Part of the Cost

Latency is often measured as time to the first token or time until one response finishes. For coding work, the more useful measure is time to an accepted result: the point when the change has passed the required checks and a reviewer is willing to keep it.

That end-to-end time has several parts:

- The selected model and effort level affect how long each model request takes.
- Repository searches, builds, tests, and other tools add execution time.
- Sequential dependencies force some steps to wait for earlier results.
- Failed attempts add correction, rerun, and review cycles.
- Slow or unclear output consumes human attention even after the model stops generating.

Run independent searches or checks in parallel when the harness supports it, but keep dependent steps in order. A test that relies on generated code cannot start before the code exists. Skipping that dependency may look faster while producing evidence about the wrong state.

Define the stopping point before starting. If "done" means a focused test passes, run that test and stop. If it means a migration plan has survived security and rollback review, a quick draft is not yet a result. Without a stopping rule, an agent can keep polishing or exploring long after the useful work is complete.

## The Expensive Part Is Often the Loop

One imperfect response is usually cheap. Repeating an unreliable loop is expensive:

1. The model produces a plausible change.
2. An engineer discovers that it missed a constraint.
3. More context and corrections are sent.
4. The model revises the change.
5. Tests or review expose a different problem.

Each pass consumes model usage and human attention. Reduce this cost by stating acceptance criteria early, giving the model the relevant context, using deterministic checks, and escalating to a stronger model or higher effort when the failure actually requires more reasoning.

Do not escalate blindly. More capability cannot reveal a file that was never provided, repair a broken tool, or decide an unstated requirement. Fixing the source of the failure is usually cheaper than paying for a more elaborate guess.

## Include the Cost of Being Wrong

Cost grows with consequence. A weak draft of internal documentation is easy to edit. A subtle authorization bug, irreversible data migration, or incompatible public API can consume days of recovery work and harm users.

For high-consequence tasks, spend more before accepting the result: use a stronger model when warranted, allow enough reasoning effort, run broader checks, and require human review. This can raise the immediate token bill and still reduce total cost.

The size of the diff is a poor proxy for risk. Renaming a hundred private variables may be cheap and reversible. Changing one boolean in an access-control path may deserve the most careful workflow available.

## A Practical Default

Start with a capable general coding model and medium effort for ordinary implementation. Then route based on evidence:

- Use a smaller, faster model or low effort for bounded, reversible work with cheap checks.
- Use a stronger model or higher effort when the task is ambiguous, cross-system, difficult to verify, or costly to get wrong.
- Use deterministic tools whenever they can answer the question directly.
- Change the context, specification, tools, or permissions when those are the actual bottleneck.
- Measure the full path to an accepted result, including retries and review, rather than optimizing one request in isolation.

The best setup is not always the fastest response, the lowest token price, or the highest-capability model. It is the route that reaches a trustworthy result with the least total time, money, and repair work.
