---
title: Context Pruning
tags: [type/concept]
related: [[Smart Zone vs Dumb Zone]], [[Context Window]], [[Lost in the Middle]], [[Instruction Pruning]]
---

# Context Pruning

Sorting an active session's content into four buckets to cut bloat — information that no longer helps the current task — down to a smaller, higher-signal working set.

## The four-way sort

- **Keep** — active goal, latest decisions, current diff, failures, next check.
- **Summarize** — completed investigation, without retaining the raw output that produced it.
- **Externalize** — raw logs or research kept available outside the conversation (a file), not deleted, just not occupying the center of context.
- **Remove** — successful test logs already acted on, duplicate file reads, rejected proposals, resolved discussion.

## The test for each item

Does this affect the next two decisions? Not: is this old, or is this long. Evidence that explains a decision or is needed to reproduce a failure under active investigation is not bloat, however old — exact error messages and repro inputs stay.

## Common failure

Retaining raw output because collecting it was expensive, rather than because it's still useful; keeping both an old and a current plan active at once instead of marking the old one rejected.

## Related concepts
- [[Smart Zone vs Dumb Zone]] — pruning is one of the concrete interventions for staying in the smart zone rather than drifting into the dumb zone.
- [[Instruction Pruning]] — same instinct applied to the standing instruction set rather than one session's content.

## Sources
- [[Killing Bloat and Pruning - AI Coding Course]]
