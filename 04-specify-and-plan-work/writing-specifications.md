# Writing Feature and Bug-Fix Specifications

You will learn to write a specification that bounds an agent's decisions without prescribing an implementation it has not researched.

## A Vague Request Produces Plausible but Incompatible Work

Suppose you ask two agents to “add CSV export to the orders page.” One exports every order the user can access. The other exports only the filtered rows on screen. Both implementations are plausible because the request does not define which behavior is correct.

More prompting does not reliably solve this problem if the missing decisions remain implicit. The agent still has to infer the user, scope, security boundary, output rules, and stopping condition. A specification makes those decisions reviewable before they become code.

```text
same vague request -> different inferred requirements -> incompatible implementations
same specification -> different valid designs -> same accepted behavior
```

The goal is not identical code. The goal is to keep implementation freedom inside an agreed behavioral boundary.

## A Specification Is a Task Contract

A useful specification records the outcome, boundaries, constraints, examples, and acceptance criteria for one piece of work. It reduces the number of consequential decisions the implementing agent must invent.

This makes the specification a **task contract** between the requester, implementer, and reviewer. It is not automatically an executable contract. Prose becomes enforceable only when acceptance criteria point to tests, commands, or explicit manual checks that can reject an incorrect implementation.

A specification is also not an implementation plan. The specification says what must remain true; the plan says how this repository will be changed to make it true. Establish the known behavioral boundary before implementation planning, then let repository research refine constraints and shape the plan.

## Feature and Bug-Fix Specifications Need Different Evidence

Both kinds of specification define expected behavior, but they begin from different evidence.

| Feature specification | Bug-fix specification |
| --- | --- |
| Starts with a user problem or capability | Starts with reproducible incorrect behavior |
| Defines the new behavioral boundary | Contrasts observed and expected behavior |
| Uses examples to resolve possible interpretations | Uses a minimal failing input to anchor diagnosis |
| Accepts any design that satisfies the boundary | Requires regression protection for the reproduced failure |

Do not turn a symptom into a premature solution. “Prefix dangerous CSV cells with an apostrophe” may be one fix. “A customer name beginning with `=` opens as a spreadsheet formula” is the observed defect. Record the defect and safe expected output before choosing the repair.

## Build the Contract Around Observable Behavior

For the CSV export feature, a compact specification could contain:

- **Context:** Finance users reconcile orders in a spreadsheet after filtering by date and status.
- **Goal:** An authorized user can download the currently filtered order set as CSV.
- **Non-goals:** Scheduled exports, PDF output, and cross-organization exports.
- **Constraints:** Existing order authorization applies; timestamps use UTC; spreadsheet-formula prefixes must be neutralized.
- **Examples:** A customer name of `=2+2` must be emitted as inert text, not an executable formula.
- **Acceptance criteria:** The file contains the filtered rows, unauthorized requests return `403` without generating a file, and dangerous cell prefixes are safely encoded.
- **Open questions:** Whether the current 10,000-row limit applies to exports, with an owner for resolving it.

Each section closes a different decision. Context explains why the behavior exists. Goals and non-goals bound scope. Constraints rule out unacceptable solutions. Examples make formats and edge cases concrete. Acceptance criteria define completion. Open questions keep unresolved product decisions visible instead of handing them silently to the agent.

Link to relevant code, tests, issues, or decisions when those anchors help research. Do not paste large repository excerpts into the specification or duplicate standing project rules that already have a clear source of truth.

## Match the Specification to the Cost of Being Wrong

Not every task needs a detailed document. Use a fuller specification when a wrong interpretation would be expensive to reverse, the work crosses sessions or owners, several systems must agree, or review needs a durable statement of intent.

A small, reversible edit may need only a task prompt with precise acceptance criteria. Exploratory work may need a hypothesis and time boundary rather than fixed requirements. The decision rule is whether important ambiguity must be resolved before implementation, not whether the task sounds like a “feature.”

Stop adding detail when another implementer can plan the work without inventing a product decision and a reviewer can reject behavior outside the boundary. More implementation detail after that point can make the specification brittle without making the outcome clearer.

## Verify the Specification Before Implementation

Give the specification and repository to a peer or fresh agent, then ask for a plan and a list of unresolved decisions. Inspect the response:

- If it invents user-visible behavior, authorization rules, limits, or data semantics, the specification is incomplete or the decision should be explicitly delegated.
- If it chooses a different internal design that still satisfies every criterion, the specification is appropriately flexible.
- If two reviewers could disagree about whether a criterion passed, rewrite it around observable input and output.
- If no test, command, inspection, or manual procedure can check a criterion, it is an aspiration rather than a stopping condition.

## References

- [Augment Code: What Is Spec-Driven Development?](https://www.augmentcode.com/guides/what-is-spec-driven-development)
