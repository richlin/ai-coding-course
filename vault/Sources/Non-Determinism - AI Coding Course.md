---
title: Non-Determinism
author: AI Coding Course
type: essay
url:
file: 01-ai-coding-system/non-determinism.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Non-Determinism — AI Coding Course

## Summary
Explains why the same prompt can produce different implementations across runs and how to build workflows that tolerate this. The goal is not to force identical output but to put deterministic checks at the end of each path. Agent output should be thought of as a distribution, not a fixed capability.

## Key takeaways
- Non-determinism arises from token sampling randomness plus provider infrastructure variation plus context/environment differences.
- One successful run proves the workflow *can* produce acceptable output — not how often it will.
- Differences between runs are harmless, beneficial, or acceptance-breaking. Only the last category must be eliminated.
- Put determinism in the checks (tests, types, linters, review), not in forcing identical implementations.
- Retry once for a bad draw; investigate a systematic failure (all runs miss the same constraint → fix the prompt/environment).
- Don't turn short streaks of good/bad runs into trend conclusions without controlled repeats.

## Open questions it raises
- How many repeated runs under controlled conditions constitute reliable evidence about a workflow's success rate?

## Concepts touched
- [[Non-Determinism]]
- [[Acceptance Checks]]

## Notable quotes
> "Think of an agent's output as a distribution, not a fixed capability. Many runs may land in an acceptable middle, while an occasional run is unusually good or badly off target. The tails matter because production workflows eventually encounter them." (One Passing Run Is One Sample)

> "same request → different implementations → same acceptance checks" (opening diagram)

## My reaction
The distribution framing is the key insight. The practical corollary — retry once, investigate a pattern — is the most actionable advice. The streak-interpretation warning is important for practitioners who anthropomorphize model quality changes.
