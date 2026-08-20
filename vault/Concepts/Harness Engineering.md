---
title: Harness Engineering
tags: [type/concept]
related: [[Model vs Harness]], [[Six Harness Components]], [[Instructions vs Permissions]], [[Permission Boundaries]]
---

# Harness Engineering

The work of designing and building the environment that lets coding agents carry out development tasks reliably while keeping their changes reviewable, governable, and reusable.

## Why it matters

AI-assisted development makes two team problems more acute:
1. An ambiguous requirement can become code before the misunderstanding is discovered.
2. Higher change volume makes production risks harder to catch early or trace after failure.

A good harness places engineering judgment where the agent can use it and where the team can inspect or enforce it.

## How to build one

Start with one recurring workflow rather than a broad platform project. Give it enough of the six components to reach a trustworthy stopping point. Improve the component implicated by real failures.

**Avoid** adding components without a job: memory needs a decision about what may persist; a tool needs a workflow and permission boundary; a rule needs a place where it applies without contradicting another.

## Evidence that the harness dominates

Two reported cases changed only the harness, not the model, and got large measured gains: a team moved a Terminal Bench 2.0 ranking from outside the top 30 to top 5 through harness changes alone, and a LangChain experiment added 13.7 benchmark points through system-prompt and middleware changes. Source: [[The New Software Lifecycle - Addy Osmani]]

## Ownership

A well-designed harness has visible ownership: a team can say who maintains the authentication test template or the deployment approval rule. Duplicate instructions drifting across prompts, skills, and documentation are a maintenance problem. [[Instruction Budget]] is the concrete practice that keeps this from happening in the standing instruction file itself: a size ceiling, a belongs/doesn't-belong test per line, and triggered links instead of inlined documentation. Source: [[Write a Good AGENTS.md - AI Coding Course]]

Source: [[Harnesses Agents and Models - AI Coding Course]]
