# Permissions and Tool Execution

Suppose you ask an agent to add rate-limit middleware to a Node application. The agent needs to read the existing server code, edit a few files, and run `npm test`. It may also need network access to read the package documentation.

None of that requires a production shell, deployment credentials, or permission to change the live gateway. Those capabilities would not make the local coding task much easier, but they would make a mistake much more expensive.

That is the purpose of a permission system: give the agent enough access to finish the current task without silently giving it access to every system you can reach.

## A Tool Call Is Where Text Becomes an Action

A model does not edit a file or run a command by itself. It returns a request such as "run `npm test`" or "write this content to `server.ts`." The agent harness checks that request against its permission rules, runs the tool if the rules permit it, and returns the result to the model.

The tool creates the side effect. Reading a file puts its contents into the model's context. Editing a file changes the working tree. A shell command can change files, install dependencies, contact remote services, or delete data. Two commands that print similar output can have very different consequences depending on their arguments, working directory, credentials, and environment.

Instructions and permissions play different roles here. A repository instruction can tell the model not to read `.env`, but that is guidance the model must follow. A deny rule prevents the harness from completing the read even if the model asks. Use instructions to shape behavior; use permissions to enforce a boundary.

## Grant Access by Consequence

The useful question is not "Do I trust this agent?" It is "What can this specific operation change, and how hard would that change be to undo?"

The common permission boundaries differ in consequence:

- Read access is usually the safest starting point, but it is not harmless when the readable files contain API keys, customer data, or private source code. Anything the agent reads may enter its context, logs, or a later tool call.
- Local writes let the agent implement code. In a version-controlled working tree, you can usually inspect and revert them, although generated files, local databases, and untracked data need more care.
- Network access lets a command download packages or send data beyond the machine. An `npm install` also changes dependency metadata and often a lockfile, so it deserves more scrutiny than reading package documentation.
- External writes change systems that Git cannot restore: pushing a branch, opening a pull request, deploying a service, sending a message, or updating a ticket.
- Destructive or privileged actions can remove data, alter infrastructure, spend money, or expose credentials. These calls need a narrow target, a clear reason, and a deliberate approval step.

Human approval is most valuable at the boundaries between these categories. Constant prompts for ordinary file reads teach people to approve reflexively. A prompt before a production deployment gives the reviewer a meaningful decision: verify the target, inspect the proposed action, and decide whether its consequences are acceptable.

## Configure Permissions in Claude Code

Claude Code reads permission rules from JSON settings files. Choose the file based on who should inherit the rule:

- Put personal defaults in `~/.claude/settings.json` when they should apply across your projects.
- Commit `<repo>/.claude/settings.json` when the team should share and review the rules.
- Put personal overrides for one repository in `<repo>/.claude/settings.local.json`, and keep that file out of version control.

The following shared project configuration permits two routine checks, asks before dependency installation or a remote Git write, and blocks common secret files:

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

A rule has the form `Tool` or `Tool(specifier)`. `Bash(npm run lint)` matches that exact command. `Bash(git push *)` uses a wildcard to match commands that begin with `git push`, including the bare command.

Claude Code checks matching rule categories in `deny`, `ask`, then `allow` order. The first category with a match determines the result, regardless of which matching rule is more specific. A broad deny such as `Bash(git *)` therefore cannot contain a narrower exception such as `Bash(git status)` in the allow list.

Open `/permissions` inside Claude Code to inspect the active rules and see which settings file supplied each one. Use `/status` to confirm which settings sources loaded. Shared project allow rules take effect only after the user accepts workspace trust.

Keep `defaultMode` set to `default` when you want approval prompts for tool calls that are not already allowed or denied. `bypassPermissions` is appropriate only when an isolated container or virtual machine provides the real safety boundary. Without that isolation, bypass mode gives a mistaken command access to everything available to the Claude Code process.

## Permissions and Sandboxing Solve Different Problems

A permission rule decides whether Claude Code may invoke a tool. A sandbox constrains what a shell command and its child processes can reach after the tool starts. In Claude Code, sandbox restrictions apply to Bash, while permission rules also cover tools such as Read, Edit, and WebFetch.

You often want both. A deny rule can stop the model from requesting a sensitive file in the first place. A filesystem sandbox can stop a shell command from reaching that file even if the command behaves differently than expected. Network restrictions can likewise contain a package script that attempts an outbound connection.

A sandbox also changes the approval tradeoff. Broad shell access inside a disposable container may be reasonable because the process cannot reach production credentials or important host files. The same access on a developer laptop may expose SSH keys, cloud credentials, and unrelated repositories. Permission decisions make sense only in the environment where the tool will run.

## Review the Operation, Not Just the Command Name

Before approving a tool call, check the working directory, the complete arguments, the credentials in scope, and the expected side effects. `npm test` in a local application is not equivalent to a script with the same name in an unfamiliar repository. Repository scripts can execute arbitrary code, and untrusted repository text should not be allowed to construct a destructive command.

Prefer a local reproduction to production access, a dry run to an immediate write, and a reversible operation to a destructive one. Keep secrets out of prompts, logs, screenshots, and committed files. If an agent does not need a credential for the task, do not place that credential in its environment.

A practical default is to begin with repository reads, scoped local edits, and the exact checks the task requires. Expand access when the agent reaches a concrete need, and add approval where an operation crosses from local and reversible to external, sensitive, or difficult to undo.

## Related Permission Settings

- [Claude Code permissions](https://code.claude.com/docs/en/permissions) — configure tool rules, permission modes, and workspace trust.
- [Claude Code settings](https://code.claude.com/docs/en/settings) — choose where personal, project, local, and managed settings live.
- [Codex permission profiles](https://learn.chatgpt.com/docs/permissions) — configure filesystem and network access boundaries.
- [GitHub Copilot CLI: Allowing and denying tool use](https://docs.github.com/en/copilot/how-tos/copilot-cli/use-copilot-cli/allowing-tools) — configure tool availability, approvals, and deny rules.
