# Use Commands, Hooks, and Scripts

By the end of this lesson, you will be able to place repeated work in the right harness mechanism: a command for an intentional workflow, a hook for an automatic reaction, or a script for deterministic operations.

## Three Mechanisms, Three Triggers

Commands, hooks, and scripts can all start work, but they solve different problems.

| Mechanism | What starts it | Best use |
|---|---|---|
| Command | A person or agent invokes a named action. | A discoverable workflow that should run on demand. |
| Hook | A defined event fires. | A small automatic check or notification tied to that event. |
| Script | Another workflow or person runs a program. | Deterministic operations that should produce the same result from the same inputs. |

A command might start “prepare this change for review.” The command can load instructions, ask the model to inspect the diff, and call project checks. A pre-commit hook might reject trailing whitespace every time a commit is attempted. A script might run the formatter or validate internal Markdown links.

The script often does the mechanical work underneath a command or hook. Keeping that operation separate means engineers and CI can run it without asking a model to reproduce the logic.

## Use a Command for Intentional Work

A command gives a repeated workflow a stable name. It is useful when someone should decide when the workflow starts and model judgment is part of the process.

For example, a review command might instruct an agent to inspect the current diff, run relevant checks, group findings by severity, and stop before committing. The command packages the procedure; it does not make every step deterministic.

Do not create a command merely to hide one ordinary shell invocation. A project script named `check-links` is clearer than a model-driven command whose only job is to run the same validator.

## Use a Hook for an Event

A hook runs because something happened: a tool finished, a file changed, a commit started, or a session reached a harness-defined boundary. Hooks are useful when relying on a person to remember the action is the actual failure mode.

Keep hooks fast and narrow. A slow hook that runs the full test suite after every small edit trains people to bypass it. Run the smallest check that provides timely feedback, then leave broader verification to an explicit command or CI stage.

Hooks also need visible failures. If an automatic formatter, validator, or notification fails silently, the workflow looks successful while the expected control never ran.

## Use a Script for Deterministic Work

A script is the right home when the operation can be specified as inputs, steps, exit status, and output. Formatting, schema generation, link validation, and focused test selection are typical examples.

Prefer a script over prose when correctness does not require judgment. “Run `scripts/check-links` and require exit code zero” is easier to reproduce than asking the model to inspect every link and decide whether it looks valid.

Make scripts safe to rerun. Avoid hidden external writes, print actionable errors, and return a non-zero exit status when the operation fails. If a script can change production data or publish an artifact, keep an explicit approval boundary outside it.

## Compose Them Without Duplicating Logic

A useful composition looks like this:

```text
review command
    ├── asks the model to inspect risk and choose relevant checks
    ├── runs scripts/check-links
    └── runs the focused test script

pre-commit hook
    └── runs scripts/check-format

CI
    ├── runs scripts/check-links
    └── runs scripts/check-format
```

The command owns the judgment-heavy review. Each script owns one deterministic check. The hook and CI reuse those scripts instead of maintaining slightly different copies of the same rule.

## Exercise

1. List three actions your team repeats during development.
2. For each action, identify whether a person should start it, an event should start it, or deterministic code should perform it.
3. Choose one action and define its inputs, output, failure signal, and approval boundary.
4. Test the mechanism on one passing and one failing case.
5. Check that the same logic is not duplicated in a command, hook, and CI configuration.

Complete the exercise when the workflow starts at the right time, reports failure clearly, and keeps deterministic logic in one reusable place.
