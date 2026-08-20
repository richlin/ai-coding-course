---
title: Skill Design and Testing
tags: [type/concept]
related: [[Slash Commands vs Skills]], [[Six Harness Components]], [[Acceptance Checks]], [[Reusable Team Assets]]
---

# Skill Design and Testing

A skill packages a recurring workflow so an agent recognizes and follows it consistently — but a written procedure isn't proven until it's tested against real cases.

## What a good skill defines

- When to activate — and, just as important, when *not* to (non-trigger examples).
- What evidence to gather.
- Ordered steps to follow.
- Stopping conditions and how to verify completion.
- A concrete, reviewable output (e.g., a severity-ordered finding list with evidence), not just "review the change".

## Testing checks behavior, not prose quality

Untested instructions may sound thorough while adding no reliable behavior. Test a skill the same way three times: a normal case, an edge case, and a case that should *not* trigger it — run all three without manual hints and compare the output against a human-made rubric. Revise only the instructions tied to an observed failure.

## Common mistakes

- A broad "do everything well" skill with vague steps.
- Omitting non-trigger examples, so the skill fires when it shouldn't.
- Encoding commands that differ across repositories without checking first.
- Trusting a skill because it reads well, rather than because it was tested.
- Letting a review-role skill silently change code.

## Related concepts
- [[Slash Commands vs Skills]] — the mechanism this concept is designing well.
- [[Reusable Team Assets]] — the broader category a skill belongs to, alongside templates, scripts, and rubrics.

## Sources
- [[Write and Test a Skill - AI Coding Course]]
