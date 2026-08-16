# Harnesses, Agents, Models, Environments, and Tools

## What It Means

- A **model** predicts useful text or actions from the information it receives.
- An **agent** uses a model repeatedly to inspect a task, choose an action, and react to the result.
- A **harness** is the software around the agent that supplies instructions, context, tools, permissions, and feedback.
- An **environment** is where the work happens, such as a repository, terminal, editor, or cloud workspace.
- A **tool** lets the agent affect or inspect that environment, such as reading a file, searching code, or running tests.

## Why It Matters

- The model is only one part of the system; changing the harness can improve results without changing models.
- An agent cannot inspect your repository or run a test unless its harness provides the appropriate tool and permission.
- Failures become easier to diagnose when you know which component supplied the bad information or action.

## Concrete Example

- **Task:** Add rate limiting to `POST /login` in a Node.js API.
- The **model** reasons about possible approaches and interprets the code.
- The **agent** searches for the route, inspects middleware, edits files, and reacts to test output.
- The **harness** supplies repository instructions, tools, permissions, and the requirement to verify the change.
- The **environment** contains the repository, installed dependencies, and test database.
- The **tools** provide evidence: search finds an existing limiter and `npm test -- auth` checks behavior.

## Best Practices

- Ask what context, tools, and permissions the agent has before expecting it to complete a task.
- Treat tool results, repository files, and test output as stronger evidence than the model's memory.
- Change one component at a time when comparing setups.
- Diagnose failures by layer: wrong reasoning may be the model, missing facts may be context, and a failed command may be the environment.
- Keep deterministic checks in tools rather than asking the model to simulate them.

## Common Mistakes

- Do not assume a more capable model can compensate for missing context, unavailable tools, or unclear goals.
- Do not call a chat response an agent workflow when it cannot observe or act on the environment.
- Do not blame the model for a permission or dependency failure reported by a tool.
- Do not grant broad tools before defining the task and its risk.

## Try It

1. Choose one completed coding-agent task.
2. Create a table with `Component`, `What it was`, `Evidence supplied`, and `Failure risk` columns.
3. Add rows for the model, agent, harness, environment, and every tool used.
4. Mark each important claim as a tool result, repository artifact, user statement, or model inference.
5. Identify one failure that changing the model would not have fixed.

## Expected Result

- A component map that separates model reasoning from harness capabilities and environmental evidence.
- At least one concrete improvement to context, tools, permissions, or verification.
