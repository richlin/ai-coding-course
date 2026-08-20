---
title: Six Harness Components
tags: [type/concept]
related: [[Harness Engineering]], [[Model vs Harness]], [[Instructions vs Permissions]], [[Permission Boundaries]]
---

# Six Harness Components

The six components that form a harness control loop. A reliable workflow usually needs all six; each has a distinct responsibility.

| Component | Job |
|---|---|
| **Ground rules & specs** | Goals, constraints, standards, acceptance criteria, execution order |
| **Context & knowledge** | Information available per request; durable project knowledge retrievable by the harness |
| **Tools & integrations** | Operations for inspecting or changing the environment; connections to external systems |
| **Skills & reusable assets** | Packaged procedures and starting material for repeated workflows |
| **Permissions & human approval** | Which actions the harness may perform; deliberate stopping points before high-consequence actions |
| **Validation & feedback** | Checks whether work meets spec; returns evidence to the agent or team to inform the next action |

## Progressive disclosure for skills

Skills & reusable assets can be layered by cost: metadata visible at startup, full instructions loaded only when a task matches, and heavy reference material loaded only when actually needed. This keeps the always-on context cheap while still making deep material available on demand. Source: [[The New Software Lifecycle - Addy Osmani]]

## Validation closes the loop

Without validation, the agent can produce changes but cannot establish that they work or know when to stop. A failed test should re-enter the loop as concrete feedback.

## Context quality over quantity

More context is not automatically better. Irrelevant logs and stale notes consume attention and can obscure the one constraint that matters. Supply the smallest body of evidence that lets the model make the next decision correctly.

This holds even when the [[Context Window]] has room to spare: retrieval degrades as the window fills, and content in the middle of a long history gets less attention regardless ([[Lost in the Middle]]). Fewer, more relevant tokens outperform more tokens. Source: [[What Is The Context Window - Matt Pocock]]

## Where components get engineered in practice

- **Ground rules & specs** — sized and placed deliberately; see [[Instruction Budget]] for the concrete discipline (line ceiling, triggered links, subtree scoping).
- **Skills & reusable assets** — designing and testing one well is its own discipline; see [[Skill Design and Testing]] and the adjacent [[Slash Commands vs Skills]] distinction.
- **Validation & feedback** — [[Hooks]] and [[Deterministic Scripts]] are the two mechanisms that most often implement this component without depending on model judgment.
- **Context & knowledge** — [[Starting Context]] is the per-task instance of this component: enough for the first decision, not the whole system; [[Durable Artifacts vs Auto-Memory]] is the cross-session instance: which store should own a given fact. [[Codebase Map]] is the reusable-across-tasks instance: where does this behavior enter, flow, and get verified.
- **Ground rules & specs** — [[Task Specification]] is this component's per-task instance: outcome, boundaries, constraints, acceptance criteria for one change, distinct from the always-loaded standing brief. [[Task Decomposition]] sequences a specification into small, independently verifiable tasks.

Source: [[Use Hooks for Automatic Checks - AI Coding Course]], [[Write Deterministic Scripts - AI Coding Course]], [[Write and Test a Skill - AI Coding Course]], [[Write a Good AGENTS.md - AI Coding Course]]

## Scaling each component to a team

- **Ground rules & specs** — [[Team Ground Rules]] scales the individual AGENTS.md practice to shared ownership and explicit precedence across a team.
- **Context & knowledge** — [[Source of Truth Mapping]] names one authoritative source per kind of fact and retrieves it on demand instead of holding a static copy.
- **Tools & integrations** — [[Tool and Integration Design]] treats inputs, outputs, permissions, error handling, and observability as first-class design decisions.
- **Skills & reusable assets** — [[Reusable Team Assets]] is the broader category [[Skill Design and Testing]] belongs to, spanning templates, scripts, rubrics, and checklists.
- **Permissions & human approval** — [[Approval Policy]] turns [[Permission Boundaries]] into a concrete matrix of automatic / notify / approve / prohibited actions.
- **Validation & feedback** — [[Harness Observability]] is the standing infrastructure; [[Harness Retrospective]] is how an observed signal actually becomes a harness change. [[Safe Shipping Pipeline]] applies the same loop specifically to CI and release.

Source: [[Scaling Ground Rules and Specifications Across a Team - AI Coding Course]], [[Context and Knowledge Management - AI Coding Course]], [[Tools and Integrations - AI Coding Course]], [[Skills and Reusable Assets - AI Coding Course]], [[Permissions and Human Approval - AI Coding Course]], [[Validation Observability and Feedback - AI Coding Course]], [[Feeding Lessons Back into the Harness - AI Coding Course]], [[CI Enforcement and Safe Shipping - AI Coding Course]]

Source: [[Harnesses Agents and Models - AI Coding Course]]
