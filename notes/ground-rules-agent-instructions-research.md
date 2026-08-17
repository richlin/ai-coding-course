# Project Instruction Files: Codex, Claude Code, and GitHub Copilot

Verified against official product documentation on 2026-08-17.

## Course-level conclusion

The course can introduce ground rules as persistent project instructions, but it should not define `AGENTS.md` as a file every harness loads automatically. The products use different native files and discovery rules:

| Harness | Native project instruction file | When it loads | Important qualification |
| --- | --- | --- | --- |
| OpenAI Codex | `AGENTS.md` | Once when a run starts; in the TUI, usually once per launched session | Native hierarchical discovery from the project root to the working directory |
| Anthropic Claude Code | `CLAUDE.md` | Ancestor files at session launch; descendant files when Claude reads in those directories | Does not natively discover `AGENTS.md`; import it from `CLAUDE.md` or use a symlink |
| GitHub Copilot | `.github/copilot-instructions.md`; several surfaces also support `AGENTS.md` | Depends on the surface; Copilot CLI loads at session start | File support and precedence differ across GitHub.com, IDEs, code review, cloud agent, and CLI |

This makes “project instruction file” the accurate general term. `AGENTS.md`, `CLAUDE.md`, and `.github/copilot-instructions.md` are concrete harness-specific implementations.

## OpenAI Codex

### Loading and scope

Codex reads `AGENTS.md` before doing work and builds its instruction chain once per run. In the TUI, this normally means once per launched session. It first reads global guidance from the Codex home directory, then walks from the project root down to the current working directory. [OpenAI: Custom instructions with AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md#how-codex-discovers-guidance)

At global scope, `AGENTS.override.md` replaces `AGENTS.md` when the override exists. At each project directory, Codex checks `AGENTS.override.md`, then `AGENTS.md`, then configured fallback filenames and includes at most one file. It concatenates the selected files root-first, so instructions closer to the working directory occur later and override earlier guidance. [OpenAI: Custom instructions with AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md#how-codex-discovers-guidance)

Codex stops its initial search at the current working directory. A nested instruction file therefore affects a run only when Codex is launched at or below that directory. The combined project guidance has a 32 KiB default limit controlled by `project_doc_max_bytes`. [OpenAI: Custom instructions with AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md#how-codex-discovers-guidance)

### What belongs in the file

OpenAI’s examples use the file for repeatable working agreements: package-manager choice, test and lint commands, documentation expectations, and actions that require confirmation. Repository instructions inherit global defaults, while nested overrides express service-specific rules. [OpenAI: Create global guidance and layer project instructions](https://learn.chatgpt.com/docs/agent-configuration/agents-md#create-global-guidance)

The AGENTS.md guide specifically tells authors to keep code-review rules concise, describe the behavior to flag plus any safe path or exception, and leave formatting and lint checks to CI. It does not state the same general brevity rule as strongly for every section of an `AGENTS.md`; the documented size cap and nested-directory scoping are the broader practical constraints. [OpenAI: Add code review rules](https://learn.chatgpt.com/docs/agent-configuration/agents-md#add-code-review-rules)

OpenAI’s current model guidance separately recommends lean prompts: state each instruction once and remove repeated instructions and examples. That guidance supports keeping always-loaded project instructions focused, but it is general prompting advice rather than an `AGENTS.md` discovery rule. [OpenAI: Model guidance—favor leaner prompts](https://developers.openai.com/api/docs/guides/latest-model#prompting-best-practices)

## Anthropic Claude Code

### Loading and scope

Claude Code’s native persistent instruction file is `CLAUDE.md`. The documented load order is managed policy, user instructions at `~/.claude/CLAUDE.md`, project instructions at `./CLAUDE.md` or `./.claude/CLAUDE.md`, and local project-specific instructions at `./CLAUDE.local.md`. Ancestor files above the working directory load in full at launch; files in descendant directories load on demand when Claude reads files there. [Anthropic: Choose where to put CLAUDE.md files](https://code.claude.com/docs/en/memory#choose-where-to-put-claudemd-files)

Claude Code concatenates discovered files rather than treating the more specific file as a hard override. Content is ordered from the filesystem root toward the working directory, and `CLAUDE.local.md` follows `CLAUDE.md` within a directory. Anthropic warns that when instructions conflict, Claude may choose one arbitrarily. This is a load order, not an enforcement or deterministic precedence system. [Anthropic: How CLAUDE.md files load](https://code.claude.com/docs/en/memory#how-claudemd-files-load)

### AGENTS.md compatibility

Anthropic states directly that Claude Code reads `CLAUDE.md`, not `AGENTS.md`. For a repository that already has `AGENTS.md`, the recommended bridge is a `CLAUDE.md` containing `@AGENTS.md`; a symlink is another option. The import is expanded into context at session start. Claude Code’s `/init` and `/import` workflows can also incorporate or copy instructions from other agent configurations, but that is not native ongoing `AGENTS.md` discovery. [Anthropic: AGENTS.md](https://code.claude.com/docs/en/memory#agentsmd)

### Concision and progressive disclosure

Anthropic says `CLAUDE.md` is loaded into the context window at the start of every session and recommends specific, concise, structured instructions. Its target is fewer than 200 lines per file because longer files consume more context and reduce adherence. Imports can improve organization, but they still load at launch and do not reduce context use. [Anthropic: Write effective instructions](https://code.claude.com/docs/en/memory#write-effective-instructions)

The documentation gives a clear routing rule: keep facts Claude should hold in every session in `CLAUDE.md`; move a multi-step procedure to a skill and narrow directory or file-type guidance to a path-scoped rule. Path-scoped rules load only when Claude works with matching files, reducing noise and saving context. [Anthropic: When to add to CLAUDE.md](https://code.claude.com/docs/en/memory#when-to-add-to-claudemd) and [Anthropic: Organize rules with `.claude/rules/`](https://code.claude.com/docs/en/memory#organize-rules-with-clauderules)

Anthropic also frames `CLAUDE.md` as guidance, not enforcement. For a behavior that must happen at a lifecycle point or an action that must be blocked, use hooks or permissions instead. [Anthropic: Claude isn’t following my CLAUDE.md](https://code.claude.com/docs/en/memory#claude-isnt-following-my-claudemd)

## GitHub Copilot

### Files, scope, and precedence

GitHub documents three repository-level instruction forms: `.github/copilot-instructions.md` for repository-wide instructions, `.github/instructions/**/*.instructions.md` for path-specific instructions, and agent instruction files such as `AGENTS.md`, `CLAUDE.md`, or `GEMINI.md`. Path-specific and repository-wide files can both apply to one request. [GitHub: About repository custom instructions](https://docs.github.com/en/copilot/concepts/prompting/response-customization#about-repository-custom-instructions)

For Copilot on GitHub.com, the documented precedence is personal instructions, applicable path-specific instructions, `.github/copilot-instructions.md`, agent instructions such as `AGENTS.md`, and organization instructions. All relevant sets are still provided to Copilot, so GitHub recommends avoiding conflicts. [GitHub: Precedence of custom instructions](https://docs.github.com/en/copilot/concepts/prompting/response-customization#precedence-of-custom-instructions)

Within agent instructions, repositories can place `AGENTS.md` files anywhere. When Copilot is working, the nearest `AGENTS.md` in the directory tree takes precedence. [GitHub: Adding repository custom instructions](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/add-custom-instructions/add-repository-instructions#creating-custom-instructions)

### Support varies by Copilot surface

`AGENTS.md` support is not universal across Copilot. GitHub’s current support matrix lists it for Copilot cloud agent, Copilot code review, VS Code Copilot Chat, and Copilot CLI. Copilot Chat on GitHub.com lists personal, repository-wide, and organization instructions, but not agent instruction files. Visual Studio and several other IDE/surface combinations also support only a subset. Any course claim about Copilot should name the relevant surface or link to the live matrix. [GitHub: Support for different types of custom instructions](https://docs.github.com/en/copilot/reference/custom-instructions-support)

Copilot CLI loads custom instructions at the start of a session, including `AGENTS.md` and `.github/copilot-instructions.md`. Changes to instruction files do not affect an active CLI session until the user exits and resumes it or starts a new session. The CLI combines applicable files and does not define a general precedence order between the file types, so its documentation says to avoid conflicts. [GitHub: Comparing Copilot CLI customization features](https://docs.github.com/en/copilot/concepts/agents/copilot-cli/comparing-cli-features#custom-instructions) and [GitHub: Adding custom instructions for Copilot CLI](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-custom-instructions#custom-instructions-in-use)

### Concision and progressive disclosure

GitHub recommends short, self-contained statements that apply broadly because repository instructions are sent with every chat message. Path-specific files keep file- or directory-specific material out of the repository-wide file. [GitHub: Writing effective custom instructions](https://docs.github.com/en/copilot/concepts/prompting/response-customization#writing-effective-custom-instructions)

For Copilot CLI, GitHub recommends a skill when instructions apply to only one workflow or become so large and specific that they distract from the immediate task. Skills load relevant instructions just in time rather than making all of them always-on context. [GitHub: Comparing Copilot CLI customization features](https://docs.github.com/en/copilot/concepts/agents/copilot-cli/comparing-cli-features#custom-instructions)

## Recommended framing for the early chapter

Use this conceptual sequence:

1. A **ground rule** is the course concept: a standing instruction that changes how an agent works across tasks.
2. A **project instruction file** is the delivery mechanism: the harness automatically contributes its relevant contents to agent context.
3. The filename is harness-specific: Codex uses `AGENTS.md`, Claude Code uses `CLAUDE.md`, and Copilot's primary repository-wide file is `.github/copilot-instructions.md`; Copilot's `AGENTS.md` support varies by feature.
4. Put only broadly applicable, non-obvious facts in always-loaded instructions. Move narrow rules to path-scoped files and multi-step workflows to skills or other on-demand assets.
5. Treat instructions as guidance. Use tests, CI, hooks, permissions, and sandboxing when a requirement must be enforced.

Avoid saying that every harness loads a root file only at “session start.” Codex searches only to its launch working directory, Claude Code additionally discovers descendant instructions on demand, and Copilot’s behavior depends on the product surface.
