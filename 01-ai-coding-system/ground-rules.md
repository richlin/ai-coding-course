# `AGENTS.md`: Ground Rules for Working with an Agent

By the end of this chapter, you will be able to write a short `AGENTS.md` that gives coding agents the project instructions they need in every session. You will also know what to leave out so the file does not consume context or bury its own important rules.

## The Project's Standing Brief

A ground rule is a standing instruction that changes how an agent works across tasks. A project instruction file is how the harness delivers that rule to the model. `AGENTS.md` is the main convention used by Codex and several other agent harnesses, but it is not the native filename in every tool.

Think of `AGENTS.md` as the project's standing brief: a small set of instructions the agent should receive before it starts work.

A task prompt says what to achieve today. `AGENTS.md` records how work is done in this repository across tasks and sessions. It is a good home for facts such as:

- Use `pnpm`; do not create an npm lockfile.
- Run `pnpm test --filter notifications` after changing the notifications package.
- Treat `src/generated/` as generated output; never edit it directly.
- Ask before adding a production dependency or changing a database schema.

The model does not carry a correction from one fresh session into the next. The harness solves part of that statelessness problem by loading the instruction file again. If you correct the same project-specific mistake in a second session, that correction is a candidate for `AGENTS.md`.

## Write the First `AGENTS.md`

Start at the repository root with a brief that covers commands, boundaries, and verification:

```markdown
# AGENTS.md

## Commands

- Install dependencies with `pnpm install`.
- Run focused tests with `pnpm test --filter <package>`.

## Boundaries

- Do not edit files under `src/generated/`; regenerate them with `pnpm generate`.
- Preserve unrelated changes already present in the working tree.
- Ask before adding dependencies or running database migrations.

## Definition of done

- Run the focused tests and type check for each package you change.
- Report any required check you could not run.
```

Each line resolves a decision the agent will actually face. “Write clean code” does not: the agent cannot infer which local pattern you consider clean or how to prove it complied. Prefer a concrete trigger and action, such as “after changing package X, run command Y.”

Commit repository-wide rules so every engineer and agent receives the same brief. Keep personal preferences in the harness's user-level instruction file, and keep requirements unique to one change in the task prompt or specification.

## Keep Always-On Context Small

Automatic loading is both the value and the cost of `AGENTS.md`. The instructions survive fresh sessions, but they also occupy context in every session within their scope. As the file grows, irrelevant material competes with the current task and the rules that matter most become harder for the model to follow.

Keep the root file short and declarative. It should contain facts the agent cannot reliably derive from the repository and that apply to nearly every task. Move other material closer to where it is needed:

- Put subsystem-specific rules in a nested instruction file when the harness supports directory scope.
- Put task-specific procedures behind a skill or invoke them only for the relevant task.
- Keep architecture explanations and style guides in normal documentation, then point to them when needed.
- Enforce objective rules with tests, linters, hooks, permissions, or CI instead of repeating long prose.

A useful filter is: “Would an agent need this line before making its first decision on most tasks in this scope?” If not, progressively disclose it later.

## Know Which Filename Your Harness Reads

`AGENTS.md` is a cross-harness convention, not a universal standard implemented identically everywhere. Check the behavior of the tool you use:

| Harness | Standing instruction files | Loading and scope |
|---|---|---|
| OpenAI Codex | `AGENTS.md` and `AGENTS.override.md` | Codex builds an instruction chain at the start of a run, combining global guidance with files from the project root down to the working directory. Instructions closer to the working directory appear later and override broader guidance. |
| Anthropic Claude Code | `CLAUDE.md`, `.claude/CLAUDE.md`, and `CLAUDE.local.md` | Claude Code loads applicable ancestor and project instructions at session start, then discovers instructions in descendant directories when it works there. It does not read `AGENTS.md` directly; a project can keep shared rules in `AGENTS.md` and import them from `CLAUDE.md` with `@AGENTS.md`. |
| GitHub Copilot | `AGENTS.md`, `.github/copilot-instructions.md`, and path-specific instruction files | Support varies by Copilot surface. Copilot cloud agent and Copilot CLI support `AGENTS.md`; repository-wide Copilot instructions live in `.github/copilot-instructions.md`. Check the support matrix for the IDE or agent you use. |

For a repository used with both Codex and Claude Code, keep shared rules in `AGENTS.md` and add this small adapter:

```markdown
# CLAUDE.md

@AGENTS.md

## Claude Code

- Add only Claude-specific instructions here.
```

This keeps one source of truth for shared ground rules without pretending the harnesses have identical discovery or precedence behavior.

## Rules Guide; Controls Enforce

Instruction files shape model behavior; they are not hard enforcement. A rule can tell an agent not to edit generated files, but the model can still misunderstand or overlook it. Pair important rules with an executable control when possible:

- A test verifies required behavior.
- A linter or formatter verifies a mechanical standard.
- A permission boundary blocks a dangerous operation.
- CI prevents an invalid change from merging.

Keep the short instruction because it tells the engineer and agent what to do. Add enforcement because prose alone is not a guarantee.

## Exercise

1. Choose a repository where you regularly work with a coding agent.
2. Write no more than ten lines of `AGENTS.md` covering commands, protected boundaries, verification, and approval points.
3. Remove anything the agent can derive from the code or that applies only to one task.
4. Start a fresh session and ask the agent to list the instruction sources it loaded.
5. Give it a small task and check whether each rule changed an observable action.

Complete the exercise when a fresh agent follows the repository's important working agreements without you repeating them in the prompt.

## Continue Through the Course

[Repository Rules and Durable Artifacts](../04-engineer-the-context/repository-rules.md) explains how instruction files fit with specs, tests, and architecture records. [Ground Rules and Specifications](../09-design-the-team-harness/ground-rules.md) shows how a team owns, enforces, and evolves the rules across many engineers and agents.

## References

- [AI Hero: `AGENTS.md`](https://www.aihero.dev/ai-coding-dictionary/agents-md) — the example definition that motivated this chapter.
- [OpenAI Codex: Custom instructions with `AGENTS.md`](https://developers.openai.com/codex/guides/agents-md) — discovery, scope, precedence, overrides, and verification.
- [Claude Code: How Claude remembers your project](https://code.claude.com/docs/en/memory) — `CLAUDE.md` loading, concise-instruction guidance, and importing `AGENTS.md`.
- [GitHub Copilot: Support for different types of custom instructions](https://docs.github.com/en/copilot/reference/custom-instructions-support) — support for `AGENTS.md` and Copilot-specific instruction files across Copilot surfaces.
- [GitHub Copilot CLI: Add custom instructions](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-custom-instructions) — discovery and use of `AGENTS.md`, `CLAUDE.md`, and `.github/copilot-instructions.md`.
