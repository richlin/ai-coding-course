# Use Harness Commands to Control a Session

By the end of this lesson, you will be able to use built-in slash commands for session control and recognize when a reusable workflow belongs in a skill instead.

## Slash Commands Come from the Harness

Suppose an agent has finished a change and you want to inspect its edits. In Codex or Claude Code, you can type:

```text
/diff
```

The harness recognizes the command and opens its diff view. The model does not need to interpret a prompt such as “show me everything you changed.”

This is the usual role of a slash command: it controls the agent session or invokes behavior built into the harness. Codex and Claude Code ship with commands for changing models, inspecting status, managing permissions, viewing diffs, compacting context, and starting new sessions. Type `/` in the prompt composer to see the commands available in your installed harness. The exact list can vary by product, version, plan, and environment ([Codex command reference](https://developers.openai.com/codex/cli/slash-commands), [Claude Code command reference](https://code.claude.com/docs/en/commands)).

A slash command is not a shell command. `/diff` asks the harness to perform a product action; `git diff` asks your shell to execute a program. The harness may use Git internally, but you are invoking a different interface.

## Start with the Commands You Will Use Often

Codex and Claude Code share several useful command names, although their exact output and options differ. These are good commands to learn first:

| Command | Use it when you need to |
| --- | --- |
| `/model` | Check or change the model used for the session. |
| `/permissions` | Inspect or change which actions require approval. |
| `/status` | Confirm session settings and the active execution context. |
| `/diff` | Inspect the current working-tree changes before accepting or committing them. |
| `/review` | Ask for a focused review of the current changes. |
| `/compact` | Summarize an older conversation to free context while preserving the important state. |
| `/clear` | Start fresh when the next task should not inherit the current conversation. |

Do not memorize a long catalog. Type `/`, search the menu, and verify what your harness says the command does. A name shared by two harnesses does not guarantee identical behavior.

## A Slash Prefix Does Not Tell You Whether Something Is a Skill

Commands and skills can look similar in the interface. Claude Code lists built-in commands, bundled skills, user skills, plugin commands, and MCP prompts in the same `/` menu. It even exposes skills as `/skill-name`. Codex uses `/skills` to browse skills and `$skill-name` to mention one explicitly. Because the invocation syntax differs, the slash prefix alone does not identify the underlying mechanism ([Claude Code skills](https://code.claude.com/docs/en/skills), [Codex skills](https://developers.openai.com/codex/skills)).

Use this distinction:

| Built-in command | Skill |
| --- | --- |
| Supplied and implemented by the harness. | Supplied by the harness, a plugin, your team, or you. |
| Usually performs a product or session action directly. | Loads task-specific instructions, references, and optional scripts for the model to follow. |
| Invoked explicitly, usually through the `/` menu. | Can be invoked explicitly and may also load automatically when the request matches its description. |
| Availability and behavior are harness-specific. | Encodes a reusable workflow that can often travel with a project or plugin. |

For example, Codex implements `/review` as a built-in working-tree review command. Claude Code currently exposes `/review` as an alias for its prompt-based `/code-review` skill. The visible action is similar, but the mechanism is different: one is harness logic, while the other gives the model a review procedure to execute.

This difference matters when you want to add your own workflow. You cannot redefine how a built-in `/status` command calculates session status. You can create a skill that tells an agent how your team reviews database migrations, which files to inspect, which checks to run, and how to report findings. The skill packages model-guided work; the command controls or enters that work.


## References

- [OpenAI: Developer commands](https://developers.openai.com/codex/cli/slash-commands)
- [OpenAI: Build skills](https://developers.openai.com/codex/skills)
- [Anthropic: Commands](https://code.claude.com/docs/en/commands)
- [Anthropic: Extend Claude with skills](https://code.claude.com/docs/en/skills)
