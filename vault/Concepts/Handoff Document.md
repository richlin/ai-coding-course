---
title: Handoff Document
tags: [type/concept]
related: [[Statelessness]], [[Harness Engineering]], [[Issue Tracker as Durable Memory]]
---

# Handoff Document

A brief artifact written at the end of an agent session to let the next session reconstruct current state and choose the next action without access to the prior conversation.

## Required content

- **Goal** — the outcome the work is aimed at
- **Decision + rationale** — what was decided and why (or pointer to the ticket/ADR that holds it)
- **Files changed** — which files were edited
- **Checks run** — which verification commands ran and their results
- **Open questions** — unresolved uncertainties that block or shape the next action
- **Next action** — what to do first in the next session

## What to omit

A diary of every file opened, every failed search, or every draft response. The next agent needs current state, evidence behind it, and the next point of uncertainty — not a transcript.

## Verification criterion

A handoff is complete when a fresh agent — given only repository access and the handoff — can correctly summarize the current state and propose the next command before editing anything.

## Links, not copies

Link to durable artifacts (ticket, ADR, test file) instead of copying their full contents. The link ages better; copied content drifts.

## Beyond the session boundary

The same standard applies to any handoff, not only between sessions: across harnesses, repositories, or people. Write for a reader with repository access but no prior conversation. Lead with current state and next action rather than a chronological summary, separate verified facts from assumptions and recommendations, and state exactly which checks ran and their scope — "tests pass" without commands and scope isn't a fact. Don't hide blockers to make progress look cleaner, and update the handoff if work continues after writing it. Source: [[Handoffs Between Sessions Tools Repositories and People - AI Coding Course]]

A handoff across a session/tool/owner boundary should link to the [[Codebase Map]] and [[Task Specification|task spec]] rather than duplicate them — the handoff carries current state and next action; the map and spec remain the maintained sources for structure and requirements. Source: [[Create Codebase Navigation Artifacts - AI Coding Course]]

A [[Issue Tracker as Durable Memory|tracker]] holds durable state across a task's entire life, spanning many sessions; a handoff is the narrower artifact for one session-to-session transition within that longer life. Source: [[Using Issue Trackers as Durable Task Memory - AI Coding Course]]

Source: [[Statelessness - AI Coding Course]]
