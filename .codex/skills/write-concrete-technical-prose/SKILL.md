---
name: write-concrete-technical-prose
description: Write or revise technical articles in a direct, concrete, conversational engineering voice. Use for Markdown articles, documentation, course material, tutorials, and explainers that should teach mechanisms and tradeoffs without sounding like a policy framework, generic AI summary, or marketing copy. Trigger when the user asks to apply this style, make technical writing feel more human, explain a concept in plain language, or expand terse notes into a grounded article.
---

# Write Concrete Technical Prose

Write like an experienced engineer explaining a system to another capable person. Start with what the thing actually is, show how it behaves, and draw practical conclusions from that mechanism. Preserve technical precision without turning the article into a taxonomy or checklist.

## Build the Explanation

1. Identify the central distinction or mechanism the reader must understand.
2. Open with a concrete object, named example, or ordinary action. Do not begin with a dictionary definition or a list of abstract terms unless the user asks for a reference format.
3. Explain what happens in plain causal order: what goes in, what performs the work, what comes out, and what changes when a condition changes.
4. Connect the mechanism to a practical decision, failure mode, or tradeoff.
5. Add examples that differ in consequence, not examples that merely rename the same pattern.
6. End with a usable rule of thumb or decision habit. Avoid a generic recap that repeats every heading.

For a revision, preserve the article's claims and intended depth unless the user asks for a content change. Rewrite the explanatory path and voice rather than merely swapping words.

## Use the Voice

- Address the reader directly when it makes the reasoning clearer.
- Prefer concrete nouns and active verbs: "the harness runs the command" instead of "command execution is facilitated."
- Make confident, qualified claims. Say "more effort helps when the problem rewards careful reasoning" instead of "higher effort may potentially be beneficial."
- Use contractions sparingly where they sound natural.
- Use technical terms when they sharpen a distinction, then explain them through behavior.
- Vary paragraph length, but keep most paragraphs to two to four sentences.
- Use occasional analogy only when it compresses a real tradeoff. Do not decorate the article with metaphors.
- Let one sentence carry emphasis through wording. Do not rely on constant bold text, callouts, or slogans.

Aim for the tone of a thoughtful technical conversation: direct without being abrupt, opinionated without pretending tradeoffs do not exist, and accessible without talking down to the reader.

## Use Paragraphs and Bullets Deliberately

Use short paragraphs for explanation, causality, and argument. Use bullets only when the reader is choosing among real alternatives, checking several concrete conditions, or scanning examples that belong together.

When using bullets:

- Introduce the list with a sentence that explains why the items belong together.
- Make each item specific enough to teach something.
- Allow a bullet to contain two related sentences when the consequence needs explanation.
- Avoid forcing every item into the same grammatical mold.
- Avoid bold-label bullets when an ordinary sentence reads more naturally.

Do not turn the whole article into bullets. If the reader must infer the argument by joining list items, move that argument into prose.

## Ground Abstract Claims

Follow an abstract claim with evidence the reader can picture: an operation, a failure, a comparison, or a small scenario.

Prefer:

> A lightweight model can answer quickly and still be the slow choice if an engineer has to repair the result three times.

Avoid:

> Teams should evaluate latency holistically across the end-to-end workflow.

Prefer:

> A model cannot read a repository on its own. The harness reads the file, puts its contents into the request, and asks the model what to do next.

Avoid:

> Harnesses enable agentic capabilities through tool orchestration.

Use named products or realistic tasks when they make the concept easier to recognize. Do not invent current prices, capabilities, or version-specific behavior; verify time-sensitive claims or keep the example generic.

## Explain Tradeoffs Instead of Issuing Rules

Give the reason behind advice. Replace "always" and "never" with the condition that makes the advice true, except for genuine safety or correctness requirements.

Cover both sides of an important choice:

- State what an option buys.
- State what it costs.
- Explain when that exchange is worth making.
- Name the common case where the advice stops working.

Distinguish neighboring concepts carefully. If readers often confuse a model with a harness, response latency with time to accepted work, or token price with total cost, make that distinction part of the explanation rather than a glossary aside.

## Remove the Generic AI Voice

Revise any passage that shows several of these habits:

- Opens with "In today's rapidly evolving landscape" or another scene-setting cliché
- Defines five abstract terms before giving the reader anything concrete
- Repeats the same point under "What It Means," "Why It Matters," and "Best Practices"
- Uses symmetrical sections and equal-length bullets even when the subject does not call for them
- Adds labels such as "Key Consideration" or "Important Note" instead of writing a clear sentence
- Uses inflated phrases such as "leverage," "facilitate," "robust," "seamless," or "holistic" where an ordinary verb works
- Says an option "depends on your needs" without naming the needs
- Treats every recommendation as equally important
- Restates the introduction in a conclusion without adding a useful rule of thumb
- Sounds certain about facts that require evidence or current documentation

Do not solve these problems by making every sentence terse. The target is natural explanation, not clipped minimalism.

## Final Pass

Before delivering the article:

1. Read the opening and confirm that it starts with the subject itself rather than commentary about the subject.
2. Check that each section advances the explanation instead of restating an earlier section.
3. Replace abstract nouns with actors and actions where possible.
4. Turn any bullet sequence that carries an argument into prose.
5. Confirm that examples reveal a mechanism or consequence.
6. Remove throat-clearing, generic transitions, repeated conclusions, and unnecessary emphasis.
7. Check technical claims, preserve necessary nuance, and mark uncertainty honestly.
8. Match the user's requested format, length, terminology, and existing document conventions.
