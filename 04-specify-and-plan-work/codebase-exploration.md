# Create Codebase Navigation Artifacts

You will turn codebase exploration into durable maps and task specs that help future agents find the right code without repeating the same search.

## Do not leave the map in the chat

Suppose an agent must add a “completed” filter to a small task application. It searches for the task list, traces the request through the UI and API, finds the query that applies filters, and locates the relevant tests.

If those findings remain only in the conversation, the next agent must repeat the exploration. Instead, preserve the useful path in the repository:

```text
Task list flow
web/tasks/page.tsx
  -> api/tasks.ts:listTasks
  -> domain/tasks/list-tasks.ts:listTasks
  -> data/tasks.ts:findTasks

Behavior owner: domain/tasks/list-tasks.ts
Relevant tests: test/domain/tasks/list-tasks.test.ts
Verification: pnpm test test/domain/tasks/list-tasks.test.ts
```

This is a navigation artifact: a maintained index of entry points, behavior owners, important flows, and their checks. It gives an agent a verified place to start, not a complete description of every file.

This solves a direct consequence of [agent statelessness](../01-ai-coding-system/statelessness.md). A new session can read files in the repository, but it does not automatically inherit the paths, decisions, and evidence discovered in an earlier conversation. Exploration becomes reusable only when the agent writes its useful findings into artifacts that the next session can retrieve.

Those findings belong in [durable project artifacts, not private auto-memory](../03-manage-context/durable-memory.md). Repository artifacts are visible to the team, reviewable in a diff, and correctable when the code changes. Auto-memory may help one user resume a conversation, but it is not the shared source of truth for codebase structure or task requirements.

The map and spec then become [focused starting context](../03-manage-context/starting-context.md). Instead of loading the entire repository or replaying an old transcript, the next agent starts with the task outcome, the relevant code path, and the first verification command. It can search outward only when the artifact leaves a material question unanswered.

## Create two outputs

Exploration should usually produce or update two artifacts:

| Artifact | Question it answers | Lifetime |
| --- | --- | --- |
| Codebase map | Where does this behavior enter, flow, and get verified? | Reused across tasks |
| Task spec | What must change now, what must remain unchanged, and how will we verify it? | Lives with the task |

If the repository has no established locations, use `docs/codebase-map.md` for the shared map and `specs/<task-name>.md` for the task spec. Follow an existing convention when one exists.

Do not put both kinds of information in `AGENTS.md`. As explained in [Write a good `AGENTS.md`](../02-configure-agent-harness/write-project-instructions.md), repository instructions are the standing brief: required commands, boundaries, and rules that apply across tasks. A codebase map describes structure. A task spec defines one change. Keeping these roles separate lets an agent load the right detail at the right time.

## Write the codebase map for navigation

Record only information that shortens future exploration:

```markdown
# Codebase Map

## System shape
One paragraph naming the major runtime parts and how they communicate.

## Feature paths
- Task list: `web/tasks/page.tsx` -> `api/tasks.ts:listTasks`
  -> `domain/tasks/list-tasks.ts:listTasks` -> `data/tasks.ts:findTasks`

## Behavior owners
- Task filtering: `domain/tasks/list-tasks.ts:listTasks`

## Tests and checks
- Task query behavior: `test/domain/tasks/list-tasks.test.ts`
- Focused command: `pnpm test test/domain/tasks/list-tasks.test.ts`
```

Use real paths, symbols, and runnable commands. Do not write labels such as “service layer” without showing where that layer exists. Link to deeper documents instead of copying them into the map.

Update the map when a change moves an entry point, behavior owner, major flow, or verification command. Do not update it for an internal refactor that leaves navigation unchanged.

## Turn current findings into a task spec

For the completed-filter task, create a small spec:

```markdown
# Completed Task Filter

## Outcome
Users can show all, active, or completed tasks.

## Relevant code
- Entry point: `web/tasks/page.tsx`
- Behavior owner: `domain/tasks/list-tasks.ts:listTasks`
- Existing test: `test/domain/tasks/list-tasks.test.ts`

## Scope boundary
Add one filter value to the existing list flow. Do not add saved views.

## Acceptance checks
- `completed=true` returns only completed tasks.
- Omitting the filter preserves the current result.
- The focused task-query test passes.

## Open questions
- Does the URL retain the selected filter? Confirm before implementation.
```

The map helps an agent navigate; the spec tells it what evidence matters for this change. A map without a spec can lead to a technically correct edit that solves the wrong problem. A spec without a map makes every agent rediscover where to work.

## Verify the artifacts with a fresh start

Use the [fresh-session workflow](../03-manage-context/fresh-sessions.md) as a test. Give a fresh agent only the repository instructions, the codebase map, and the task spec. Ask it to identify:

1. The first file to inspect.
2. The code that owns the behavior.
3. The nearby test to change or extend.
4. The command that verifies the focused behavior.
5. Any unresolved question that blocks a safe plan.

The artifacts are useful when the agent can answer those questions from valid repository evidence without scanning the whole codebase. Correct any stale path or unsupported claim it exposes. The goal is not more documentation; it is less repeated discovery and a more reliable starting point for implementation.

When work crosses a session, tool, or owner boundary, the [handoff](../03-manage-context/handoffs.md) should link to the map and spec rather than duplicate them. The handoff records current state and the next action; the durable artifacts remain the maintained sources for structure and requirements.

## References

- [Codebase Exploration](https://www.skillsdirectory.com/skills/rsmdt-codebase-exploration) — an example of structured exploration output.
- [Codebase Exploration Pilot](https://mcpmarket.com/tools/skills/codebase-exploration-pilot) — examples of architecture and entry-point reconnaissance.
- [The AI-Legible Codebase](https://tianpan.co/blog/2026-04-13-the-ai-legible-codebase) — a discussion of structural indexes for agent navigation.
