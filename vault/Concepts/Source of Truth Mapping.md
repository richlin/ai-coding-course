---
title: Source of Truth Mapping
tags: [type/concept]
related: [[Codebase Map]], [[Durable Artifacts vs Auto-Memory]], [[Six Harness Components]]
---

# Source of Truth Mapping

Naming, for each kind of fact an agent needs (requirements, code behavior, decisions, task state, external API behavior), exactly one authoritative source and retrieving it on demand — instead of injecting a permanent documentation dump that goes stale and competes with the code it describes.

## Context vs. knowledge management

Context management selects what's needed for the current decision. Knowledge management preserves reliable information for future decisions. Both fail the same way if a fact has no named owner: it goes stale silently and repeatedly misleads whoever reads it next.

## What good mapping looks like

Code and tests own current behavior. An ADR owns a past decision and its rationale. The issue tracker owns delivery state and blockers. Official external docs own current third-party API behavior. Search and tools retrieve these on demand rather than the harness holding a static copy. Precedence is defined for when sources appear to conflict, and sensitive data is kept out of general agent context.

## Common failure

Building a large knowledge base with no freshness or retrieval strategy. Copying code behavior into prose that will drift from the code. Treating every source as equally authoritative. Retrieving a broad document when one symbol or section would answer the question. Persisting customer or secret data as reusable context.

## Related concepts
- [[Codebase Map]] — the source-of-truth artifact specifically for "where does this behavior live and how is it verified."
- [[Durable Artifacts vs Auto-Memory]] — the same naming discipline applied to which store — ticket, ADR, or private memory — should hold a given fact.

## Sources
- [[Context and Knowledge Management - AI Coding Course]]
