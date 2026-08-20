---
title: vault — README
purpose: First page for anyone opening the vault
---

# vault

A personal knowledge vault owned by Lin Richuang.

## What this vault is

- **Synthesis**, not source. Original articles, papers, and decks live upstream.
- Organized into **topics** (domain-specific) and four **cross-topic layers**:
  Concepts, Sources, Questions, Insights.
- Single-user. Grows through on-demand ingestion.

## Where to start

| What you want | Go to |
|---|---|
| Current focus + recent activity | `00. Navigation/Dashboard.md` |
| A topic's content | `Topics/<topic>/_MOC.md` |
| All sources ingested | `Sources/_Sources index.md` |
| Open questions you're carrying | `Questions/_Questions.md` |
| Synthesized conclusions | `Insights/_Insights.md` |
| A specific concept | `Concepts/<name>.md` |
| Fleeting captures to process | `Inbox/` |

## How content gets in

| Command | What |
|---|---|
| `/ingest-article` | Article text from clipboard or file |
| `/ingest-webpage <url>` | Fetch a URL live |
| `/ingest-file <path>` | Local .pptx or .pdf |
| `/capture-note` | Quick fleeting idea → Inbox/ |
| `/weekly-review` | Synthesize + triage (Sundays) |
| `/monthly-health` | Structural maintenance (1st of month) |
| `/topic-search <query>` | Cross-vault search (read-only) |

## How to contribute manually

- **New concept:** `Templates/Template - Concept.md` → `Concepts/<name>.md`
- **New question:** `Templates/Template - Question.md` → `Questions/Q-NNN <title>.md`
  → row in `_Questions.md`
- **New insight:** `Templates/Template - Insight.md` → `Insights/I-NNN <title>.md`
  → row in `_Insights.md`
