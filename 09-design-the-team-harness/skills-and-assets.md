# Skills and Reusable Assets

## What It Means

- Reusable assets standardize workflows that the team performs repeatedly.
- Examples include skills, templates, scripts, review rubrics, task commands, and checklists.
- Good assets encode proven practice without hiding important decisions.

## Why It Matters

- Teams can improve one shared workflow instead of rewriting prompts for every task.
- Standard outputs make review, handoff, and evaluation easier.

## Concrete Example

- A notification-feature template captures intent, channels, defaults, consent, tenant boundaries, and rollout.
- A security-review skill checks authorization, sensitive content, provider failure, unsubscribe behavior, and logging.
- A deterministic script validates event schemas.
- A review rubric standardizes evidence expected before merge.

## Best Practices

- Build assets from observed repetition and failure, not hypothetical needs.
- Give each asset an owner, scope, version, and test examples.
- Keep deterministic work in code and judgment-heavy work in skills or rubrics.
- Remove assets that no longer improve outcomes.
- Build assets from repeated successful practice and observed failures.
- Assign owner, version, scope, and test cases.
- Keep deterministic logic in scripts.
- Measure adoption and correction rate rather than asset count.

## Common Mistakes

- Do not measure success by the number of skills or templates the team creates.
- Do not create assets for one-time problems.
- Do not hide important judgment behind automatic commands.
- Do not let templates accumulate optional sections nobody uses.
- Do not leave reusable assets untested after workflow changes.

## Exercise

1. Select a workflow completed at least three times.
2. Separate fixed data, deterministic operations, judgment steps, and approval decisions.
3. Assign each to template, script, skill, rubric, or human owner.
4. Build the smallest missing asset.
5. Test it on normal, edge, and unrelated cases.
6. Record whether it reduces errors or review effort.

Complete the exercise when:

- One tested asset with a clear responsibility and owner.
- Evidence it improves a real workflow rather than adding ceremony.
