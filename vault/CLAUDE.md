# CLAUDE.md — vault

This file is the persistent context every Claude Code session in this vault must read first.

## What this vault is

**vault** — a personal knowledge base for Lin Richuang. Organized by topic,
synthesized into cross-topic concepts, questions, and insights. Single-user.

- **Owner:** Lin Richuang
- **Timezone:** America/New_York for all scheduled tasks
- **Active topics:** AI Coding

## Source-of-truth hierarchy

The vault is **synthesis**, not source. Authoritative content lives in the original articles,
papers, and decks. The vault distils, connects, and keeps it queryable.

1. **Original sources** — the article text, PDF, or slide deck as ingested
2. **Source stubs** (`Sources/`) — the vault's reference record, citing the original
3. **Concepts** (`Concepts/`) — atomic ideas synthesized from multiple sources
4. **Insights** (`Insights/`) — cross-topic conclusions, each backed by evidence
5. **Questions** (`Questions/`) — open curiosities, linked to relevant concepts and sources

When the vault conflicts with a source, the source wins. Flag stale vault content with
`[stale]` and update.

## Vault structure

```
vault/
├── CLAUDE.md
├── 00. Navigation/
│   └── Health reports/
├── Inbox/
├── Topics/
│   └── AI Coding/
├── Concepts/
├── Sources/
│   └── _Sources index.md
├── Questions/
│   ├── _Questions.md
│   └── Resolved/
├── Insights/
│   └── _Insights.md
├── Archive/
├── Attachments/
│   └── Slides/
├── Templates/
└── .claude/
    ├── commands/
    ├── scripts/
    ├── scheduled-tasks/
    │   └── _templates/
    ├── cross-vault-sweep.md
    └── ingestion-state.json
```

Start any session by reading `00. Navigation/Dashboard.md`.

## Conventions

- **File naming:** `Q-NNN <title>.md` for questions, `I-NNN <title>.md` for insights,
  `<Concept name>.md` for concepts, `<Title> - <Author>.md` for sources,
  `YYYY-MM-DD <slug>.md` for inbox captures
- **Dates:** ISO 8601 (`YYYY-MM-DD`); always absolute, never "yesterday"
- **Sources:** every claim in a concept or insight gets a `Source:` line pointing at a
  source stub in `Sources/`
- **Confidence flags:** `[confirmed]`, `[draft]`, `[OPEN]`, `[stale]` after key statements
- **No silent rewrites:** when an insight changes, note the update — don't rewrite history
  without a trace

## Working norms

1. **Synthesis over summary.** A source stub summarises what an article said. A concept
   explains the mechanism. An insight makes a claim backed by evidence. Keep these distinct.
2. **No hallucinations.** When uncertain, write `[OPEN]` — never fabricate.
3. **Concise.** No filler. One sentence per note field if that's enough.
4. **Surface connections.** When ingesting, actively look for links to existing concepts
   and open questions. Cross-links are the value.
5. **Execution bias.** High-confidence writes (new source stubs, MOC updates, concept
   cross-links) happen automatically. Propose-only for new insights, concept rewrites,
   and question resolutions.
6. **Visual-first for decks.** Embed relevant slide images inline rather than just
   describing them.

## Active research threads

> What's driving your reading right now? Update this section when focus shifts.

<!-- populate as you go; leave empty at setup -->

## Automation suite

| Command | Cadence | Mode | What |
|---|---|---|---|
| `/ingest-article` | on demand | hybrid | Article text → source stub → cross-vault sweep |
| `/ingest-webpage <url>` | on demand | hybrid | Fetch URL via WebFetch |
| `/ingest-file <path>` | on demand | hybrid | .pptx or .pdf — deck or paper auto-detected |
| `/capture-note` | on demand | auto | Fleeting idea → Inbox/ |
| `/weekly-review` | Sundays America/New_York | hybrid | Synthesize new sources + housekeeping |
| `/monthly-health` | 1st of month | mostly propose | Orphans, dead links, archive sweep |
| `/topic-search <query>` | on demand | read-only | Cross-vault context bundle |

State file: `.claude/ingestion-state.json` — tracks all sources processed so `/weekly-review`
knows what's new.

## How to update this file

Update `CLAUDE.md` when:
- Your active research threads shift
- Vault structure changes (new top-level folder added)
- Working norms evolve

Do NOT bloat with per-source notes — those belong in `Sources/` and `Inbox/`.
