# Skills, Prompts, Rules, Commands, Hooks, and Scripts

## What It Means

- A **prompt** is a task-specific instruction given in a conversation.
- A **rule** is persistent guidance applied at user or project scope.
- A **skill** is a reusable workflow with triggers, steps, and verification.
- A **command** starts a named workflow.
- A **hook** runs automatically at a defined event.
- A **script** performs deterministic operations that should not depend on model judgment.

## Why It Matters

- Choosing the right asset makes repeated behavior easier to maintain and verify.
- Not every recurring instruction needs a complex skill or agent.

## Concrete Example

- **Prompt:** “Review this one CSV helper for injection risk.”
- **Rule:** “All external data exports require authorization and formula-injection tests.”
- **Skill:** A repeatable export-security review with discovery, threat checks, and evidence output.
- **Command:** `/verify-export` starts the project workflow.
- **Hook/script:** Run a deterministic test or formatter before commit.

## Best Practices

- Use prompts for one-off work and rules for stable conventions.
- Use skills for repeated judgment-heavy procedures.
- Use scripts and hooks for deterministic enforcement or automation.
- Keep each asset focused on one responsibility.
- Use the least complex asset that reliably changes behavior.
- Give reusable assets owners and representative tests.
- Make outputs and stopping conditions explicit.
- Keep enforcement in deterministic tools when possible.

## Common Mistakes

- Do not encode deterministic formatting or validation as prose when a tool can enforce it.
- Do not turn every successful prompt into a skill.
- Do not use a rule for one temporary task requirement.
- Do not duplicate the same workflow in a command, skill, and script.
- Do not add automation without visible failure output.

## Exercise

1. Collect five repeated instructions from reviews or agent sessions.
2. Classify each as one-off prompt, stable rule, judgment workflow, named command, event hook, or deterministic script.
3. Explain frequency, variability, and enforcement needs.
4. Convert one objective instruction into an executable check.
5. Test that check on one passing and one failing example.

Complete the exercise when:

- An asset-selection table with no unnecessary abstraction.
- One repeated objective standard is now enforced automatically.
