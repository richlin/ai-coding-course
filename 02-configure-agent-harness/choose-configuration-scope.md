# Choose User-Level or Project-Level Configuration

By the end of this lesson, you will be able to place a configuration at the narrowest useful scope and predict which value an agent harness will apply when scopes conflict.

## One Session Can Have Several Configuration Sources

Suppose your personal Claude Code settings enable spinner tips, the repository disables them, and a local file enables them again:

```text
~/.claude/settings.json          spinnerTipsEnabled: true
repo/.claude/settings.json       spinnerTipsEnabled: false
repo/.claude/settings.local.json spinnerTipsEnabled: true
```

Claude Code does not choose the first file it happens to find. It loads applicable sources and resolves the same setting according to a defined scope priority. Here, the local value applies.

That mechanism separates two questions:

1. **Reach:** which sessions and people can receive this configuration?
2. **Authority:** which source wins when more than one source defines the same setting?

Choose a scope by reach. Diagnose a conflict by authority.

## Scope Determines Reach

Claude Code exposes four durable scopes. The command line adds a temporary, session-level source between managed and local configuration.

| Scope | Typical location | Who receives it | Use it for |
|---|---|---|---|
| Managed | Organization-deployed settings | Organization members or machine users | Enforced security, compliance, and fleet policy |
| User | `~/.claude/settings.json` | You, across repositories | Personal preferences and tools you use everywhere |
| Project | `.claude/settings.json` | Everyone using the checked-in repository | Shared permissions, hooks, plugins, and tooling |
| Local | `.claude/settings.local.json` | You, in this repository | Machine-specific values and experiments |

Use the narrowest scope that still reaches everyone who depends on the configuration. A formatter hook required for every contributor belongs in project scope. Your preferred theme belongs in user scope. A path to a tool installed only on your laptop belongs in local scope.

Project correctness must not depend on a private user or local file. If every contributor needs a setting, check it into the repository or enforce it through managed configuration.

## Resolve Settings in Priority Order

For ordinary Claude Code settings, evaluate applicable sources according to Claude Code's documented [settings precedence](https://code.claude.com/docs/en/settings#settings-precedence), from highest to lowest priority:

```text
managed settings
    > command-line arguments
        > local project settings
            > shared project settings
                > user settings
```

For a scalar value such as `spinnerTipsEnabled`, the highest-priority source that defines the key supplies the effective value. Lower-priority sources still fill keys that higher-priority sources leave unset. This is precedence, not permission for a private preference to redefine a team requirement: a local override changes only your session and does not fix the shared repository configuration.

Reading order and conflict resolution are easy to confuse. A harness may load several files into one effective configuration; the documented precedence rule determines the result, not the incidental filesystem read order. Other harnesses use different files and priorities, so verify their documentation rather than transferring Claude Code's order by analogy.

## Not Every Conflict Is Replacement

“Higher scope wins” is incomplete because the setting's data type and semantics affect how sources combine.

Claude Code handles common cases this way:

| Configuration shape | Combination behavior |
|---|---|
| Most scalar values | Take the value from the highest-priority source that defines the key |
| Most arrays | Concatenate and deduplicate entries across scopes |
| Permission arrays | Merge rules, then evaluate matches as `deny`, `ask`, and `allow` |
| Documented exceptions | Follow the setting-specific rule instead of the general order |

Consider a user-level permission that allows `Bash(pnpm test *)` and a project-level permission that denies reading `.env`. Both rules remain active because permission arrays merge. If one tool call matches more than one permission category, Claude Code checks `deny` before `ask`, then `allow`; the first matching category determines the result.

This differs from the spinner setting. The spinner values compete for one scalar slot, while the permission rules form a combined policy. Before resolving a conflict, identify whether the key replaces, merges, or has a documented exception.

## Settings and Instructions Are Different Systems

`settings.json` controls harness behavior such as permissions, hooks, plugins, and interface options. `CLAUDE.md` supplies natural-language instructions to the model. Their locations have corresponding user, project, and local scopes, but that does not make instruction text a set of scalar settings with automatic key-level conflict resolution.

For a session launched from a repository subtree, Claude Code [orders instruction files](https://code.claude.com/docs/en/memory#how-claude-md-files-load) from broadest to most specific:

```text
managed CLAUDE.md
-> user ~/.claude/CLAUDE.md
-> ancestor CLAUDE.md files, from the filesystem root toward the working directory
-> CLAUDE.md in the working directory
```

Within one directory, `CLAUDE.local.md` is appended after `CLAUDE.md`. Instructions below the working directory are not loaded at launch; Claude Code loads them on demand when it reads files in those subdirectories. Run `/context` and inspect **Memory files** to see which instruction files are present.

This order affects where the text appears in context, but all discovered files are concatenated. A more specific file does not delete a broader file. Two contradictory prose rules can therefore both enter the model's context, and Claude may choose between them inconsistently. Avoid relying on “read last” as conflict management. Remove the duplicate, narrow one rule's applicability, or enforce the invariant with settings, a hook, a script, or a test.

A task prompt is different again. It defines the current assignment: the desired outcome, task-specific constraints, and evidence of completion. It is not another durable configuration file and should not be treated as an enforceable security-policy layer.

Use this boundary:

```text
durable harness behavior -> settings at managed, user, project, or local scope
durable working guidance -> user, project, or subtree instruction file
current assignment       -> task prompt
mechanical invariant     -> permission, hook, script, test, or CI check
```

## Manage Conflicts at the Source

When observed behavior does not match the file you edited:

1. List every applicable source, including managed policy, command-line arguments, local files, project files, and user files.
2. Find every source that defines the setting. Do not stop at the file you expected to win.
3. Classify the setting as scalar, array, permission rule, or documented exception.
4. Apply the harness's precedence or merge rule.
5. Remove accidental duplicates. Keep deliberate overrides only when their scope and reason are clear.
6. Start a representative session and inspect an observable result.

In Claude Code, run `/status` and inspect `Setting sources` to confirm which layers loaded. This identifies active sources, not the source of each effective key, so you still need to inspect conflicting files. Test permission changes with a harmless command or path that should be allowed, asked, or denied.

Keep raw secrets out of checked-in project configuration and natural-language instruction files. Use the harness's supported credential mechanism or an external secret store; a private scope changes distribution but does not automatically make plaintext safe.

## Exercise

1. Gather ten entries from user settings, project settings, local settings, instruction files, and recent task prompts.
2. Label each entry by scope and by type: setting, instruction, task constraint, or executable check.
3. For every duplicate, state whether it replaces, merges, or remains ambiguous prose.
4. Move one entry to the narrowest scope that reaches everyone who needs it.
5. Test from a fresh session with and without repository context.

Complete the exercise when you can show the loaded sources, predict the effective value of each duplicated setting, and demonstrate that team-critical behavior does not depend on private configuration.

## References

- [Claude Code settings: configuration scopes and precedence](https://code.claude.com/docs/en/settings#how-scopes-interact) — scope locations, priority, merge behavior, exceptions, and active-source verification.
- [Claude Code memory](https://code.claude.com/docs/en/memory) — user, project, and local `CLAUDE.md` instruction loading.
