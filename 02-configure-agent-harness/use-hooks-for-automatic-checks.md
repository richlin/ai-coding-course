# Use Hooks for Automatic Checks

By the end of this lesson, you will be able to ask an agent to set up a Claude Code hook, explain how the hook handles an event, and verify which hooks are actually configured and running.

## A Hook Runs Because an Event Occurred

Suppose your repository already has this formatting command:

```text
npm run format
```

Your project instructions tell the agent to run it after editing code, but the agent sometimes moves directly to the next task. The instruction described the desired behavior; nothing caused the formatter to run.

A hook closes that gap:

```text
Edit or Write completes
    -> hook matches the file-writing tool
    -> hook runs npm run format
    -> Claude Code reads the outcome
```

A prompt or `CLAUDE.md` rule gives the model guidance. A hook attaches code to a lifecycle event, so the reaction does not depend on the model remembering to initiate it. The handler itself can still fail or be misconfigured, which is why you must test the trigger as well as the underlying command.

This lesson uses Claude Code for a concrete setup because hook configuration is harness-specific. Claude Code currently supports events around prompts, tool calls, permissions, tasks, notifications, context compaction, and session boundaries. Other harnesses may expose different events, configuration files, and failure semantics ([Claude Code hooks guide](https://code.claude.com/docs/en/hooks-guide), [Claude Code hooks reference](https://code.claude.com/docs/en/hooks)).

## A Hook Has Five Runtime Steps

Use this sequence to read any hook:

```text
event -> matcher -> structured input -> handler -> outcome
```

For the formatting hook:

1. `PostToolUse` fires after a tool succeeds.
2. The `Edit|Write` matcher keeps only file-writing tool calls.
3. Claude Code sends JSON describing the event to the command's standard input. This simple command does not need to read it.
4. Claude Code runs `npm run format`.
5. Claude Code interprets the handler's exit status, standard output, and standard error.

A matcher does not perform the check. It prevents the formatting command from running after unrelated tools such as file reads or searches.

The event also determines what an outcome can do. A `PreToolUse` hook can stop a tool before it runs. A `PostToolUse` hook can report a problem or make a follow-up change, but it cannot undo the completed tool call. Exit code `0` with no output means that a command hook has no decision to report. Exit code `2` blocks many decision-capable events and sends standard error back as feedback, but the exact behavior varies by event. Structured JSON provides event-specific decisions such as denying a tool call or adding context. Check the selected event's output contract before writing the handler ([hook input and output](https://code.claude.com/docs/en/hooks#hook-input-and-output)).

## Choose Where the Hook Should Apply

Before creating a hook, choose its scope. In Claude Code, the configuration location determines who receives it ([hook locations](https://code.claude.com/docs/en/hooks#hook-locations)).

| Location | Use it for | Shared with the repository |
| --- | --- | --- |
| `~/.claude/settings.json` | A personal preference across projects, such as desktop notifications. | No |
| `.claude/settings.json` | A project rule every contributor should receive. | Yes |
| `.claude/settings.local.json` | A project-specific experiment or machine-dependent path. | No |
| Plugin `hooks/hooks.json` | A hook distributed as part of a reusable plugin. | With the plugin |
| Managed settings | An organization-controlled policy. | By administrators |

Start in `.claude/settings.local.json` when you are testing a machine-specific hook. Move a stable, portable project control to `.claude/settings.json` after the team has reviewed the command, dependencies, side effects, and latency.

## Use a Starter Prompt to Set Up One Hook

Claude Code's documentation explicitly allows you to ask Claude to create a hook. For the formatting example, start with this prompt:

```text
This repository already uses `npm run format`.

Add a project-shared Claude Code hook that runs `npm run format` after Claude
successfully uses Edit or Write. Merge it into `.claude/settings.json` without
removing existing settings. Do not add dependencies.

Afterward, show me the configuration, explain how to confirm it in `/hooks`,
and tell me how to test it with one file edit.
```

The prompt names one existing command, one trigger, and one scope. It does not ask the agent to choose among unrelated hooks or invent a new formatting workflow.

## Read the Generated Configuration

The prompt above should produce this configuration inside `.claude/settings.json`:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Edit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "npm run format"
          }
        ]
      }
    ]
  }
}
```

Read it from the outside in:

- `PostToolUse` selects the lifecycle event.
- `Edit|Write` selects successful calls to either file-writing tool.
- `type: command` tells Claude Code to start a shell command.
- `npm run format` is the exact command from the starter prompt.

This simple hook runs the formatter after every successful `Edit` or `Write`. That is reasonable only when `npm run format` already exists, is safe to repeat, and finishes quickly. If it becomes slow, replace the inline command with a handler that reads the changed path from the event input and formats only that file.

## Inspect Which Hooks Are Configured

In Claude Code, type:

```text
/hooks
```

The read-only hooks browser shows every event, the number of configured hooks, and each hook's matcher, handler type, source, and command or prompt. The source tells you whether a hook came from user, project, local, plugin, session, or built-in configuration. This resolved view is more reliable than inspecting only `.claude/settings.json`, because hooks can come from multiple scopes ([the `/hooks` menu](https://code.claude.com/docs/en/hooks#the-hooks-menu)).

Use `/hooks` to answer “what is registered?” Then inspect the source file and handler to answer “what code will run?” Neither step proves that the event has fired successfully.

## Prove That a Hook Ran

A successful command hook is often silent. Verify its observable effect first: inspect the formatted file, blocked tool call, written diagnostic, or other intended result.

If the effect is unclear:

1. Press `Ctrl+O` to inspect the transcript for blocking or non-blocking hook errors.
2. Start a diagnostic session with `claude --debug-file /tmp/claude-hooks.log`.
3. Trigger the matching event once.
4. Inspect the local debug log for the matched event, handler, exit status, standard output, and standard error.

You can also run `/debug` during an existing session to enable debug logging. Debug logs may contain commands, paths, and hook output, so keep them local and inspect them before sharing. Anthropic's troubleshooting guide documents these signals and notes that successful hooks normally produce no transcript message ([debug techniques](https://code.claude.com/docs/en/hooks-guide#debug-techniques)).

Distinguish four checks:

```text
settings file parses       -> configuration is syntactically valid
/hooks lists the handler   -> hook is registered
debug log shows execution  -> event and matcher reached the handler
observable state is right  -> handler achieved the intended outcome
```

Stopping after any earlier check leaves a different failure mode untested.

## Start with a Concrete Failure Mode

Do not add a hook merely because an event exists. Start with something people or agents repeatedly forget, then choose the earliest event that provides useful feedback.

| Failure you want to catch | Event | Narrow reaction | Observable result |
| --- | --- | --- | --- |
| Edited code is left unformatted. | After a file-writing tool succeeds | Format only the changed supported file. | The file is formatted before the next review. |
| An agent tries to edit generated code. | Before a file-writing tool runs | Reject paths under `generated/` and point to the generator. | The write does not occur; the agent receives the correct command. |
| A secret or oversized asset is about to be committed. | Before commit | Use a Git hook to scan staged files and reject the commit on a match. | The commit stops with the affected path and rule. |
| A schema edit leaves generated artifacts stale. | After a schema file changes | Run the repository's focused consistency check. | Stale output is named immediately. |
| A migration uses a forbidden operation. | After a migration file changes | Run a static migration-policy check on that file. | The diagnostic identifies the operation and line. |
| A long-running agent needs a decision. | When Claude Code sends a notification | Send a local desktop notification. | The user can switch away without polling the terminal. |
| Important context may be lost during compaction. | When a compacted session resumes | Re-inject concise project state from a durable source. | The restored context appears in the next model turn. |
| A tracked task cannot finish without a focused smoke check. | Before that task is marked complete | Run the check and return actionable feedback if it fails. | Task completion is blocked with the failed check. |

A Git pre-commit hook and a Claude Code hook are adjacent but different mechanisms. Git owns commit lifecycle events; Claude Code owns agent lifecycle events. Choose the system that can observe the event you care about ([Git hooks](https://git-scm.com/docs/githooks)).

## Match Cost and Side Effects to the Event

The more often an event fires, the less work its hook should perform:

```text
after each edit       -> format or lint one changed file
before each commit    -> check staged files
before each push      -> run a focused package test suite
in CI                 -> run all required checks in a clean environment
```

Choose the earliest event where the check is both cheap enough and accurate enough. A full test suite after every edit delays the feedback loop. Waiting until CI to report a one-file formatting error wastes a faster feedback opportunity.

Hooks can either report a problem or correct it automatically. Formatting a changed source file may be safe when the result is local, repeatable, and reviewable. Rewriting a migration, updating a lockfile, or regenerating a large client can obscure consequential changes. In those cases, report the exact remediation command instead of silently changing more state.

Do not use a hook to silently publish an artifact, modify production data, send a team message, or approve a sensitive external action. Those operations need an explicit approval boundary. A predictable trigger does not make a consequential side effect safe.

## Complete the Setup with Evidence

A hook is ready when you can show all of the following:

- its scope is intentional;
- `/hooks` shows the expected event, matcher, source, and handler;
- the handler runs for a matching event and skips a non-matching event;
- a known violation produces an actionable outcome;
- a repeated event does not duplicate or corrupt state;
- its normal runtime is acceptable at the event's frequency; and
- the broader requirement remains covered by permissions, explicit review, or CI where appropriate.

## References

- [Anthropic: Automate actions with hooks](https://code.claude.com/docs/en/hooks-guide)
- [Anthropic: Hooks reference](https://code.claude.com/docs/en/hooks)
- [Git: githooks](https://git-scm.com/docs/githooks)
- [Jose Parreño Garcia: Claude Code hooks explained](https://joseparreogarcia.substack.com/p/claude-code-hooks-explained-the-missing)
