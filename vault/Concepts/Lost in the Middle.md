---
title: Lost in the Middle
tags: [type/concept]
related: [[Context Window]], [[Statelessness]]
---

# Lost in the Middle

Within a model's context window, content near the start and near the end of the message history gets more attention than content in the middle — and the effect grows worse as the window fills.

## Mechanism

Attention across a long input is not uniform. Early messages (system prompt, initial framing) and the most recent messages both carry disproportionate weight in shaping the output; material placed in between is more likely to be under-weighted or missed, even though it is technically "in context."

## Consequence

Simply fitting information into the context window does not guarantee the model will use it. A fact placed in the middle of a long session or a long document is at higher risk of being effectively ignored than the same fact placed near the start or end.

## Related concepts
- [[Context Window]] — this is the mechanism behind that concept's "bigger isn't simply better" caveat.

## Sources
- [[What Is The Context Window - Matt Pocock]]
