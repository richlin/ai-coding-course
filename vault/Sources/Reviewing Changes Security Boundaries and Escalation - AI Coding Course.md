---
title: "Reviewing Changes, Security Boundaries, and Escalation"
author: AI Coding Course
type: essay
url:
file: 05-implement-and-verify/review-security-escalation.md
date: 2026-08-20
topics: [AI Coding]
tags: [type/source]
ingested: 2026-08-20
---

# Reviewing Changes, Security Boundaries, and Escalation — AI Coding Course

## Summary
Frames review as checking correctness, regression risk, maintainability, security, and scope against the actual diff and behavior — not the agent's summary of what it did — and escalation as handing a decision back to a human when impact is high or evidence is insufficient. Fluent, plausible-looking code can still hide authorization gaps or unsafe defaults, and agents should not be the ones accepting policy-sensitive risk.

## Key takeaways
- Review by risk in order: authorization, data exposure, injection, state changes, then maintainability — trace untrusted data across input, transformation, storage, and output boundaries.
- Validation is not authorization; confirming a value is well-formed says nothing about whether the caller was allowed to submit it.
- Escalate destructive actions, production access, unclear requirements, and any point where risk is being accepted rather than eliminated.
- A good escalation states the proposed behavior, the evidence, the risk, and the specific decision needed — not a generic "is this okay?"
- Separate fixable findings (fix now) from accepted-risk decisions (owned by someone accountable, with an explicit deadline) so risk acceptance isn't silently absorbed into the diff.

## Open questions it raises
- [OPEN] — none stated explicitly.

## Concepts touched
- [[Escalation]]
- [[Permission Boundaries]]

## Notable quotes
> "Do not let the implementing agent accept security or policy risk."

## My reaction
[OPEN] — not yet reviewed by Lin.
