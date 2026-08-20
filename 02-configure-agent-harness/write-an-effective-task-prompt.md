# Write an Effective Task Prompt

By the end of this lesson, you will be able to define an agent's assignment without prescribing a turn-by-turn implementation.

## A Prompt Defines the Current Assignment

A task prompt tells an agent what job to do in one run. It supplies the desired outcome, context that changes the work, boundaries that apply now, and evidence that will demonstrate success. The harness combines this assignment with standing project rules, repository context, tool results, and later feedback.

A prompt should give the agent a destination, not a turn-by-turn route. The useful question is not “Did I specify every step?” but “Did I make success and the important boundaries observable?”

## Close the Assignment Gap

Many weak prompts are not too short; they are too compressed. “Fix this” does not identify the observed problem, correct behavior, or evidence that would prove the fix. “Research context windows” names a topic but not the question, reader, decision, acceptable evidence, or deliverable.

The author may already carry those details and unconsciously read them back into the words. The agent receives only the fragment. The distance between the full task in the author's head and the task actually stated is the **assignment gap**.

An agent can fill that gap with plausible guesses and produce polished work for the wrong assignment. Fluency is not evidence of alignment. A minimum viable prompt therefore states:

- the observed problem or desired outcome;
- context and decisions the agent cannot discover;
- constraints that bound acceptable solutions; and
- observable evidence that would demonstrate success.

The prompt defines the assignment while leaving the agent room to inspect the repository, find existing patterns, and choose an implementation.

## Use a Stable Prompt Shape

Use this format rather than treating its parts as an optional menu:

```markdown
[Desired outcome]

Context that changes the work:
[Why, audience, or relevant background]

Constraints:
[Boundaries the agent must not cross]

Done when:
[Observable evidence]
```

Each field externalizes a part of the assignment the author might otherwise keep in their head: destination, consequential context, boundaries, and finish line. A stable shape also lowers the effort of starting a prompt because the author can copy it and fill in the decisions.

For example:

```text
Add CSV export to the existing orders page so support staff can download the currently filtered results.

Context that changes the work:
Support uses the export to investigate customer reports against the same order set visible in the UI.

Constraints:
Preserve the page's active filters and authorization checks. Do not add a dependency.

Done when:
The downloaded CSV matches the visible filtered results, unauthorized users receive the existing response, and focused tests and relevant checks pass.
```
