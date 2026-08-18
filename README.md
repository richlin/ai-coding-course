# AI Coding: Self-Guided Training

This course explains how to use coding agents reliably, starting with the system around one model request and ending with a team-scale delivery harness. Follow the chapters in order: each chapter assumes the mechanisms and working habits introduced before it.

## Choose Your Path

- **New to AI coding:** Complete Chapters 1–5, then attempt the capstone. Return to Chapters 6–7 when you begin coordinating larger or team-owned work.
- **Experienced AI coding user:** Review Chapters 1–2, then start at your first weak area.
- **Senior engineer or harness owner:** Review Chapters 1–3, then focus on Chapters 6–7 and the capstone.
- **Everyone:** Do not skip context, specification, or verification. They are shared foundations, not beginner-only topics.

## 1. The Core AI Coding System

- [Harnesses, agents, and models](01-ai-coding-system/system-components.md)
- [Model selection](01-ai-coding-system/model-selection.md)
- [Reasoning effort](01-ai-coding-system/effort.md)
- [Cost](01-ai-coding-system/cost.md)
- [Permissions and tool execution](01-ai-coding-system/permissions-and-tools.md)
- [Statelessness](01-ai-coding-system/statelessness.md)
- [Non-determinism](01-ai-coding-system/non-determinism.md)
- [Compliance bias](01-ai-coding-system/compliance-bias.md)

## 2. Configure the Agent Harness

- [Write an effective task prompt](02-configure-agent-harness/task-prompts.md)
- [AGENTS.md](02-configure-agent-harness/ground-rules.md)
- [Write and test a skill](02-configure-agent-harness/writing-skills.md)
- [Use commands, hooks, and scripts](02-configure-agent-harness/commands-hooks-and-scripts.md)
- [Enforce coding standards with executable checks](02-configure-agent-harness/executable-standards.md)
- [Prune stale or conflicting instructions](02-configure-agent-harness/pruning-instructions.md)
- [Choose user-level or project-level configuration](02-configure-agent-harness/configuration-scope.md)

## 3. Manage Context and Sessions

- [Understand context windows](03-manage-context/context-windows.md)
- [Start with the right context](03-manage-context/starting-context.md)
- [Recognize the smart zone and dumb zone](03-manage-context/smart-zone-dumb-zone.md)
- [Diagnose context degradation](03-manage-context/context-degradation.md)
- [Make context visible](03-manage-context/context-visibility.md)
- [Kill bloat and prune context](03-manage-context/pruning-context.md)
- [Use fresh sessions and clear context](03-manage-context/fresh-sessions.md)
- [Compact long sessions](03-manage-context/compacting.md)
- [Hand work across sessions, tools, repositories, and people](03-manage-context/handoffs.md)
- [Choose between clear, compact, handoff, and subagent](03-manage-context/session-strategy.md)
- [Store shared truth in durable artifacts, not auto-memory](03-manage-context/durable-memory.md)

## 4. Specify and Plan the Work

- [Explore the codebase before deciding](04-specify-and-plan-work/codebase-exploration.md)
- [Verify information against primary sources](04-specify-and-plan-work/primary-sources.md)
- [Separate repository rules from task artifacts](04-specify-and-plan-work/repository-rules.md)
- [State intent, assumptions, constraints, and non-goals](04-specify-and-plan-work/task-boundaries.md)
- [Define acceptance criteria and goal commands](04-specify-and-plan-work/acceptance-criteria.md)
- [Write feature and bug-fix specifications](04-specify-and-plan-work/writing-specifications.md)
- [Decompose work in plan mode](04-specify-and-plan-work/planning-and-decomposition.md)
- [Use the research, plan, implement, verify loop](04-specify-and-plan-work/development-loop.md)
- [Update, retain, or discard a specification](04-specify-and-plan-work/specification-lifecycle.md)
- [Reroute when evidence changes the destination](04-specify-and-plan-work/rerouting.md)

## 5. Implement and Verify

- [Make small, reversible changes](05-implement-and-verify/reversible-changes.md)
- [Use test-driven development](05-implement-and-verify/test-driven-development.md)
- [Combine tests, types, linting, builds, and runtime checks](05-implement-and-verify/verification-hierarchy.md)
- [Debug and recover systematically](05-implement-and-verify/debugging-and-recovery.md)
- [Review changes, security boundaries, and escalation](05-implement-and-verify/review-security-escalation.md)

## 6. Scale the Work

- [Recognize work that exceeds one context window](06-scale-the-work/large-task-signals.md)
- [Use issue trackers as durable task memory](06-scale-the-work/issue-trackers.md)
- [Split features into verifiable tickets](06-scale-the-work/verifiable-tickets.md)
- [Manage dependencies, ownership, and integration order](06-scale-the-work/dependencies-and-ownership.md)
- [Use subagents and parallel work](06-scale-the-work/subagents-and-parallel-work.md)
- [Set integration checkpoints](06-scale-the-work/integration-checkpoints.md)

## 7. Design the Team Harness

- [Scale ground rules and specifications across a team](07-design-the-team-harness/ground-rules.md)
- [Manage context and knowledge](07-design-the-team-harness/knowledge-management.md)
- [Choose tools and integrations](07-design-the-team-harness/tools-and-integrations.md)
- [Share skills and reusable assets](07-design-the-team-harness/skills-and-assets.md)
- [Set permissions and human approval points](07-design-the-team-harness/human-approval.md)
- [Build validation, observability, and feedback](07-design-the-team-harness/validation-and-feedback.md)
- [Enforce standards in CI and ship safely](07-design-the-team-harness/ci-and-shipping.md)
- [Feed lessons back into the harness](07-design-the-team-harness/continuous-improvement.md)

## 8. Capstone: Deliver a Feature Reliably

- [Specify a realistic feature](08-capstone/specify-feature.md)
- [Assemble context and controls](08-capstone/assemble-context.md)
- [Research, plan, implement, and verify](08-capstone/deliver-feature.md)
- [Cross a session boundary or delegate a task](08-capstone/cross-boundaries.md)
- [Review and hand off the work](08-capstone/review-and-handoff.md)
- [Improve the project harness](08-capstone/improve-harness.md)
