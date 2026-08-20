---
title: Settings Merge Behavior
tags: [type/concept]
related: [[Configuration Scope]], [[Permission Boundaries]], [[Instructions vs Permissions]]
---

# Settings Merge Behavior

"Higher scope wins" is incomplete — a setting's data type determines how sources combine, not just which one wins.

## Combination rules

| Configuration shape | Combination behavior |
|---|---|
| Most scalar values | The highest-priority source that defines the key supplies the value; lower sources fill keys the higher source leaves unset |
| Most arrays | Concatenate and deduplicate entries across scopes |
| Permission arrays | Merge rules from every scope into one policy, then evaluate: `deny` checked before `ask`, then `allow` — first match wins |
| Documented exceptions | Follow the setting-specific rule instead of the general order |

## Why it matters

A user-level permission that allows a command and a project-level permission that denies a path both stay active — they merge into one policy rather than one replacing the other. This differs from a scalar setting like a UI toggle, where only one value can win. Before troubleshooting a conflict, identify which of these four shapes applies.

## Related concepts
- [[Configuration Scope]] — establishes which sources are even in play before this decides how they combine.
- [[Permission Boundaries]] — the deny/ask/allow evaluation order this table describes is what makes consequence-tiered permissions composable across scopes.

## Sources
- [[Choose User-Level or Project-Level Configuration - AI Coding Course]]
