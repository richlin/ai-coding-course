# AI Coding Course

This repository is a self-guided course about using coding agents reliably, from model and harness basics through team-scale workflows.

## Repository Map

- `README.md` is the course index and source of truth for module order.
- Numbered directories contain the lessons for each module.

## Writing Ground Rules

- Write direct, concrete Markdown for a technically capable reader.
- Explain the mechanism first, then the practical decision or tradeoff.
- Use examples that show observable consequences; avoid generic advice and marketing language.
- Distinguish adjacent concepts explicitly when readers could confuse them.
- Keep headings descriptive and paragraphs short. Use lists only when readers need to scan distinct items.
- Preserve the depth and structure of nearby lessons unless the task calls for a broader rewrite.
- Use relative links for files in this repository.
- When adding, moving, or renaming a lesson, update `README.md` in the same change.

## Sources and Claims

- Verify current product behavior, APIs, benchmarks, and tool support against primary sources.
- Prefer official documentation and research papers. Use secondary sources for perspective, not as the sole authority for technical claims.
- Add source links near time-sensitive or non-obvious claims, and keep the lesson's `References` section concise.
- Do not invent commands, measurements, repository behavior, or citations.

## Boundaries

- Preserve unrelated working-tree changes. Do not reformat or rewrite files outside the requested scope.
- Do not add dependencies, build tooling, generated files, or new repository-wide conventions without asking.
- Keep task-specific requirements and definitions of done in the task or specification, not in project ground rules.
- Never add secrets, credentials, private customer data, or copied production content.

## Verification

- Run `git diff --check` after Markdown edits.
- Check that every changed relative link resolves, including links added to `README.md`.
- Review the final diff for accidental edits, repeated material, and claims that need a source.
- This repository currently has no automated test or documentation build command; report manual checks performed instead of inventing one.


## Plan with grilling
When in plan mode or planning, use grilling skill by default
