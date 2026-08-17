# Non-Determinism

By the end of this lesson, you will be able to tell useful variation from unreliable behavior and build checks that keep an agent's output acceptable even when its implementation changes from run to run.

Suppose you ask a coding agent to add login rate limiting. You give it the same repository and the same request three times, resetting the repository before each run:

```text
Block an account after five failed login attempts.
Return 429 and allow another attempt after ten minutes.
```

The first run reuses existing middleware. The second writes a small helper around the login handler. The third adds a counter but never resets it after ten minutes.

Nothing in the prompt or code had to change. The output changed anyway.

These runs show the important distinction. Different code is not automatically a problem. The first two implementations may both be acceptable. The third is not, because it breaks required behavior.

That is non-determinism in practical terms: the same request can lead an agent through different reasoning, tool calls, and code changes. Your job is not to force every run down the same path. Your job is to put stable checks at the end of those paths.

```text
same request -> different implementations -> same acceptance checks
```

## One Token Can Change the Whole Run

A model does not retrieve one fixed answer from a stored answer key. At each step, it assigns probabilities to possible next pieces of text, called tokens, and selects one. Sampling often includes some randomness because always taking the highest-probability token can produce repetitive or lower-quality text.

Suppose the model is about to choose between these two plans:

```text
Reuse the existing limiter ...  51%
Write a small helper ...         49%
```

The numbers are illustrative, but the consequence is real. If one run selects `Reuse` and another selects `Write`, every choice that follows now starts from a different plan. One different token can grow into different searches, tool calls, and code.

Provider infrastructure can add more variation. Requests may be batched with other requests and run across shared hardware. Small differences in floating-point calculations can affect a close choice. The details vary by provider, but the practical conclusion is stable: turning sampling randomness down may make runs more repeatable; it does not make a complete agent workflow perfectly deterministic.

Context and environment add another layer. A changed conversation, different tool output, or modified repository can alter the result before token sampling is even considered. If two runs start from different files, they are different experiments, not evidence of model non-determinism.

## One Passing Run Is One Sample

This is why one successful attempt proves less than it first appears to prove. If one run passes, you know that the workflow *can* produce an acceptable result. You do not yet know how often it will do so.

Imagine that an agent succeeds once, then fails four times on clean repeats. Reporting only the first result makes a fragile workflow look reliable. Repeated runs expose whether success comes from stable instructions and checks or from a lucky path through the task.

Think of an agent's output as a distribution, not a fixed capability. Many runs may land in an acceptable middle, while an occasional run is unusually good or badly off target. The tails matter because production workflows eventually encounter them.

## Decide Which Differences Matter

You can sort differences between runs by their consequence:

- A harmless difference changes the shape of the code without changing its behavior. One run names a helper `isRateLimited`; another names it `shouldBlockLogin`.

- A beneficial difference reveals a useful option. One run finds existing middleware that is simpler than the custom counter proposed by another run.

- An acceptance-breaking difference violates a requirement. A run returns `403` instead of `429`, blocks successful logins, or never clears the counter.

Only the last category must be eliminated. Forcing identical helper names or file layouts can hide useful alternatives and make the prompt harder to maintain without making the feature safer.

For the rate limiter, a small set of checks can define the boundary:

```text
four failed attempts  -> login may continue
five failed attempts  -> return 429
ten minutes later     -> allow another attempt
successful login      -> preserve existing behavior
```

The agent may use middleware, a helper, or a small service. If every required check passes and review finds no unacceptable tradeoff, the implementation can differ without the outcome becoming unreliable.

## Put Determinism in the Checks

A precise prompt helps the agent aim at the right target, but a prompt is not a test. The sentence “reset after ten minutes” can still produce an off-by-one error or a counter that resets only when the process restarts.

Executable checks make the required outcome repeatable. A test can advance a fake clock by ten minutes and assert that the next login is allowed. Types can reject an invalid return value. A linter can reject a forbidden import. Review can catch a needless new dependency that automated checks do not cover.

Use the cheapest check that can observe the failure:

- Put exact behavior in tests when code can verify it.

- Use types and linters for structural rules they can enforce directly.

- Use review for design costs, readability, and side effects that are hard to encode.

- Write acceptance criteria in plain language so both the agent and reviewer know what the checks are protecting.

## Retry a Bad Draw, Investigate a Pattern

A fresh attempt is a reasonable response to one poor run. If the agent chooses an awkward design or gets stuck debugging the wrong file, reset the work and retry from the same clean starting point. The next run may take a better path without any change to the prompt.

Retrying buys another draw, but it does not repair a bad task definition. If every run misunderstands the ten-minute reset rule, clarify the acceptance criterion or add a failing test. If every run crashes because a command is broken, fix the environment. Repeating a systematic failure only spends more time.

Be equally careful with stories about improvement or decline. Three frustrating runs can make it feel as though “the model got worse this week,” while three excellent runs can create the opposite impression. A short streak may be ordinary variation. Before blaming a model or provider change, repeat a fixed task from clean state and compare the results with the same checks. This is the practical warning behind [AI Hero's description of non-determinism](https://www.aihero.dev/ai-coding-dictionary/non-determinism): do not turn a few draws into a trend without evidence.
