---
title: Task Specification
tags: [type/concept]
related: [[Task Boundary]], [[Acceptance Checks]], [[Assignment Gap]], [[Codebase Map]], [[Specification Lifecycle]], [[Team Ground Rules]]
---

# Task Specification

A task contract — outcome, boundaries, constraints, examples, and acceptance criteria for one piece of work — that keeps an agent's implementation freedom inside an agreed behavioral boundary, without prescribing an implementation it hasn't researched.

```
same vague request  -> different inferred requirements -> incompatible implementations
same specification   -> different valid designs         -> same accepted behavior
```

## What it is not

Not automatically executable — prose becomes enforceable only when its acceptance criteria point to tests, commands, or explicit manual checks that can reject an incorrect implementation. Not an implementation plan: the spec says what must remain true; the plan says how this repository will change to make it true. Establish the boundary first, then let repository research refine constraints and shape the plan.

## Feature vs. bug-fix specs need different evidence

| Feature specification | Bug-fix specification |
|---|---|
| Starts with a user problem or capability | Starts with reproducible incorrect behavior |
| Defines the new behavioral boundary | Contrasts observed and expected behavior |
| Uses examples to resolve possible interpretations | Uses a minimal failing input to anchor diagnosis |
| Accepts any design that satisfies the boundary | Requires regression protection for the reproduced failure |

For a bug fix specifically: record the observed defect and safe expected output before choosing a repair. "Prefix dangerous CSV cells with an apostrophe" is one possible fix; "a customer name beginning with `=` opens as a spreadsheet formula" is the defect. Naming the fix first risks mistaking one repair for the actual requirement.

## What belongs in it

Context (why the behavior exists), goal and non-goals (scope), constraints (what rules out unacceptable solutions), examples (concrete formats/edge cases), acceptance criteria (what "done" means), and open questions (unresolved product decisions kept visible rather than silently handed to the agent). Link to relevant code/tests/issues; don't paste large repository excerpts or duplicate standing rules that already have a clear source elsewhere.

## Match detail to the cost of being wrong

Not every task needs a full document. Use a fuller spec when a wrong interpretation is expensive to reverse, the work crosses sessions or owners, several systems must agree, or review needs a durable statement of intent. A small, reversible edit may need only a task prompt with precise acceptance criteria. Stop adding detail once an implementer can plan without inventing a product decision and a reviewer can reject behavior outside the boundary — more detail past that point makes the spec brittle without making the outcome clearer.

## Verifying a spec before implementation

Give it to a peer or fresh agent and ask for a plan plus unresolved decisions:
- Invents user-visible behavior, limits, or data semantics → the spec is incomplete, or that decision needs explicit delegation.
- Picks a different internal design that still satisfies every criterion → the spec is appropriately flexible.
- Two reviewers could disagree whether a criterion passed → rewrite it around observable input/output.
- No test, command, inspection, or manual procedure can check a criterion → it's an aspiration, not a stopping condition.

## Related concepts
- [[Task Boundary]] — the intent/assumptions/constraints/non-goals framework that fills the spec's boundary section.
- [[Acceptance Checks]] — what turns the spec's criteria from prose into something that can actually fail.
- [[Assignment Gap]] — the problem a specification exists to close at the task level, the way [[Starting Context]] closes it at the session-brief level.
- [[Codebase Map]] — the spec tells an agent what to verify; the map tells it where to look. Neither substitutes for the other.
- [[Specification Lifecycle]] — what happens to this artifact after it's written.
- [[Team Ground Rules]] — the standing, repository-scoped counterpart: a spec is "what this task must achieve," a ground rule is "how we work here."

## Sources
- [[Writing Feature and Bug-Fix Specifications - AI Coding Course]] — primary source.
- [[Create Codebase Navigation Artifacts - AI Coding Course]]
- [[Intent Assumptions Constraints and Non-Goals - AI Coding Course]]
- [[Acceptance Criteria and Goal Commands - AI Coding Course]]
