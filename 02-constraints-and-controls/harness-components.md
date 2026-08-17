# Overview of the Six Harness Components

## What It Means

- **Ground rules and specifications** define goals, constraints, standards, and execution order.
- **Context and knowledge** determine what the agent can see and what state persists.
- **Tools and integrations** let the agent inspect, change, and verify the environment.
- **Skills and reusable assets** encode repeated procedures and templates.
- **Permissions and human approval** define delegation boundaries and stopping points.
- **Validation and feedback** measure progress and guide the next action.

## Why It Matters

- The harness is the control system around the model.
- Reliable results usually require several components working together.

## Concrete Example

- **Rules/spec:** Limit failed logins to five per user and IP in ten minutes; return `429`; add no dependency.
- **Context/knowledge:** Supply auth architecture, existing Redis helper, neighboring middleware, and deployment topology.
- **Tools:** Enable code search, scoped edits, focused tests, type checks, and official docs.
- **Reusable assets:** Use the security-review skill and API-test template.
- **Permissions/HITL:** Allow local edits; require approval for dependency, infrastructure, or production changes.
- **Validation/feedback:** Run auth tests and CI, then monitor `429` and login-failure rates after rollout.

## Best Practices

- Start with the smallest harness that supports a real workflow.
- Put stable knowledge in durable artifacts and changing evidence in tool output.
- Give each component one clear responsibility and owner.
- Use validation to close the loop after every meaningful action.
- Review the harness after failures and major environment changes.

## Common Mistakes

- Do not treat the harness as a one-time configuration.
- Do not install many tools or write broad rules before defining a workflow.
- Do not duplicate one instruction across components with different wording.
- Do not add memory without deciding what may persist and who corrects it.
- Do not call a harness reliable when it cannot verify output or stop safely.

## Exercise

1. Choose one recurring workflow, such as fixing a bug or adding an endpoint.
2. Draw boxes for rules/specs, context/knowledge, tools, reusable assets, permissions/HITL, and validation/feedback.
3. List the current mechanism and owner in each box.
4. Trace one recent failure to the component that should have prevented or detected it.
5. Add one small improvement and define how to test it on the next task.

Complete the exercise when:

- A complete harness map for one real workflow, including ownership and gaps.
- One evidence-driven improvement rather than a generic tool wish list.
