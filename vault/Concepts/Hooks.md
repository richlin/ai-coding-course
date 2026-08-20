---
title: Hooks
tags: [type/concept]
related: [[Deterministic Scripts]], [[Six Harness Components]], [[Acceptance Checks]]
---

# Hooks

Code attached to a harness lifecycle event, so a reaction does not depend on the model remembering to trigger it.

## Mechanism

```
event -> matcher -> structured input -> handler -> outcome
```

An event fires (e.g., a tool call succeeds); a matcher narrows it to relevant cases (e.g., only file-writing tools); the harness sends structured data to a handler; the handler runs; the harness interprets the handler's exit status and output as the outcome.

The event determines what the outcome can do: a hook running *before* an action can block it; a hook running *after* can only report or make a follow-up change — it cannot undo what already happened.

## Verification is four separate checks

```
settings file parses       -> configuration is syntactically valid
hook registry lists it     -> hook is registered
debug log shows execution  -> event and matcher reached the handler
observable state is right  -> handler achieved the intended outcome
```

Stopping at an earlier check leaves a later failure mode untested — a hook can be registered and still never fire, or fire and still fail silently.

## Match cost to event frequency

The more often an event fires, the cheaper its hook should be: format one file after an edit, check staged files before a commit, run a fuller suite before a push, run everything in CI. A hook should report or correct only when the result is local and reviewable — not silently publish, modify production data, or approve a consequential action.

## Authoring friction determines whether a hook gets built at all

A hook that would catch a real mistake is worth nothing if manual JSON authoring friction keeps it un-written. Hookify (a Claude Code plugin) converts hook authoring into a conversational request — describe the guardrail in natural language and the plugin generates the Markdown/YAML rule file directly — on the claim that "the perfect guard rail is the one you actually build." This doesn't change the underlying event → matcher → handler → outcome mechanism above; it changes only how the matcher and handler get written in the first place. Source: [[Hookify Claude Code Hook Creation Tool - Eric Grill]]

## Related concepts
- [[Deterministic Scripts]] — the handler a hook calls is typically one of these; the hook decides *when* to run it, the script defines *what* running it means.
- [[Six Harness Components]] — hooks are one implementation of "Validation & feedback" and can also enforce "Permissions & human approval" boundaries.

## Sources
- [[Use Hooks for Automatic Checks - AI Coding Course]]
- [[Hookify Claude Code Hook Creation Tool - Eric Grill]]
