# Model Selection, Effort, Latency, and Cost

## What It Means

- **Model Capability** is the model's ability to reason about and perform the task.
- **Effort** is the amount of reasoning or work allocated to the response.
- **Latency** is how long you wait for a useful result.
- **Cost** includes model usage, engineer review time, retries, and mistakes.
- The best choice is the least expensive setup that reliably handles the task's risk and complexity.

## Why It Matters

- A fast model can be ideal for search or formatting but unreliable for architectural decisions.
- A powerful model is wasteful when a deterministic tool or smaller model can do the job.
- Cheap output becomes expensive when engineers must repeatedly repair it.

## Concrete Example

- **Low risk:** Rename a private variable and run a focused test. Use a fast model with normal effort.
- **Medium risk:** Add rate limiting by following an existing middleware pattern. Use a capable coding model with medium effort.
- **High risk:** Design distributed limiting across services with abuse requirements. Use a stronger reasoning model, high effort, and human review.
- A 10-second answer requiring 30 minutes of repair costs more than a 60-second answer that passes review immediately.

## Best Practices

- Use lower-cost models for bounded, reversible, easily checked tasks.
- Use stronger models for ambiguous, high-risk, or cross-system reasoning.
- Increase effort only when the task benefits from deeper reasoning.
- Match effort to uncertainty and consequence, not requested line count.
- Compare total time to verified completion, including retries and review.

## Common Mistakes

- Do not select models by reputation alone; test them on representative tasks with the same harness and checks.
- Do not use high effort for deterministic formatting, search, or command execution.
- Do not choose the cheapest model for security or migration work merely because the diff is small.
- Do not compare models with different tools, context, or repository states.
- Do not assume higher effort repairs an unclear specification.
