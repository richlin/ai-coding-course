# CI Enforcement and Safe Shipping

## What It Means

- Continuous integration runs shared checks whenever code changes.
- Safe shipping uses review, staged rollout, monitoring, and rollback to limit production risk.
- Agent-generated code follows the same delivery standards as human-written code.

## Why It Matters

- Local prompts and checks are easy to skip or configure differently.
- Production behavior can reveal failures that pre-merge tests cannot reproduce.

## Concrete Example

- A notification PR must pass unit, contract, migration, type, lint, build, and security checks.
- Review confirms consent behavior and rollout plan.
- A feature flag enables internal users first; dashboards monitor provider errors and preference violations.
- Rollback disables the flag and leaves the backward-compatible schema in place.

## Best Practices

- Run required tests, types, linting, builds, and security checks in CI.
- Protect important branches and require review for high-risk changes.
- Use feature flags or staged rollout where appropriate.
- Define rollback and post-release signals before deployment.
- Keep required local and CI commands aligned.
- Make checks risk-based and non-flaky.
- Separate deployment from release with flags when appropriate.
- Test rollback and migration compatibility before rollout.

## Common Mistakes

- Do not weaken CI to merge plausible agent output more quickly.
- Do not add CI gates no one owns or can reproduce.
- Do not deploy irreversible schema changes before compatible code.
- Do not call deployment complete before observing runtime signals.
- Do not rely on the agent's summary for release approval.

## Exercise

1. Trace one feature from local branch to production.
2. List checks, artifacts, owners, and approvals at each stage.
3. Add staged rollout, success thresholds, abort thresholds, and rollback action.
4. Verify every CI command can run or be understood locally.
5. Simulate one failed release signal and execute the rollback procedure in a safe environment.

Complete the exercise when:

- A delivery map with no unowned gate or hidden production step.
- Rollout and rollback have observable triggers and tested actions.
