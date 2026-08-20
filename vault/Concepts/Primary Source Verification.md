---
title: Primary Source Verification
tags: [type/concept]
related: [[Non-Determinism]], [[Task Specification]]
---

# Primary Source Verification

Checking a model's recalled API/library knowledge — which may be outdated, incomplete, or mixed across versions — against the project's actual installed version and current official documentation, before committing an implementation choice to it.

## Mechanism

A model can recall a plausible-sounding API that belonged to an older version of a library. The fix isn't to ask the model to "remember better" — it's to check the project's actual dependency version (lockfile) and retrieve official, version-matched documentation, release notes, or source code when prose is ambiguous.

## Practical discipline

Verify the publication date and applicable version of any doc consulted — docs for a newer major version than the project uses can actively mislead. Don't treat a search-result snippet or a popular tutorial as the final source, and don't assume a tutorial reflects secure defaults. Once verified, record the conclusion and its applicability (version, link, consequence) in the spec or a test — not in the conversation, which won't survive to the next session.

## Related concepts
- [[Non-Determinism]] — a model's confident-sounding but version-mismatched recall is a related but distinct failure from run-to-run output variance; both call for an external check rather than trusting the model's own confidence.

## Sources
- [[Verifying Information Against Primary Sources - AI Coding Course]]
