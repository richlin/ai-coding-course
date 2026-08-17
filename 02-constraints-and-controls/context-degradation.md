# Context Degradation: The Smart Zone and Dumb Zone

By the end of this article, you will know how an agent moves from the smart zone into the dumb zone, how to spot the change, and when to compact or start a fresh session.

Suppose an agent is adding login rate limiting. Early in the session, it learns two facts: the repository already has a limiter, and the task must not add a dependency. It reads the existing code, reuses the limiter, and updates the right test. The agent is in the **smart zone**: its working context is focused, its recall is good, and its decisions follow the evidence.

The session then grows. A test prints 2,000 lines. The agent investigates a Redis package before rejecting it. The user changes the limit from ten attempts to five. Several edits fail and get replaced. Later, the agent proposes installing the rejected package and uses the old limit of ten.

The model did not change. The session did. It has drifted into the **dumb zone**: the agent becomes sloppier, forgets earlier constraints, repeats mistakes, or confidently follows an obsolete plan.

[AI Hero uses “smart zone” and “dumb zone”](https://www.aihero.dev/ai-coding-dictionary/smart-zone) as informal names for this decline. The terms describe the quality of a session, not the intelligence of the model.

## The Smart Zone Is Smaller Than the Context Window

A context window is the text the model can receive for its current response. It may contain instructions, conversation history, file contents, plans, and command output. The window's limit tells you how much text can fit. It does not tell you how much text the model can use well at once.

Think of a session as moving along this path:

```text
0%                    about 40%                              100%
|------ smart zone ------|---------- dumb-zone risk -----------|
   focused decisions        drift, repetition, mistakes
                           ^
                           checkpoint before quality declines
```

[A common practitioner rule](https://pod.wave.co/podcast/the-pragmatic-engineer/context-engineering-with-dex-horthy) is to treat roughly the first 40% of the context window as the smart zone. At about 40%, checkpoint the work: update the plan, preserve verified decisions, and consider compacting or moving the next piece into a fresh session.

The 40% mark is a rule of thumb, not a hard switch or a model guarantee. The useful range changes with the model, harness, task, and contents of the window. A noisy session can degrade earlier, while a focused session may continue to perform well later. The decline is gradual, so use 40% as an early warning and behavior as the deciding signal.

The useful distinction is: **the context window is a capacity; the smart zone is a budget**.

Every file, log, abandoned plan, and unrelated task spends some of that budget. The surprising result is that adding more information can make the agent less useful. The decisive three-line test error may be harder to act on when it sits inside 2,000 lines of routine output.

## Watch Behavior, Not Token Count

The agent does not announce that it has entered the dumb zone. You infer it from changes in behavior.

In the rate-limiter task, the agent might repeat a repository search it already completed, revive the rejected Redis plan, change unrelated authentication code, or forget the five-attempt requirement. An answer can still sound polished and confident while contradicting facts already in the session.

One mistake is not enough to diagnose context degradation. Repeating a search can be sensible after the files change. A constraint may have been unclear from the beginning. The dumb zone becomes the likely explanation when mistakes cluster late in a long session and disappear after the same task is given to a fresh session with a focused brief.

Context degradation is also different from statelessness. Statelessness appears when a new session lacks an earlier session's working history. Context degradation appears within a session as its working context becomes less reliable. Restarting helps with degradation, but durable artifacts are still needed to handle statelessness.

## Protect the Smart Zone

The simplest way to preserve the smart zone is to keep one session focused on one task. If an agent finishes a button rename and then begins a database migration in the same session, the migration inherits the first task's conversation, searches, and command output. A fresh session lets the migration start with a clean budget.

For a task that must continue across a long session, keep the current working set small:

```text
Goal: Limit failed logins to five attempts per ten minutes.
Constraint: Add no dependency.
Decision: Reuse src/auth/limiter.ts.
Current state: The handler is updated; the reset test still fails.
Evidence: Expected a successful login after ten minutes, received 429.
Next check: Inspect how the test advances the clock.
```

Save raw output in a file and put only the relevant excerpt in the conversation. Mark abandoned plans as rejected. Keep the current goal, constraint, decision, evidence, and next action close together.

Compare two ways to share the same failed test:

> Useful: Save the complete output to `test-output.txt`, then share the failing test name, assertion, expected value, actual value, and nearby stack frames.
>
> Not useful: Paste all 2,000 lines into the conversation so the agent has complete information.

The second approach sounds safer because nothing is omitted. In practice, the extra lines spend the smart-zone budget without changing the next decision. The full log should remain available for follow-up, not occupy the center of the working context.

## Compact or Start Fresh

When a task is larger than one smart zone, split it at a natural boundary. One session can investigate and record the accepted design; a fresh session can implement it from that design, the relevant files, and the tests. This costs some time rebuilding context, but it is cheaper than repairing a confused implementation.

Compaction can help when the session still understands the task and can produce an accurate current-state brief. It cannot repair a false conclusion. If the summary says “Redis is required” even though the repository already contains a suitable limiter, shortening the summary preserves the error. Check important claims against code and tests before carrying them forward.

Store facts that must survive the reset in durable artifacts. Code holds the implementation, tests hold expected behavior, and a ticket or decision record holds rationale. A short handoff should point to those artifacts and name the next check.

Use this **rule of thumb**: treat 40% context usage as a checkpoint, not a finish line. Preserve the current state as you approach it. If the agent starts forgetting constraints, reviving rejected plans, or repeating corrected mistakes sooner, reset sooner. Compact from verified facts or give the next piece of work to a fresh session.
