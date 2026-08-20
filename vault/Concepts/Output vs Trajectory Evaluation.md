---
title: Output vs Trajectory Evaluation
tags: [type/concept]
related: [[Acceptance Checks]], [[Vibe Coding vs Agentic Engineering]]
---

# Output vs Trajectory Evaluation

Two distinct questions to ask when checking an agent's work.

## The distinction

**Output evaluation** — is the result correct? Checks the artifact: does the test pass, does the API return the right shape, does the diff do what was asked.

**Trajectory evaluation** — was the reasoning path sound? Checks the process that produced the artifact: did the agent consult the right files, did it skip a step that happened to not matter this time, would the same reasoning generalize.

## Why the distinction matters

An agent can reach a correct output through unsound reasoning — e.g., it copies a pattern from an unrelated file that happens to work here but will fail on the next similar task. Output evaluation alone would pass this; trajectory evaluation catches it.

Conversely, sound trajectory with a wrong final output usually means a narrow, fixable slip rather than a systemic harness problem.

## Related concepts
- [[Acceptance Checks]] — the deterministic-check machinery that typically implements output evaluation; trajectory evaluation is harder to make deterministic and often leans on human review.

## Sources
- [[The New Software Lifecycle - Addy Osmani]]
