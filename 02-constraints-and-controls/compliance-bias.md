# Compliance Bias

## What It Means

- Coding agents are optimized to be helpful and may agree with a user's premise too quickly.
- An agent may implement a requested approach even when a safer or simpler option exists.
- Confident agreement does not prove that the requirement or design is correct.
- Agents tend to say "You are absolutely right."

## Why It Matters

- Unchallenged assumptions can become code, tests, and documentation before anyone notices.
- Senior-sounding output can make weak decisions harder to question.

## Best Practices

Treat the agent as an active partner, not an agreeable executor. Grant explicit permission to push
back on the proposed approach, challenge assumptions, flag contradictions, and explain what
evidence would change its recommendation.

- Ask, “What questions do you have?” before saying, “Just go build it.” This gives the agent room
  to identify an unclear goal instead of silently misinterpreting it.
- Ask the agent to list assumptions, risks, and alternatives before implementation.
- Request repository or primary-source evidence for technical claims.
- Separate the required outcome from the user's suggested implementation.
- Ask for the strongest objection when a decision is costly or hard to reverse.
- Encourage concise disagreement supported by evidence.

For example:

> Before making changes, ask me the questions you need answered. Identify your assumptions,
> challenge any questionable requirements, and explain risks or simpler alternatives. Do not
> proceed until the goal and constraints are clear.

This is one useful solution; other safeguards can work too, such as requiring an explicit question
round before implementation.

## Common Mistakes

- Do not use agreement as a quality signal; use evidence and engineering review.
- Do not ask leading questions that only confirm your preferred answer.
- Do not demand alternatives when one established repository pattern clearly controls the decision.
- Do not confuse engineering rigor with reflexive disagreement; challenge a proposal when it
  improves correctness, safety, maintainability, or decision quality.
- Do not accept confident or flattering language as evidence.

## Exercise

Use this exercise to compare an agreeable executor with an active engineering partner.

1. Pick a small, reversible change in the repository. For example: “Add Redis for login rate
   limiting.” Do not make the change yet.
2. Run this starter prompt exactly as written:

   > Add Redis for login rate limiting. Implement it now. Keep the response concise and do not
   > ask follow-up questions.

3. Save the response as **Attempt 1**. Do not evaluate it yet.
4. Start a new conversation and provide the same repository context. Run this prompt:

   > Act as an engineering partner, not an agreeable executor. Before making any changes, ask
   > the questions you need answered. Separate the required outcome from my proposed solution.
   > List your assumptions, identify contradictions or risks, and propose one simpler alternative.
   > Check the repository for relevant deployment, authentication, rate-limiting, and storage
   > patterns. Support technical claims with repository evidence or official documentation. Do
   > not implement anything until the goal and constraints are clear.
   >
   > Proposed change: Add Redis for login rate limiting.

5. Save the response as **Attempt 2**. Check whether it asks useful questions before proposing
   implementation details.
6. Verify each important claim in Attempt 2 by inspecting the repository or the cited official
   documentation. Mark each claim as **verified**, **uncertain**, or **unsupported**.
7. Compare the attempts using these questions:
   - Did the agent distinguish the requirement from the proposed implementation?
   - Did it identify assumptions about scale, deployment, or existing infrastructure?
   - Did it raise a concrete risk or contradiction?
   - Did it suggest a simpler option with engineering justification?
   - Did it ask questions that a human must answer before implementation?
8. Submit a short decision note with exactly three parts:
   - **Requirement:** State the actual outcome needed, separate from the proposed implementation.
   - **Evidence:** Record the repository or official-documentation evidence you verified, including
     at least one challenged assumption.
   - **Next action:** State whether to implement the proposal, revise it, or investigate further.

Your exercise is complete when the decision note separates the requirement from the proposed
solution and includes at least one evidence-backed challenge—not disagreement for its own sake.
