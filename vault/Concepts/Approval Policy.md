---
title: Approval Policy
tags: [type/concept]
related: [[Permission Boundaries]], [[Escalation]], [[Six Harness Components]]
---

# Approval Policy

Setting where human approval is required based on impact, reversibility, confidence, and policy, rather than applying uniform caution to every action. Extends [[Permission Boundaries|the consequence-tier model]] into a concrete matrix: which actions run automatically, which merely notify, which require explicit approval, and which are prohibited outright.

## Why it matters

Autonomous execution can amplify a mistake quickly, so some boundary is necessary. But excessive approval prompts on routine, low-consequence steps train reviewers into careless, reflexive approval — the boundary has to be selective to stay meaningful.

## What a good approval policy looks like

Least privilege by default, with access expanded for a specific task rather than held open standing. Approval required for destructive, production, financial, legal, or sensitive-data actions. Approvers shown the proposed action, expected effect, evidence, and rollback plan — not a vague summary. Approvals that expire when the action or its supporting evidence changes.

## Common failure

Adding approval to every minor step. Requesting approval with a vague summary instead of concrete evidence. Reusing an old approval for a materially changed command. Letting the implementing agent approve its own accepted risk. Treating a notification as if it were approval.

## Related concepts
- [[Permission Boundaries]] — the underlying consequence-tier model this policy turns into a concrete, scored matrix.
- [[Escalation]] — the practice of actually returning a decision to a human at one of this policy's approval points.

## Sources
- [[Permissions and Human Approval - AI Coding Course]]
