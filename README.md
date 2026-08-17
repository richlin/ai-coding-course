# AI Coding: Self-Guided Training

Follow the modules in order. Later modules assume that you understand the concepts and practices introduced earlier.

## Choose Your Path

- **New to AI coding:** Complete Modules 1-7, then attempt the capstone.
- **Experienced AI coding user:** Review Modules 1-2, then start at your first weak area.
- **Senior engineer or harness owner:** Review the Core modules, then focus on Modules 7-9 and the capstone.
- **Everyone:** Do not skip constraints, specification, context, or verification. These are shared foundations, not beginner-only topics.

## 1. AI Coding System `Core`

- [Harnesses, agents, models, environments, and tools](01-ai-coding-system/system-components.md)
- [Model selection, effort, latency, and cost](01-ai-coding-system/model-selection.md)
- [Permissions and tool execution](01-ai-coding-system/permissions-and-tools.md)

## 2. Constraints and Controls `Core`

- [Compliance bias](02-constraints-and-controls/compliance-bias.md)
- [Statelessness](02-constraints-and-controls/statelessness.md)
- [Context degradation](02-constraints-and-controls/context-degradation.md)
- [Non-determinism](02-constraints-and-controls/non-determinism.md)
- [How harness controls mitigate constraints](02-constraints-and-controls/constraint-mitigations.md)
- [Overview of the six harness components](02-constraints-and-controls/harness-components.md)

## 3. Specify the Work `Core`

- [Intent, assumptions, constraints, and non-goals](03-specify-the-work/task-boundaries.md)
- [Acceptance criteria and goal commands](03-specify-the-work/acceptance-criteria.md)
- [Writing feature and bug-fix specifications](03-specify-the-work/writing-specifications.md)
- [Plan mode and task decomposition](03-specify-the-work/planning-and-decomposition.md)
- [Updating, retaining, or discarding a specification](03-specify-the-work/specification-lifecycle.md)
- [Rerouting when evidence changes the destination](03-specify-the-work/rerouting.md)

## 4. Engineer the Context `Core`

- [Starting context](04-engineer-the-context/starting-context.md)
- [Repository rules and durable artifacts](04-engineer-the-context/repository-rules.md)
- [Codebase exploration](04-engineer-the-context/codebase-exploration.md)
- [Context visibility](04-engineer-the-context/context-visibility.md)
- [Smart zone and dumb zone](04-engineer-the-context/smart-zone-dumb-zone.md)
- [Killing bloat and pruning](04-engineer-the-context/pruning-context.md)
- [Verifying information against primary sources](04-engineer-the-context/primary-sources.md)

## 5. Execute and Verify `Core`

- [Research, plan, implement, verify](05-execute-and-verify/development-loop.md)
- [Small and reversible changes](05-execute-and-verify/reversible-changes.md)
- [Test-driven development](05-execute-and-verify/test-driven-development.md)
- [Tests, types, linting, builds, and runtime checks](05-execute-and-verify/verification-hierarchy.md)
- [Debugging and recovery](05-execute-and-verify/debugging-and-recovery.md)
- [Reviewing changes, security boundaries, and escalation](05-execute-and-verify/review-security-escalation.md)
- [Using `/teach` to explain a change](05-execute-and-verify/teach-the-change.md)

## 6. Manage Sessions and State `Practitioner`

- [Context windows and degradation](06-manage-sessions-and-state/context-windows.md)
- [Compacting and auto-compact](06-manage-sessions-and-state/compacting.md)
- [Fresh sessions and clearing context](06-manage-sessions-and-state/fresh-sessions.md)
- [Durable artifacts and auto-memory](06-manage-sessions-and-state/durable-memory.md)
- [Handoffs between sessions, tools, repositories, and people](06-manage-sessions-and-state/handoffs.md)
- [Choosing between clear, compact, handoff, and subagent](06-manage-sessions-and-state/session-strategy.md)

## 7. Encode Reusable Workflows `Practitioner`

- [Skills, prompts, rules, commands, hooks, and scripts](07-encode-reusable-workflows/reusable-assets.md)
- [User-level versus project-level configuration](07-encode-reusable-workflows/configuration-scope.md)
- [Writing and testing a skill](07-encode-reusable-workflows/writing-skills.md)
- [Enforcing coding standards with executable checks](07-encode-reusable-workflows/executable-standards.md)
- [Pruning stale or conflicting instructions](07-encode-reusable-workflows/pruning-instructions.md)

## 8. Scale the Work `Advanced`

- [Recognizing work that exceeds one context window](08-scale-the-work/large-task-signals.md)
- [Using issue trackers as durable task memory](08-scale-the-work/issue-trackers.md)
- [Splitting features into verifiable tickets](08-scale-the-work/verifiable-tickets.md)
- [Dependencies, ownership, and integration order](08-scale-the-work/dependencies-and-ownership.md)
- [Subagents and parallel work](08-scale-the-work/subagents-and-parallel-work.md)
- [Integration checkpoints](08-scale-the-work/integration-checkpoints.md)

## 9. Design the Team Harness `Advanced`

- [Ground rules and specifications](09-design-the-team-harness/ground-rules.md)
- [Context and knowledge management](09-design-the-team-harness/knowledge-management.md)
- [Tools and integrations](09-design-the-team-harness/tools-and-integrations.md)
- [Skills and reusable assets](09-design-the-team-harness/skills-and-assets.md)
- [Permissions and human approval](09-design-the-team-harness/human-approval.md)
- [Validation, observability, and feedback](09-design-the-team-harness/validation-and-feedback.md)
- [CI enforcement and safe shipping](09-design-the-team-harness/ci-and-shipping.md)
- [Feeding lessons back into the harness](09-design-the-team-harness/continuous-improvement.md)

## 10. Capstone: Reliable Feature Delivery

- [Specify a realistic feature](10-capstone/specify-feature.md)
- [Assemble context and controls](10-capstone/assemble-context.md)
- [Research, plan, implement, and verify](10-capstone/deliver-feature.md)
- [Cross a session boundary or delegate a task](10-capstone/cross-boundaries.md)
- [Review and hand off the work](10-capstone/review-and-handoff.md)
- [Improve the project harness](10-capstone/improve-harness.md)
