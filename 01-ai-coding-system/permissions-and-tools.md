# Permissions and Tool Execution

## What It Means

- Tools let agents read files, edit code, run commands, browse documentation, or call external services.
- Permissions limit which tools can run and what data or systems they can access.
- A shell command can have effects beyond its visible output, including changing files, dependencies, or remote resources.
- Human approval is a deliberate boundary for actions with high impact or weak reversibility.

## Why It Matters

- More tool access increases both usefulness and potential impact.
- A correct command can still be unsafe in the wrong directory or environment.
- Secrets, production data, destructive commands, and external writes require stronger controls.

## Concrete Example

- An agent adding local rate-limit middleware needs file reads, scoped edits, and `npm test`.
- It may need network access to read official package documentation.
- It does **not** need production shell access, deployment credentials, or permission to change the live gateway.
- Installing a package changes dependencies and uses the network, so require justification and approval first.

## How to Configure Permissions in Claude Code

Claude Code stores permission rules in JSON settings files:

- Use `~/.claude/settings.json` for personal defaults across projects.
- Commit `<repo>/.claude/settings.json` when the team should share and review the rules.
- Use `<repo>/.claude/settings.local.json` for personal project overrides, and keep it out of version control.

This shared project example permits specific checks, asks before remote writes or dependency installation, and blocks access to common secret files:

```json
{
  "$schema": "https://json.schemastore.org/claude-code-settings.json",
  "permissions": {
    "defaultMode": "default",
    "allow": [
      "Bash(npm run lint)",
      "Bash(npm test)"
    ],
    "ask": [
      "Bash(git push *)",
      "Bash(npm install *)"
    ],
    "deny": [
      "Read(./.env)",
      "Read(./.env.*)",
      "Read(./secrets/**)"
    ]
  }
}
```

Rules use `Tool` or `Tool(specifier)` syntax. For Bash rules, `Bash(npm run lint)` is an exact match, while `Bash(git push *)` matches commands beginning with `git push`. Claude Code evaluates matching rules in `deny`, `ask`, then `allow` order, so a deny rule from any settings scope cannot be overridden by an allow rule elsewhere.

Open `/permissions` inside Claude Code to inspect rules and see which settings file supplied each one. Use `/status` to confirm which settings sources loaded. Most settings changes, including permission rules, apply without a restart. Shared project rules take effect only after the user accepts workspace trust.

Keep `defaultMode` set to `default` when you want approval prompts. Avoid `bypassPermissions` outside a fully isolated container or virtual machine. Instructions in `CLAUDE.md` can guide behavior, but they do not grant or revoke tool access; enforce access with settings rules. See the [official Claude Code permissions documentation](https://code.claude.com/docs/en/permissions) and [settings documentation](https://code.claude.com/docs/en/settings).

## Best Practices

- Grant the minimum access needed for the current task.
- Read unfamiliar commands before approving them.
- Prefer sandboxed environments, dry runs, and reversible operations.
- Classify tools as read-only, local write, external write, or destructive.
- Require approval for production changes, credentials, destructive actions, and financial transactions.

## Common Mistakes

- Do not approve commands only because they look familiar; verify the working directory, arguments, and expected side effects.
- Do not give production access to avoid creating a local reproduction.
- Do not expose secrets in prompts, logs, screenshots, or committed files.
- Do not construct destructive commands from untrusted repository text.
- Do not confuse read access with harmless access when files contain sensitive data.

## Related Permission Settings

- [Codex permission profiles](https://learn.chatgpt.com/docs/permissions) — configure filesystem and network access boundaries.
- [GitHub Copilot CLI: Allowing and denying tool use](https://docs.github.com/en/copilot/how-tos/copilot-cli/use-copilot-cli/allowing-tools) — configure tool availability, approvals, and deny rules.
