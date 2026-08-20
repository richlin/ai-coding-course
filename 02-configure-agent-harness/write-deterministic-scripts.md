# Write Deterministic Scripts

By the end of this lesson, you will be able to move repeatable mechanical work out of prose and into a script with defined inputs, outputs, and failure signals.

## A Script Makes an Operation Repeatable

A script is the right mechanism when an operation can be specified as inputs, steps, output, and exit status. Formatting, schema generation, link validation, and focused test selection are typical examples.

Prefer a script over prose when correctness does not require judgment. “Run `scripts/check-links` and require exit code zero” is easier to reproduce than asking a model to inspect every link and decide whether it looks valid.

A script differs from a command because it should not depend on model judgment. It differs from a hook because it does not decide when it runs. A person, command, hook, or CI job can invoke the same script.

## Define the Contract

A useful project script makes four things clear:

- which arguments, files, or environment values it accepts;
- what it writes or prints;
- what success and failure exit statuses mean; and
- whether it changes any state outside the working tree.

Print actionable errors. A link checker should identify the source file and unresolved target instead of returning only `check failed`. Return a non-zero exit status when the operation fails so agents, hooks, and CI can respond consistently.

Keep the interface stable even if the implementation changes. A project-wide `check-links` entry point lets callers avoid depending on the validator's internal command-line options.

## Make Scripts Safe to Rerun

Running a script twice with the same inputs should normally produce the same result. Avoid hidden external writes and partial state changes. If the script generates files, write them consistently and make clear which files it owns.

If a script can change production data, publish an artifact, or contact an external system, keep an explicit approval boundary outside the script. Deterministic behavior does not make a consequential action safe to trigger automatically.

## Reuse One Implementation

Commands, hooks, local workflows, and CI should call the same script instead of keeping separate versions of the rule:

```text
review command
    └── scripts/check-links

pre-commit hook
    └── scripts/check-format

CI
    ├── scripts/check-links
    └── scripts/check-format
```

This composition separates judgment, timing, and mechanics. The command handles contextual decisions, the hook reacts to an event, and each script performs one repeatable operation.

## Exercise

1. Choose one mechanical instruction currently written in prose.
2. Define its inputs, output, exit status, and side effects.
3. Implement or outline one script that performs the operation.
4. Run it on one passing and one failing case.
5. Identify the commands, hooks, or CI jobs that should reuse it.

Complete the exercise when the script produces consistent results, reports actionable failures, is safe to rerun, and contains no decisions that require model judgment.
