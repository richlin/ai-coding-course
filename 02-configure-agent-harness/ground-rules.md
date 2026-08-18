# `AGENTS.md`: Project Ground Rules

By the end of this chapter, you will be able to write a short `AGENTS.md`, place rules at the right scope, and keep task-specific details out of always-loaded context.

## The Project's Standing Brief

`AGENTS.md` tells a coding agent how to work in a repository across tasks and sessions. A task prompt says what to build today; `AGENTS.md` records durable project rules such as:

- Use `pnpm`; do not create an npm lockfile.
- After changing notifications, run `pnpm test --filter notifications`.
- Do not edit `src/generated/`; run `pnpm generate`.
- Ask before adding a production dependency or changing the database schema.

If you repeat the same project-specific correction in fresh sessions, it may belong in `AGENTS.md`.

## Start Small

Begin at the repository root:

```markdown
# AGENTS.md

This repository contains the web app and API for a team notification product.

## Commands

- Install dependencies with `pnpm install`.
- Run package tests with `pnpm test --filter <package>`.

## Boundaries

- Do not edit `src/generated/`; run `pnpm generate`.
- Ask before adding dependencies or running migrations.

## Verification

- After changing a package, run its tests and type check.
- Report any repository check you could not run.
```

Each line should resolve a real decision. “Write clean code” does not explain what to do. “After changing package X, run command Y” does.

Verification belongs here only when it is a stable project rule. “Run the affected package's type check” applies across tasks. “The checkout page handles expired cards” is a feature acceptance criterion and belongs in its issue or specification—not in `AGENTS.md`.

## Use Three Levels

Place each rule at the narrowest scope where it remains useful:

```text
~/.codex/AGENTS.md                         personal defaults
work/acme/AGENTS.md                        repository rules
work/acme/services/payments/AGENTS.md      payments-only rules
```

| Level | Put here | Keep out |
|---|---|---|
| Personal | Preferences that follow you across repositories. | Team rules, repository commands, and credentials. |
| Repository | Project purpose, shared commands, boundaries, approvals, and verification. | Package-only rules and long documentation. |
| Subtree | Commands, invariants, and boundaries unique to one package or service. | Repeated root rules and full design documents. |

A monorepo root should explain the shared project, not every package. Put payment rules in `services/payments/AGENTS.md` so unrelated work does not carry them. Large repositories can repeat the subtree level as deeply as needed.

## Keep It Short

Every loaded rule consumes context. Keep each `AGENTS.md` within 100–150 lines. Treat 150 as a ceiling, not a target; a complete 30-line file is better than a padded 100-line file.

Ask of every line: “Does an agent need this before making its first decision on most tasks in this scope?” If not, move it closer to where it is needed:

- Put package rules in a subtree `AGENTS.md`.
- Link architecture and style guides instead of copying them.
- Load task procedures through a skill or task prompt.
- Enforce mechanical rules with tests, linters, hooks, permissions, or CI.

Use links as triggered breadcrumbs:

```text
AGENTS.md -> docs/typescript.md -> docs/testing.md
          -> release skill, loaded only for release work
```

“For TypeScript changes, read `docs/typescript.md`” is useful. “Read every file in `docs/`” merely moves the context problem elsewhere.

## What Belongs—and What Does Not

Include:

- A one-sentence project or package purpose.
- Commands the agent cannot safely guess, including when to run them.
- Boundaries around generated files, migrations, dependencies, and external writes.
- Project conventions where choosing the wrong pattern causes real rework.
- Stable verification expectations and approval points.
- Links to deeper guidance, each with a clear trigger.

Leave out:

- A task or feature's definition of done and acceptance criteria.
- Long architecture explanations, tutorials, API references, and file inventories.
- Generic advice such as “be careful” or “follow best practices.”
- Rules already expressed precisely by formatters, linters, compilers, or CI.
- Secrets, customer data, credentials, and production examples.
- Temporary status, duplicated rules, and brittle line-number references.

Prefer stable capabilities over current coordinates. “The authentication package owns login and sessions; read `docs/authentication.md` before changing it” ages better than “authentication lives at `src/auth/handlers.ts`.”

Generated instruction files are drafts, not finished rules. Review every line and remove repository facts the agent can discover, advice that applies only sometimes, and anything likely to go stale.

## Know How Your Harness Loads Rules

Codex loads the global file, then one instruction file per directory from the repository root to the current working directory. A closer file wins when rules conflict. `AGENTS.override.md` replaces `AGENTS.md` in the same directory.

Codex does not load descendant instructions when started at the repository root. To load payment rules, start in that subtree or run `codex --cd services/payments`.

Other harnesses differ. Claude Code uses `CLAUDE.md`; it can share the same rules with `@AGENTS.md`. GitHub Copilot support varies by surface, so check its current support matrix. Keep tool-specific adapters small and preserve one source of truth for shared rules.

## Maintain and Test the Rules

Add a rule when it prevents a repeated or expensive mistake. When the file approaches 150 lines, remove duplicates, move narrow rules into subtree files, and move explanations into normal documentation.

Test changes in a fresh session from the directory where they should apply. Ask the agent which instruction files it loaded, give it a representative task, and check an observable action: the command it chose, the file it avoided, or the approval it requested.

## Exercise

1. Write a one-sentence project description.
2. Sort candidate rules into personal, repository, and subtree scope.
3. Add only non-standard commands, important boundaries, verification, and approval points.
4. Use 100–150 lines as the ceiling; split or prune the file when it grows beyond that range.
5. Start a fresh session and verify which instruction files load.
6. Give the agent a small task and check whether each rule changes an observable action.

## References

- [AI Hero: A Complete Guide to `AGENTS.md`](https://www.aihero.dev/a-complete-guide-to-agents-md) — instruction budgets, progressive disclosure, monorepo scope, and pruning.
- [OpenAI Codex: Custom instructions with `AGENTS.md`](https://developers.openai.com/codex/guides/agents-md) — discovery, scope, precedence, and overrides.
- [Claude Code: How Claude remembers your project](https://code.claude.com/docs/en/memory) — `CLAUDE.md` loading and importing `AGENTS.md`.
- [GitHub Copilot: Custom instructions support](https://docs.github.com/en/copilot/reference/custom-instructions-support) — supported instruction files by Copilot surface.
