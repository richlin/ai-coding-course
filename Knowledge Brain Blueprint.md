# Knowledge Brain — Blueprint

> A reusable pattern for setting up a **personal knowledge vault** — built on Obsidian + Claude Code. The output is an `.md`-native vault that ingests articles, webpages, PDFs, and slide decks into a structured, searchable, AI-queryable personal knowledge base organized by topic.
>
> **This document is dual-purpose.** A human can read it end-to-end to understand the pattern. A Claude Code session can also execute it directly — see **Section 0** below for the interactive bootstrap protocol.

---

## Section 0 — Bootstrap protocol (read this first if you're Claude Code)

If a user hands you this document and asks you to **set up a new knowledge brain**, follow this protocol exactly:

### Phase 1 — Interview the user

Ask the questions below **one or two at a time, not all at once**. Record the answers; you'll need them in Phase 2+.

After each answer set, briefly echo back what you captured so the user can correct it.

**Question 1 — Vault name**
What should the vault be called? This becomes the root folder name.
- Examples: `Knowledge Brain`, `Lin's Brain`, `Personal Vault`

**Question 2 — Storage location**
Where should the vault live? Provide the full local path.
- Examples:
  - iCloud Drive: `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/Knowledge Brain`
  - Dropbox: `~/Dropbox/Knowledge Brain`
  - Local: `~/Documents/Knowledge Brain`

**Question 3 — Initial topics** (multiple choice — confirm or modify the suggested set)
Which knowledge domains should be created as starter topic folders? Suggested defaults:
- a) AI Coding
- b) Product Thinking
- c) Writing
- d) Research Methods
- e) Add your own (list them)

Echo the final topic list before proceeding.

**Question 4 — Timezone**
What timezone should scheduled tasks use? (e.g., `Asia/Singapore`, `America/New_York`, `Europe/London`)

**Question 5 — OS**
Are you on macOS or Linux? This determines the slide-extraction path in `embed-slides.sh`.
- a) macOS
- b) Linux

After all answers are captured, **summarise back** to the user as a single block and ask: *"Should I proceed with vault creation using these inputs? (y/n)"*. Only proceed on `y`.

### Phase 2 — Create folder structure

Based on Question 1 (vault name) + Question 2 (storage path) + Question 3 (topics):

```bash
VAULT="<<STORAGE_PATH>>/<<VAULT_NAME>>"
mkdir -p "$VAULT"
cd "$VAULT"

# Core structure
mkdir -p "00. Navigation/Health reports"
mkdir -p "Inbox"
mkdir -p "Concepts"
mkdir -p "Sources"
mkdir -p "Questions/Resolved"
mkdir -p "Insights"
mkdir -p "Archive"
mkdir -p "Attachments/Slides"
mkdir -p ".claude/commands"
mkdir -p ".claude/scripts"
mkdir -p ".claude/scheduled-tasks/_templates"
mkdir -p "Templates"

# Topic folders (per Question 3 — repeat for each topic)
mkdir -p "Topics/AI Coding"
mkdir -p "Topics/Product Thinking"
mkdir -p "Topics/Writing"
mkdir -p "Topics/Research Methods"
# (plus any user-defined additions)
```

### Phase 3 — Write all canonical files

Use the templates in Sections 3 through 10 below to create:

- `CLAUDE.md` at vault root
- `00. Navigation/README.md`
- `00. Navigation/Dashboard.md`
- `Sources/_Sources index.md`
- `Questions/_Questions.md`
- `Insights/_Insights.md`
- `Topics/<each topic>/_MOC.md` (one per topic)
- `.claude/cross-vault-sweep.md`
- All 7 slash commands in `.claude/commands/`
- `.claude/scripts/embed-slides.sh`
- Scheduled-task templates in `.claude/scheduled-tasks/_templates/`
- All 6 note templates in `Templates/`
- `.claude/ingestion-state.json` (empty baseline)

Merge the user's Phase 1 answers as placeholders using the `<<FIELD_NAME>>` convention.

### Phase 4 — Final report

Print to the user:

```
─── Knowledge Brain bootstrapped ───
Vault path: <path>
Vault name: <name>
Files created: N md files + scripts
Folders: <list>
Topics ready: <list>

Next steps:
1. Read CLAUDE.md at vault root
2. Open the vault in Obsidian (File → Open folder as vault)
3. Run /ingest-article or /ingest-webpage to add your first source
4. Run /capture-note for any ideas you want to record immediately
5. After a week of ingestion, run /weekly-review to synthesize
```

---

## Section 1 — What this is and what it solves

A **knowledge brain** is a personal synthesis layer over the reading and thinking you already do. It sits between the raw sources (articles, papers, slide decks, webpages) and your working knowledge (concepts you understand, insights you've formed, questions you're still chasing). **Synthesis, not source** — original content lives upstream; the vault distils, cross-references, and keeps it queryable.

**Problems it solves:**

- "I read a great piece on this six months ago — what did it say?" (verbatim-searchable source stubs, not browser bookmarks)
- "What do I actually know about X across all the things I've read?" (topic MOCs surface everything in one view)
- "I have a vague feeling these two ideas are connected — are they?" (Concepts/ and cross-links make the connection explicit)
- "What questions am I still carrying?" (Questions/ keeps open curiosities alive and trackable)
- "What have I concluded that I actually believe?" (Insights/ is your personal claim layer, distinct from source summaries)
- "That article I ingested — what did it update in my model?" (cross-vault sweep ripples new sources through existing concepts and questions)

**Architecture in one paragraph:**

A local `.md` folder, structured into topic sub-folders plus four cross-topic layers (Concepts, Sources, Questions, Insights), opened in **Obsidian** by you and in **Claude Code** by the AI. Claude reads a top-level `CLAUDE.md` on every session that anchors your active research threads. Seven slash commands run on-demand or on schedule to keep the vault growing. No external MCP dependencies — everything works with Claude Code's built-in tools plus a local `embed-slides.sh` script.

---

## Section 2 — Prerequisites

| Item | Purpose | Cost |
|---|---|---|
| **Claude Code** (CLI or Desktop) | The AI client that reads/writes the vault | Pro subscription |
| **Obsidian** | Human-readable rendering (wiki-links, graph view, slide previews, search) | Free |
| **Local folder** | Where the vault lives (optionally synced via iCloud/Dropbox/OneDrive) | Free |
| **`brew` / equivalent** | For slide-extraction tooling (LibreOffice or Microsoft PowerPoint on macOS) | Free |

No Microsoft Graph MCP, no SharePoint, no Outlook integration required.

---

## Section 3 — Vault structure (canonical)

```
<<VAULT_NAME>>/
├── CLAUDE.md                          Session-entry context (most important file in the vault)
├── 00. Navigation/                    README, Dashboard, health reports
│   └── Health reports/                Auto-generated monthly health reports
├── Inbox/                             Fleeting captures from /capture-note — awaiting triage
├── Topics/                            One flat folder per knowledge domain
│   ├── AI Coding/                     Each contains: note files + one _MOC.md index
│   ├── Product Thinking/
│   ├── Writing/
│   └── Research Methods/
├── Concepts/                          Atomic, cross-topic ideas (one file per concept, flat)
├── Sources/                           Reference stubs for articles, papers, books, decks
│   └── _Sources index.md              Auto-maintained index
├── Questions/                         Open curiosities — Q-NNN files
│   ├── _Questions.md                  Auto-maintained index
│   └── Resolved/                      Q-NNN files whose answer was found
├── Insights/                          Synthesized conclusions — I-NNN files
│   └── _Insights.md                   Auto-maintained index
├── Archive/                           Outdated or retired material
├── Attachments/
│   └── Slides/                        Extracted slide PNGs per deck
├── Templates/                         Note templates
└── .claude/
    ├── commands/                       Slash command definitions (7 files)
    ├── scripts/                        Helper scripts (embed-slides.sh + companions)
    ├── scheduled-tasks/
    │   └── _templates/                 Scheduled task templates
    ├── cross-vault-sweep.md            Shared sweep procedure
    └── ingestion-state.json            Tracks sources already processed
```

**Topic folders are intentionally flat.** Files live directly in `Topics/<topic>/` with a `_MOC.md` index. No sub-folder hierarchy within topics — wiki-links and the MOC do the navigation job without adding folder overhead.

---

## Section 4 — `CLAUDE.md` template (vault root)

```markdown
# CLAUDE.md — <<VAULT_NAME>>

This file is the persistent context every Claude Code session in this vault must read first.

## What this vault is

**<<VAULT_NAME>>** — a personal knowledge base for <<OWNER_NAME>>. Organized by topic,
synthesized into cross-topic concepts, questions, and insights. Single-user.

- **Owner:** <<OWNER_NAME>>
- **Timezone:** <<TZ>> for all scheduled tasks
- **Active topics:** <<TOPIC_LIST>>

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

[See Section 3 folder map — reproduced at vault root by bootstrap]

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

<<RESEARCH_THREADS — populate as you go; leave empty at setup>>

## Automation suite

| Command | Cadence | Mode | What |
|---|---|---|---|
| `/ingest-article` | on demand | hybrid | Article text → source stub → cross-vault sweep |
| `/ingest-webpage <url>` | on demand | hybrid | Fetch URL via WebFetch |
| `/ingest-file <path>` | on demand | hybrid | .pptx or .pdf — deck or paper auto-detected |
| `/capture-note` | on demand | auto | Fleeting idea → Inbox/ |
| `/weekly-review` | Sundays <<TZ>> | hybrid | Synthesize new sources + housekeeping |
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
```

---

## Section 5 — Slash commands (full content for `.claude/commands/`)

Write each of these files. Replace `<<TZ>>` and `<<VAULT_PATH>>` from Phase 1 answers.

### `.claude/commands/ingest-article.md`

```markdown
---
description: Ingest an article, essay, or blog post from clipboard or local file into the vault
---

# /ingest-article

Reads article content, creates a source stub, triages into topics, and runs the cross-vault sweep.

## Procedure

1. Read `CLAUDE.md` + `00. Navigation/Dashboard.md` for context.
2. Read `.claude/ingestion-state.json` — check if this source was already processed (by URL
   or filename). If yes, ask whether to re-ingest or skip.
3. Get the article content:
   - If the user pastes text directly: use it as-is
   - If the user provides a file path: read the file
4. Extract metadata: title, author, publication, date, URL if present.
5. **Triage** — classify the content:
   - Which topic(s) does it belong to? (may span multiple)
   - Does it introduce or deepen a named concept? → note for Concepts/
   - Does it raise an open question? → note for Questions/
   - Does it provide evidence for or against an existing insight? → note for Insights/
6. Create a source stub in `Sources/` using `Template - Source (article or paper).md`.
   Fill in metadata + key takeaways + open questions the article raises.
7. Add a row to `Sources/_Sources index.md`.
8. Link the stub from the relevant `Topics/<topic>/_MOC.md`.
9. Run **cross-vault sweep** per `.claude/cross-vault-sweep.md`.
10. Update `.claude/ingestion-state.json` with the source URL or filename.

## Report format

- Source: <title> by <author>
- Topics tagged: <list>
- Concept links: <list>
- Questions raised: <list>
- Existing insights updated: <list>
- Auto-written: <count> items
- Pending your review: <list of proposals>
```

### `.claude/commands/ingest-webpage.md`

```markdown
---
description: Fetch a URL and ingest it as a source into the vault
---

# /ingest-webpage <url>

Fetches the URL via WebFetch and runs the same pipeline as /ingest-article.

## Procedure

1. Read `CLAUDE.md` for context.
2. Check `.claude/ingestion-state.json` — if this URL was already processed, ask whether
   to re-ingest or skip.
3. Fetch the URL content using the WebFetch tool.
4. Extract: title, author (if bylined), publication, date, URL.
5. Run the same **triage → source stub → cross-links → cross-vault sweep** pipeline as
   `/ingest-article`.
6. Update ingestion state with the URL.

## Notes

- If the page is paywalled or requires login, WebFetch will return partial content —
  note in the stub: `coverage: partial (paywall)`.
- For Substack posts, Twitter/X threads, or YouTube transcripts: treat as article;
  note the format in the stub's `type:` field.

Report format same as `/ingest-article`.
```

### `.claude/commands/ingest-file.md`

```markdown
---
description: Ingest a local .pptx or .pdf — auto-detects slide deck vs paper/book
---

# /ingest-file <path>

Auto-detects whether the file is a **slide deck** (visual-first) or a **paper/book**
(text-first) and applies the appropriate extraction.

## Detection logic

- `.pptx` → always slide deck
- `.pdf` → inspect first 3 pages via Read tool (Claude is multimodal):
  - Mostly prose paragraphs → paper/book mode
  - Mostly slides, diagrams, bullet layouts → deck mode

## Deck mode (.pptx or visual PDF)

1. Check `.claude/ingestion-state.json` for prior processing.
2. Run `bash .claude/scripts/embed-slides.sh "<path>"` → extracts slide PNGs to
   `Attachments/Slides/<base>/` + generates `_index.md` gallery.
3. Visually inspect 4–6 representative slides via Read tool.
4. Create source stub in `Sources/` using `Template - Source (deck).md`. Include
   📎 gallery link + embed 2–3 key diagram slides.
5. Add row to `Sources/_Sources index.md`.
6. Link from relevant `Topics/<topic>/_MOC.md`.
7. Auto-embed key diagram slides into the right topic file if a clear fit exists.
8. Run cross-vault sweep.
9. Update ingestion state.

## Paper/book mode (text PDF)

1. Check ingestion state.
2. Read the PDF via Read tool (paginated for long documents).
3. Extract: title, authors, abstract/summary, key claims, methodology if relevant.
4. Create source stub using `Template - Source (article or paper).md`. Include page
   references for key claims.
5. Add row to `Sources/_Sources index.md`.
6. Link from relevant `Topics/<topic>/_MOC.md`.
7. Run cross-vault sweep.
8. Update ingestion state.

## Report format

- File: <filename> — detected as: <deck | paper>
- Slides extracted: N (deck mode only)
- Topics tagged: <list>
- Concept links: <list>
- Questions raised: <list>
- Auto-written: <count>
- Proposals: <list>
```

### `.claude/commands/capture-note.md`

```markdown
---
description: Quick capture of a fleeting idea, observation, or half-formed thought into Inbox/
---

# /capture-note

Low-friction capture. Gets the idea recorded immediately; /weekly-review triages it later.

## Procedure

1. Ask the user: "What's the thought?" (or read it from the prompt if they included it inline).
2. Ask: "Any topic hint?" (optional — e.g., "AI Coding", "vague feeling about incentives")
3. Create a file in `Inbox/` named `YYYY-MM-DD <slug>.md` using `Template - Inbox note.md`.
4. Write the raw thought, the optional topic hint, and the date. Nothing else.
5. Confirm: "Captured to Inbox/YYYY-MM-DD <slug>.md. /weekly-review will triage it."

## What NOT to do

- Do not attempt to classify or synthesize the note during capture — that's
  /weekly-review's job.
- Do not add wiki-links or cross-references — those emerge during triage.
- Do not ask for more context than the user volunteers.

Capture must be frictionless. If the user resists answering questions, write what they gave you.
```

### `.claude/commands/weekly-review.md`

```markdown
---
description: Weekly synthesis pass — Inbox triage, new source synthesis, housekeeping sweep. Runs Sundays <<TZ>>.
---

# /weekly-review

Three passes: Inbox triage, synthesis of new sources, housekeeping.

## Pass 1 — Inbox triage

1. List all files in `Inbox/` (newest first).
2. For each inbox note, classify:
   - **Concept seed** → create or update `Concepts/<name>.md`
   - **Question** → create `Questions/Q-NNN <title>.md` + add row to `_Questions.md`
   - **Insight candidate** → propose I-NNN (do not auto-create)
   - **Belongs in a topic** → move to `Topics/<topic>/` + link in `_MOC.md`
   - **Too rough to classify** → leave in Inbox with `[review again]` tag
3. Delete processed Inbox files after moving content to the right place.
4. Report: N items processed, M moved, K left pending.

## Pass 2 — Synthesis of new sources

1. Read `.claude/ingestion-state.json`. Identify sources ingested since `last_weekly_review`.
2. For each new source, re-read its source stub and check:
   - Does it confirm, deepen, or challenge an existing insight? → AUTO-WRITE additive note;
     PROPOSE status changes.
   - Does it crystallize a new cross-topic insight? → PROPOSE a new I-NNN file (do not
     auto-create).
   - Does it answer or partially answer an open Q-NNN? → PROPOSE resolution or update.
   - Does it introduce a concept not yet in `Concepts/`? → AUTO-WRITE new concept stub.
3. List all insight proposals in the review output — wait for user endorsement.

## Pass 3 — Housekeeping

1. **Dashboard refresh** — update `00. Navigation/Dashboard.md`: research threads, open
   question count, recent insights, inbox status.
2. **Questions sort** — move `status: resolved` Q-NNN files to `Questions/Resolved/`;
   re-sort `_Questions.md`.
3. **Stale flags** — surface any `[stale]` markers found in concepts or insights.

## Report format

- Inbox: N processed, M moved, K pending
- New sources reviewed: N
- Concepts auto-written: M
- Insight proposals (pending your endorsement): <list>
- Question updates proposed: <list>
- Housekeeping: Dashboard updated, N Q-NNN moved to Resolved

Update `last_weekly_review` timestamp in `.claude/ingestion-state.json`.

Runs Sundays <<TZ>>.
```

### `.claude/commands/monthly-health.md`

```markdown
---
description: Monthly structural maintenance — 1st of each month. Orphans, dead links, naming, archive sweep, proposals.
---

# /monthly-health

Five passes:

1. **Pass 1 — Orphan notes** — find files with no inbound wiki-links; flag for review
   (acceptable for many source stubs; concerning for concepts or insights)
2. **Pass 2 — Dead links** — `[[targets]]` pointing at non-existent files
3. **Pass 3 — Source line validity** — every `Source:` line in concepts and insights points
   at an extant stub in `Sources/`
4. **Pass 4 — Naming convention violations** — files not matching canonical patterns
   (Q-NNN, I-NNN, etc.)
5. **Pass 5 — Archive sweep (auto)** — resolved Questions 60+ days old → move to
   `Questions/Resolved/`; Inbox items 30+ days old with `[review again]` tag → flag loudly

Output: `00. Navigation/Health reports/YYYY-MM.md`.

AUTO-WRITE only the archive sweep (Pass 5); everything else PROPOSE.
```

### `.claude/commands/topic-search.md`

```markdown
---
description: Cross-vault search — bundles context for a topic or query. Read-only.
---

# /topic-search <query>

Pulls everything relevant to a topic or question across the vault.

## Procedure

1. Read `CLAUDE.md` for active research threads.
2. Search for `<query>` across:
   - All `Topics/<topic>/_MOC.md` files
   - `Concepts/` (titles + content)
   - `Sources/_Sources index.md` (titles + tags)
   - `Questions/_Questions.md` (titles + status)
   - `Insights/_Insights.md` (titles)
3. For top matches, read full file content.
4. Bundle into a chat output: relevant concepts, related sources, open questions on the
   topic, insights that bear on it.

Read-only. No vault writes.
```

---

## Section 6 — `.claude/cross-vault-sweep.md` (the shared procedure)

```markdown
# Cross-vault sweep (shared procedure)

> Invoked by `/ingest-article`, `/ingest-webpage`, and `/ingest-file` for every piece of
> new content. New content must ripple through existing concepts, questions, and insights
> so the vault stays internally consistent.

## Execution bias: act on high confidence, propose only judgment calls

### Auto-execute (just write it)

- New row in `Sources/_Sources index.md`
- New row in `Topics/<topic>/_MOC.md`
- `[[wiki-links]]` from existing concept/insight/question files to the new source
- New stub in `Concepts/` when a named concept is clearly identified and not yet present
- Additive content on existing concept files (new examples, new source rows)
- New `Questions/Q-NNN` file when content explicitly raises an unresolved question
- New row in `Questions/_Questions.md`

### Propose-only (judgment calls — always ask)

- New `Insights/I-NNN` file — claims require the user's explicit endorsement
- Updates to existing insight status or content
- Resolution of an existing Question (Q-NNN status flip to resolved)
- Concept rewrites (changing the mechanism or definition, not just adding examples)
- Anything where confidence < 80%

## Indexes to check on every ingest

| Vault area | Index file | What to check |
|---|---|---|
| Sources | `Sources/_Sources index.md` | Add new row |
| Topics | `Topics/<topic>/_MOC.md` | Add link to new source stub |
| Questions | `Questions/_Questions.md` | New question raised? Existing Q answered or refined? |
| Insights | `Insights/_Insights.md` | New evidence for/against? New insight to propose? |
| Concepts | `Concepts/` (scan titles) | New concept named? Existing concept needs new source/example? |

Inbox/ is /weekly-review's domain — do not touch during ingest sweeps.

## Report format

After every ingest:

```
Auto-written:
  Source stub: 1
  MOC links: N
  Concept updates: M
  New concepts: K
  New questions: L
  Wiki-links added: N

Pending your review:
  New insights: <list with one-line rationale>
  Question resolutions: <list>
  Concept rewrites: <list>
```

All auto-writes are reversible — ask Claude to undo, or revert in git if the vault is
version-controlled.

## Hard rules

- Run the sweep for **every** new source, not just "important-looking" ones
- **Source-tag every edit** with the originating source stub
- **Auto-write is additive only** — never delete or overwrite existing content
- **If < 80% confidence — propose instead of auto-write**
- **Insights require the user's explicit endorsement** — never auto-create I-NNN files
```

---

## Section 7 — Scheduled task templates (`.claude/scheduled-tasks/_templates/`)

### `weekly-review.template.md`

```markdown
---
name: kb-weekly-review
description: Sunday weekly synthesis — Inbox triage, new source synthesis, housekeeping
---

Run the `/weekly-review` slash command in this vault.

Working directory: <<VAULT_PATH>>

1. Read `.claude/commands/weekly-review.md` for full procedure
2. Read `.claude/ingestion-state.json` for sources ingested since last review
3. Pass 1: triage Inbox/
4. Pass 2: synthesize new sources → propose insights, auto-write concepts
5. Pass 3: dashboard refresh + questions maintenance

All times in <<TZ>> local. Runs Sundays.
```

### `monthly-health.template.md`

```markdown
---
name: kb-monthly-health
description: Monthly structural maintenance — 1st of each month
---

Run `/monthly-health`.

Five passes: orphans, dead links, source validity, naming, archive sweep.

Auto-write only the archive sweep (Pass 5); everything else propose.

Output to `00. Navigation/Health reports/YYYY-MM.md`.

1st of month, <<TZ>>.
```

---

## Section 8 — Scripts (`.claude/scripts/`)

### `embed-slides.sh` (macOS / Linux compatible)

```bash
#!/bin/bash
# Extract per-slide PNGs from .pptx or .pdf into Attachments/Slides/<base>/
#
# Usage: bash .claude/scripts/embed-slides.sh "<path-to-pptx-or-pdf>"

set -euo pipefail

INPUT="${1:-}"
if [ -z "$INPUT" ] || [ ! -f "$INPUT" ]; then
  echo "Usage: $0 <pptx-or-pdf-path>"
  exit 1
fi

SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"
VAULT="$(dirname "$(dirname "$SCRIPT_DIR")")"
BASE="$(basename "$INPUT")"
BASE="${BASE%.*}"
OUT="$VAULT/Attachments/Slides/$BASE"
mkdir -p "$OUT"

EXT="${INPUT##*.}"
if [ "$EXT" = "pptx" ]; then
  if [ "$(uname)" = "Darwin" ] && [ -d "/Applications/Microsoft PowerPoint.app" ]; then
    osascript "$SCRIPT_DIR/export-slides.applescript" "$INPUT" "/tmp/$BASE.pdf"
  else
    soffice --headless --convert-to pdf --outdir /tmp "$INPUT" >/dev/null
  fi
  PDF="/tmp/$BASE.pdf"
else
  PDF="$INPUT"
fi

if command -v sips >/dev/null 2>&1 && [ "$(uname)" = "Darwin" ]; then
  python3 "$SCRIPT_DIR/pdf-to-pngs.py" "$PDF" "$OUT"
else
  pdftoppm -png -r 150 "$PDF" "$OUT/slide"
  cd "$OUT"
  for f in slide-*.png; do
    n=$(echo "$f" | sed 's/slide-\([0-9]*\)\.png/\1/')
    printf -v new "slide-%02d.png" "$n"
    [ "$f" != "$new" ] && mv "$f" "$new"
  done
fi

INDEX="$OUT/_index.md"
cat > "$INDEX" <<EOF
---
title: $BASE — slide gallery
source: $INPUT
extracted: $(date -u +"%Y-%m-%dT%H:%M:%SZ")
---

# $BASE

$(for f in "$OUT"/slide-*.png; do
  fn=$(basename "$f")
  echo "## ${fn%.*}"
  echo ""
  echo "![[Attachments/Slides/$BASE/$fn]]"
  echo ""
done)
EOF

echo "Extracted slides to: $OUT"
echo "Embed via:  ![[Attachments/Slides/$BASE/slide-NN.png]]"
```

(Companion helpers: `export-slides.applescript` for PowerPoint headless export on macOS, and `pdf-to-pngs.py` for Quartz-based PDF→PNG splitting. Generate these alongside `embed-slides.sh` when running on macOS. On Linux the `pdftoppm` fallback is sufficient.)

---

## Section 9 — Index file templates

### `00. Navigation/README.md`

```markdown
---
title: <<VAULT_NAME>> — README
purpose: First page for anyone opening the vault
---

# <<VAULT_NAME>>

A personal knowledge vault owned by <<OWNER_NAME>>.

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
```

### `00. Navigation/Dashboard.md`

```markdown
---
title: Dashboard
last_updated: <<DATE>>
purpose: Single-screen orientation — where you are, what's open, what's next
---

# Dashboard — <<VAULT_NAME>>

> Refreshed weekly by `/weekly-review`.

## Active research threads

> What's driving your reading right now? Update in CLAUDE.md when focus shifts.

<<RESEARCH_THREADS — populate as you go>>

## Open questions (top 5)

> Full list: `Questions/_Questions.md`

[populate]

## Recent insights (last 30 days)

> Full list: `Insights/_Insights.md`

[populate]

## Inbox status

> Files in `Inbox/` awaiting triage: [count] — run `/weekly-review` to clear.

[populate]

## Recently ingested sources

[auto-populated by /weekly-review]
```

### `Sources/_Sources index.md`

```markdown
---
title: Sources index
purpose: Index of all ingested source stubs
---

# Sources

| Title | Author | Type | Date | Topics | File |
|---|---|---|---|---|---|
```

### `Questions/_Questions.md`

```markdown
---
title: Open questions
purpose: Index of all Q-NNN files
---

# Questions

## Open

| ID | Question | Blocking | Opened | Target |
|---|---|---|---|---|

## Resolved

| ID | Question | Resolved date | Resolution summary |
|---|---|---|---|
```

### `Insights/_Insights.md`

```markdown
---
title: Insights
purpose: Index of all I-NNN files
---

# Insights

| ID | Claim | Confidence | Topics | Date |
|---|---|---|---|---|
```

### `Topics/<topic>/_MOC.md` (one per topic, repeat for each)

```markdown
---
title: <<TOPIC>> — Map of Content
purpose: Index of everything in this topic folder
---

# <<TOPIC>>

## Sources

| Title | Author | Date | File |
|---|---|---|---|

## Concepts touched

- [[<concept>]]

## Open questions

- [[Q-NNN <title>]]

## Insights

- [[I-NNN <title>]]

## Notes

[freeform notes about this topic's scope, sub-areas, reading list]
```

---

## Section 10 — Note templates (`Templates/`)

### `Template - Concept.md`

```markdown
---
concept: <name>
tags: [type/concept, topic/<primary topic>]
created: YYYY-MM-DD
---

# <Concept name>

## Definition
<What it is — 1-3 sentences>

## Mechanism
<How it works — the underlying logic or process>

## Examples
- <concrete example 1> — Source: [[<source stub>]]
- <concrete example 2> — Source: [[<source stub>]]

## Related concepts
- [[<concept>]] — <one-line relationship>
- [[<concept>]] — <one-line relationship>

## Open questions it raises
- [[Q-NNN <title>]]

## Sources
- [[<source stub>]] — <what this source contributed to this concept>
```

### `Template - Source (article or paper).md`

```markdown
---
title: <title>
author: <author>
type: article | paper | book | essay
url: <url>
file: <local path if applicable>
date: YYYY-MM-DD
topics: [<topic>, <topic>]
tags: [type/source]
ingested: YYYY-MM-DD
---

# <Title> — <Author>

## Summary
<2-4 sentences: what it argues and why it matters>

## Key takeaways
- <claim 1>
- <claim 2>
- <claim 3>

## Open questions it raises
- <question 1>
- <question 2>

## Concepts touched
- [[<concept>]]

## Notable quotes
> <verbatim quote> (p. N or section name)

## My reaction
<brief personal response — agreement, skepticism, things to follow up>
```

### `Template - Source (deck).md`

```markdown
---
title: <deck title>
file: <local path>
type: deck
date: YYYY-MM-DD
topics: [<topic>]
tags: [type/source, type/deck]
ingested: YYYY-MM-DD
gallery: "[[Attachments/Slides/<base>/_index.md]]"
---

# <Deck title>

> 📎 **Slides:** `<local path>` · gallery: `[[Attachments/Slides/<base>/_index.md]]`

## Summary
<What the deck covers and the key argument>

## Key slides

![[Attachments/Slides/<base>/slide-NN.png]]
<caption — what this slide shows>

![[Attachments/Slides/<base>/slide-NN.png]]
<caption>

## Key takeaways
- <point 1>
- <point 2>

## Concepts touched
- [[<concept>]]

## Open questions raised
- <question>
```

### `Template - Question.md`

```markdown
---
id: Q-NNN
title: <one-line question>
opened: YYYY-MM-DD
status: open
blocks: <what thinking or work waits on this>
target_resolution: <date or trigger — or leave blank>
tags: [type/question, status/open]
---

# Q-NNN — <title>

## Question
<the question in one sentence>

## Why it matters
<consequence of leaving it unresolved>

## Working hypothesis
<current best guess — or [OPEN]>

## Relevant sources
- [[<source stub>]] — <what it contributes>

## Related concepts
- [[<concept>]]

## Notes
<as the question develops>

## ✅ Resolution
<filled in when resolved — date + answer + linked insight if applicable>
```

### `Template - Insight.md`

```markdown
---
id: I-NNN
title: <one-line claim>
created: YYYY-MM-DD
status: draft | confirmed
confidence: low | medium | high
tags: [type/insight, status/draft]
---

# I-NNN — <title>

## Claim
<the insight in 1-2 sentences — a claim you actually believe>

## Evidence
- [[<source stub>]] — <what it contributes>
- [[<source stub>]] — <what it contributes>

## Counter-evidence or limitations
- <known challenge to this claim>

## Implications
- <what follows if this is true>

## Related concepts
- [[<concept>]]

## Related questions
- [[Q-NNN <title>]]

## Notes
<how this insight has evolved>
```

### `Template - Inbox note.md`

```markdown
---
date: YYYY-MM-DD
topic_hint: <optional — e.g., "AI Coding", "vague feeling about incentives">
tags: [type/inbox]
---

# YYYY-MM-DD — <slug>

<raw thought, exactly as captured>

---
*Captured via /capture-note. Awaiting /weekly-review triage.*
```

---

## Section 11 — Conventions (canonical)

### File naming

| Type | Pattern | Example |
|---|---|---|
| Question | `Q-NNN <title>.md` | `Q-007 Why does RAG degrade at scale.md` |
| Insight | `I-NNN <title>.md` | `I-003 AI tools amplify senior judgment.md` |
| Source | `<Title> - <Author>.md` | `Attention Is All You Need - Vaswani et al.md` |
| Concept | `<Concept name>.md` | `Retrieval-Augmented Generation.md` |
| Inbox | `YYYY-MM-DD <slug>.md` | `2026-08-20 thought-on-prompting.md` |
| Topic MOC | `_MOC.md` (inside topic folder) | `Topics/AI Coding/_MOC.md` |
| Health report | `YYYY-MM.md` (inside Health reports/) | `2026-08.md` |

### Dates

ISO 8601 (`YYYY-MM-DD`). Always absolute, never "yesterday" or "last week". `<<TZ>>` for scheduled tasks.

### Source attribution

Every claim in a Concept or Insight gets a `Source:` line pointing at the relevant stub in `Sources/`. Don't cite the original URL directly in Concept or Insight files — link through the stub so the stub is the single contact point for metadata. If the stub ever needs updating (URL changes, author correction), one file changes and all links stay valid.

### Confidence flags

- `[confirmed]` — backed by multiple sources or your own experience
- `[draft]` — working position, not yet tested
- `[OPEN]` — unresolved, actively uncertain
- `[stale]` — may be outdated; needs checking against current sources

### Binary files

`.md`-only in the vault. PDFs, PPTX, and other binaries live outside the vault folder (or in `Attachments/Slides/` for extracted PNGs only). The vault keeps reference stubs in `Sources/`. Deck galleries live in `Attachments/Slides/<base>/`.

---

## Section 12 — Recommended setup sequence

| Day | Action | Time |
|---|---|---|
| **Day 1** | Hand this blueprint to Claude Code: *"Use this blueprint to set up a knowledge brain — start the interview"* | — |
| **Day 1** | Complete the Phase 1 interview (5 questions) | ~10 min |
| **Day 1** | Claude executes Phases 2–4: folders + CLAUDE.md + slash commands + scripts | ~20 min |
| **Day 1** | Open the vault folder in Obsidian; verify folders render correctly | 5 min |
| **Day 1** | Run `/ingest-article` or `/ingest-webpage` on one article you've recently read | 10 min |
| **Days 2–6** | Add 5–10 more sources (mix of articles, webpages, one PDF or deck) | ~1 hr total |
| **Day 7** | Run `/weekly-review` — first synthesis pass | 20 min |
| **Week 2** | Schedule `weekly-review` and `monthly-health` in Claude Code's scheduled-tasks UI | 5 min |
| **Month 2** | First `/monthly-health` run | 20 min |

**Total setup time: ~1 hour.** The vault is useful from the first ingestion.

---

## Section 13 — Common pitfalls

| Pitfall | Counter |
|---|---|
| **Vault becomes a bookmark dump** — source stubs with no synthesis | Key takeaways required in every stub; weekly-review surfaces synthesis gaps |
| **Concepts too broad** — one concept tries to cover a whole field | One concept = one mechanism or idea; split large concepts into linked sub-concepts |
| **Insights auto-generated without endorsement** — vault drifts with unverified claims | Insights are always propose-only; you endorse before I-NNN is created |
| **Inbox accumulates indefinitely** — capture without triage | Weekly-review's Pass 1 is mandatory; monthly-health flags 30-day-old inbox items |
| **Questions never resolve** — open Q-NNN pile up with no follow-through | Target resolution field on every Q-NNN; weekly-review checks for partial answers |
| **Topics sprawl** — a new topic folder per article | Topics are broad domains, not article categories; when in doubt, file under the closest existing topic |
| **Source links go stale** — URL dies, file moves | Source stubs include both `url:` and `file:` fields; the stub is the stable reference, not the URL |
| **Concepts and insights blur** — synthesis happens in source stubs | Keep the layers distinct: stub = what the source says; concept = how the mechanism works; insight = what you believe |

---

## Section 14 — When NOT to use this pattern

- **If you read fewer than ~5 articles per month** — the overhead of stubs and cross-links won't pay off; a simple reading log in one markdown file is enough
- **If you have no sustained research threads** — the vault compounds over focused domains; for one-off research, a scratch document is faster
- **If you won't run weekly-review regularly** — the vault decays into a source dump without synthesis; the weekly pass is load-bearing

---

## Closing — the 4-line summary

If you do nothing else, do these four:

1. **Create the folder structure + `CLAUDE.md`** — anchors every Claude Code session.
2. **Set up the 7 slash commands** in `.claude/` — ingestion is the growth engine.
3. **Run `/ingest-article` or `/ingest-webpage` on your first source** — proves the pipeline.
4. **Hold the weekly-review cadence** — synthesis is what makes the vault useful past month 1.

Everything else is amplification.

---

*Blueprint version: 1.0 (personal knowledge, single-user). Adapted from the Case Brain Blueprint pattern.*
