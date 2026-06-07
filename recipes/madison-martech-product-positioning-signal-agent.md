# Madison Martech Product Positioning Signal Agent

## Purpose

Tracks martech, platform, integration, and product-stack signals so marketing and product teams can understand how technology adoption affects positioning, partner strategy, and campaign claims.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Technology watchlist | JSON | [TODO: DATA SOURCE] Approved tools, platforms, integrations, and product categories. | Yes |
| Public documentation and release feeds | RSS/API/Markdown | [TODO: DATA SOURCE] Vendor docs, release notes, integration pages, and trade news. | Yes |
| Signal rubric | JSON | [TODO: DEFINE] Define adoption, deprecation, integration, compliance, and ecosystem signals. | Yes |
| Mycroft adaptation source | Markdown | `/Users/bear/Documents/CoWork/bear-textbooks/books/mycroft/recipes/tech-stack-directional-signal-agent.md` | No |

## Phase Gates

1. Watchlist gate: tools and platforms are approved. Test: `python3 -m json.tool data/raw/madison-martech-product-positioning-signal-agent/watchlist.json`. Human capacity: [PF].
2. Source gate: vendor documentation sources are allowed. Test: `rg -n "TODO:" recipes/madison-martech-product-positioning-signal-agent.md`. Human capacity: [PA].
3. Sample gate: sample mode does not call vendor APIs. Test: `snickerdoodle run madison-martech-product-positioning-signal-agent --mode dialogic --sample`. Human capacity: [TO].

## Steps

1. Step name: Ingest martech signals. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/ingest/madison-martech-product-positioning-signal-agent__ingest-martech-signals.py`
   Input: technology watchlist and approved feeds.
   Output: raw JSON fields: vendor, product, signal_type, source_url, title, published_at, snippet.
   Where output goes: `data/raw/madison-martech-product-positioning-signal-agent/`.
2. Step name: Score positioning impact. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/gigo/madison-martech-product-positioning-signal-agent__score-positioning-impact.py`
   Input: raw martech signals and signal rubric.
   Output: verified JSON fields: signal_id, product, signal_type, impact_score, positioning_implication, evidence_url, flags.
   Where output goes: `data/verified/madison-martech-product-positioning-signal-agent/`.
3. Step name: Produce martech signal report. Labor: AI with Human review.
   Script called: `[TODO: DEV] Create scripts/tools/madison-martech-product-positioning-signal-agent__produce-martech-signal-report.py`
   Input: verified martech signals.
   Output: markdown sections: adoption signals, platform risks, partner opportunities, positioning implications.
   Where output goes: `reports/generated/`.

## Output Contract

### Agent output
File: `logs/madison-martech-product-positioning-signal-agent-[DATE].json`
Fields: `workflow`, `run_id`, `mode`, `steps_completed`, `records_seen`, `rejects`, `duplicates`, `flags`, `stop_conditions`, `todo_items`, `source_files`, `gate_decisions`, `generated_at`.

### Human report
File: `reports/generated/madison-martech-product-positioning-signal-agent-[DATE].md`
Reader: product marketing lead.
Decision enabled: decide whether technology signals affect positioning, integration roadmap, partner claims, or campaign timing.
Sections: Source coverage, signal table, impact scores, positioning implications, recommended follow-up.

## Stop Conditions

- Stop if watchlist is undefined because signal collection would be unfocused.
- Stop if vendor claims are not cited because product positioning implications need evidence.
- Stop if report recommends integration commitments without product-owner approval.

## Snickerdoodle

### Run Commands
Full dialogic run: `snickerdoodle run madison-martech-product-positioning-signal-agent --mode dialogic`
Sample mode: `snickerdoodle run madison-martech-product-positioning-signal-agent --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Ingest martech signals | `snickerdoodle run madison-martech-product-positioning-signal-agent --step ingest-martech-signals` | `--sample` |
| Score positioning impact | `snickerdoodle run madison-martech-product-positioning-signal-agent --step score-positioning-impact` |  |
| Produce martech signal report | `snickerdoodle run madison-martech-product-positioning-signal-agent --step produce-martech-signal-report` | `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - watchlist approval | `snickerdoodle gate madison-martech-product-positioning-signal-agent --gate 1 --decision approve --note "..."` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Ingest martech signals | `[TODO: DEV] scripts/ingest/madison-martech-product-positioning-signal-agent__ingest-martech-signals.py` | ingest |
| Score positioning impact | `[TODO: DEV] scripts/gigo/madison-martech-product-positioning-signal-agent__score-positioning-impact.py` | gigo |
| Produce martech signal report | `[TODO: DEV] scripts/tools/madison-martech-product-positioning-signal-agent__produce-martech-signal-report.py` | tool |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/madison-martech-product-positioning-signal-agent/` | JSON |
| Verified data | `data/verified/madison-martech-product-positioning-signal-agent/` | JSON |
| Agent log | `logs/madison-martech-product-positioning-signal-agent-[DATE].json` | JSON |
| Human report | `reports/generated/madison-martech-product-positioning-signal-agent-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

