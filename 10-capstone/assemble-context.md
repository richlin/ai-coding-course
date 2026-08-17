# Assemble Context and Controls

## What It Means

- Select the repository rules, files, tests, docs, tools, permissions, and human checkpoints needed for the feature.
- Connect each known risk to a specific harness control.
- Create a focused starting brief instead of loading everything available.

## Why It Matters

- This step demonstrates that reliable work depends on the system around the model.
- Explicit controls make safety and verification part of the plan.
- A focused context brief prevents the agent from inventing architecture, missing project rules, or reading unrelated parts of the repository.
- Permission and approval boundaries prevent a useful coding task from turning into an unsafe production or data change.

## Concrete Example

- **Task:** Add self-service account deletion to an existing web application.
- **Useful starting context:**
	- The approved feature spec and acceptance criteria.
	- The route that handles account settings.
	- The user model and existing service used to delete dependent data.
	- A neighboring test for another authenticated settings action.
	- The repository's migration, testing, and security instructions.
- **Context to leave out initially:**
	- The entire frontend component directory.
	- Historical discussions that were superseded by the approved spec.
	- Raw logs from unrelated authentication incidents.
- **Controls:**
	- Allow local file edits and focused tests.
	- Require human approval before creating or applying a destructive migration.
	- Require tests proving that one user cannot delete another user's account.
	- Require a final diff review for accidental logging of personal data.

## Best Practices

- Start from the spec and nearest controlling code path.
- Include only context that can affect an early decision.
- Define permission limits and approval points before execution.
- Record where current external documentation is required.
- Label information as **verified fact**, **assumption**, or **open question**.
- Pair every meaningful risk with a prevention, detection, or approval control.
- Prefer file paths and symbols over pasted file contents when the agent can read the repository.
- Include the exact focused test command the agent should run after its first edit.
- Revisit the context brief when evidence changes the implementation plan.

## Common Mistakes

- Do not confuse having more context or tools with having the right ones.
- Do not provide a repository-wide file dump before identifying the controlling code path.
- Do not give production credentials or broad write access for a task that can be completed locally.
- Do not present assumptions as facts; the agent may build its entire plan on them.
- Do not rely on prose such as “be careful with security” when a permission boundary or test can enforce the requirement.
- Do not omit the verification command and then accept the agent's statement that the feature works.

## Exercise

1. Choose a feature in an existing repository that touches at least two files and has an observable result.
2. Write the feature's goal, non-goals, and three acceptance criteria at the top of a new one-page brief.
3. Identify the first concrete anchor: a route, component, symbol, failing test, or error message.
4. List no more than seven starting sources. For each source, add one bullet explaining which decision it informs.
5. List the tools the agent may use and classify each as read-only, local write, external write, or destructive.
6. Identify at least three risks. Pair each risk with a test, permission limit, human approval, or review check.
7. Add the exact command that should verify the first implementation increment.
8. Give only this brief to a fresh agent and ask it to state its first hypothesis and next action without editing code.
9. Review its answer. Remove unused context and add any missing fact that genuinely blocked the first decision.

Complete the exercise when:

- A one-page context brief containing:
	- One bounded goal and explicit non-goals.
	- No more than seven justified context sources.
	- A tool and permission list.
	- At least three risk-to-control mappings.
	- One focused verification command.
- A fresh agent can identify the likely controlling code path and propose a safe first check without requesting the entire repository.
