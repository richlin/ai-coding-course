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

## Try It

1. Open the tool and permission configuration for your coding agent.
2. List every tool and the systems or data it can reach.
3. Classify each as read-only, local write, external write, or destructive.
4. Choose one typical feature task and mark only the tools it requires.
5. Define approval rules for installation, network, production, and destructive actions.
6. Run the task with reduced permissions and record any legitimate blocker.

## Expected Result

- A permission matrix with default, approval-required, and prohibited actions.
- The sample task can complete without unused high-impact access.