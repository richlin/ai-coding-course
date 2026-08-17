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
