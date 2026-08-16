# Verifying Information Against Primary Sources

## What It Means

- A primary source is authoritative material from the technology owner, such as official documentation, specifications, or release notes.
- Model knowledge may be outdated, incomplete, or mixed across library versions.
- Source-driven work connects implementation choices to current documented behavior.

## Why It Matters

- APIs, recommended patterns, and defaults change over time.
- Plausible but obsolete code can compile poorly, create security risks, or increase maintenance cost.

## Concrete Example

- An agent suggests a CSV library API remembered from an older version.
- Check `package.json` and the lockfile to identify the installed version.
- Read the official versioned API reference and security notes for formula escaping and streaming.
- Record the relevant behavior in the spec or test; do not rely on the conversation retaining the documentation.

## Best Practices

- Check the project's actual dependency version first.
- Prefer official version-matched documentation over tutorials and snippets.
- Record the relevant constraint or link when it affects a lasting decision.
- Distinguish official docs, standards, release notes, source code, and third-party tutorials.
- Verify publication date and applicable version.
- Use source code or tests when official prose is ambiguous.
- Capture the conclusion and its applicability, not a large copied page.

## Common Mistakes

- Do not ask the model to remember current documentation when it can retrieve and verify it.
- Do not use search-result snippets as the final source.
- Do not follow current docs for a newer major version than the project uses.
- Do not assume a popular tutorial reflects secure defaults.
- Do not paste copyrighted documentation into project files when a concise decision and link suffice.

## Try It

1. Choose one version-sensitive API or configuration in your project.
2. Identify its installed version from the lockfile or tool output.
3. Ask the agent to explain the behavior before browsing.
4. Retrieve official version-matched documentation and, if needed, release notes or source.
5. List every difference between recollection and the source.
6. Update the implementation decision, test, or documentation with the verified conclusion and link.

## Expected Result

- A source note naming version, authoritative URL, verified behavior, and project consequence.
- At least one automated check where the documented behavior matters to correctness.
