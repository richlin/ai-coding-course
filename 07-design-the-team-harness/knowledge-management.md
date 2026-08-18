# Context and Knowledge Management

## What It Means

- Context management selects the information needed for the current decision.
- Knowledge management preserves reliable information for future work.
- Sources include code, tests, docs, tickets, decisions, memory, and external documentation.

## Why It Matters

- Agents need current, authoritative information without receiving every available document.
- Unowned knowledge becomes stale and can repeatedly mislead work.

## Concrete Example

- Code and tests own current notification behavior.
- An ADR owns the provider-adapter decision.
- The issue tracker owns delivery state and blockers.
- Official provider docs own current external API behavior.
- Repository search retrieves these sources on demand instead of injecting a permanent documentation dump.

## Best Practices

- Name a source of truth for requirements, code behavior, decisions, and task state.
- Keep durable knowledge close to the system it describes.
- Load information on demand through search and tools.
- Assign ownership and review dates to manually maintained knowledge.
- Define source precedence for conflicting facts.
- Index or structure knowledge around real retrieval questions.
- Keep sensitive data out of general agent context.
- Measure whether retrieved material improves task outcomes.

## Common Mistakes

- Do not create a large knowledge base without a freshness and retrieval strategy.
- Do not copy code behavior into prose that will drift.
- Do not treat all sources as equally authoritative.
- Do not retrieve broad documents when a symbol or section answers the question.
- Do not persist customer or secret data as reusable context.

## Exercise

1. Choose one recurring workflow and list ten facts agents need.
2. Map each fact to source, owner, lifetime, sensitivity, and retrieval method.
3. Resolve duplicates by naming one source of truth.
4. Add a freshness rule for external or manually maintained facts.
5. Test three realistic retrieval questions with a fresh agent.

Complete the exercise when:

- A knowledge map with authority, ownership, and retrieval paths.
- The agent finds current facts without loading an entire knowledge base.
