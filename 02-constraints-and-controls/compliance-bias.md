# Compliance Bias

## What It Means

- Coding agents are optimized to be helpful and may agree with a user's premise too quickly.
- An agent may implement a requested approach even when a safer or simpler option exists.
- Confident agreement does not prove that the requirement or design is correct.

## Why It Matters

- Unchallenged assumptions can become code, tests, and documentation before anyone notices.
- Senior-sounding output can make weak decisions harder to question.

## Concrete Example

- A developer says, “Add Redis because login rate limiting must be distributed.”
- A compliant agent immediately adds a Redis dependency and configuration.
- An active partner checks whether the app has multiple instances, whether a gateway already limits traffic, and whether an existing store should be reused.
- A useful challenge is: “Redis fits multiple instances, but this repository currently deploys one. Should we optimize for today's architecture or a confirmed scale-out plan?”

## Best Practices

- Ask the agent to list assumptions, risks, and alternatives before implementation.
- Request repository or primary-source evidence for technical claims.
- Separate the required outcome from the user's suggested implementation.
- Ask for the strongest objection when a decision is costly or hard to reverse.
- Encourage concise disagreement supported by evidence.

## Common Mistakes

- Do not use agreement as a quality signal; use evidence and engineering review.
- Do not ask leading questions that only confirm your preferred answer.
- Do not demand alternatives when one established repository pattern clearly controls the decision.
- Do not turn active partnership into automatic disagreement.
- Do not accept confident or flattering language as evidence.

## Try It

1. Choose a reversible decision, such as adding a dependency for a small feature.
2. Write a prompt that confidently proposes a questionable implementation.
3. Run it once normally and save the response.
4. Run it again asking for assumptions, the strongest objection, evidence to inspect, and one simpler alternative.
5. Verify every important claim against code or official documentation.
6. Compare which response better supports a human decision.

## Expected Result

- A short decision note separating the requirement from the proposed solution.
- At least one challenged assumption backed by evidence rather than disagreement alone.
