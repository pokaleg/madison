# Madison Market Momentum Funding Monitor

## Purpose

Tracks funding, acquisitions, partnerships, and category investment signals so marketing teams can identify where a market is heating up, which competitors are gaining narrative momentum, and where campaigns need stronger proof.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Category watchlist | JSON | [TODO: DATA SOURCE] Approved categories, competitors, and investor keywords. | Yes |
| Funding and company sources | RSS/API/CSV | [TODO: DATA SOURCE] Funding news, SEC/company datasets, press releases, and partnership feeds. | Yes |
| Momentum rubric | JSON | [TODO: DEFINE] Define funding size, strategic relevance, recency, and competitor proximity scoring. | Yes |
| Mycroft adaptation source | Markdown | `/Users/bear/Documents/CoWork/bear-textbooks/books/mycroft/recipes/funding-intelligence-agent.md` | No |

## Phase Gates

1. Category gate: market categories and competitors are approved. Test: `python3 -m json.tool data/raw/madison-market-momentum-funding-monitor/category-watchlist.json`. Human capacity: [PF].
2. Source gate: funding sources are allowed and not paywalled/private. Test: `rg -n "TODO:" recipes/madison-market-momentum-funding-monitor.md`. Human capacity: [PA].
3. Sample gate: sample mode writes only local handoff files. Test: `snickerdoodle run madison-market-momentum-funding-monitor --mode dialogic --sample`. Human capacity: [TO].

## Steps

1. Step name: Ingest market momentum signals. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/ingest/madison-market-momentum-funding-monitor__ingest-market-momentum-signals.py`
   Input: category watchlist and approved sources.
   Output: raw JSON fields: company, category, event_type, amount, investor_or_partner, source_url, announced_at, snippet.
   Where output goes: `data/raw/madison-market-momentum-funding-monitor/`.
2. Step name: Score market momentum. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/gigo/madison-market-momentum-funding-monitor__score-market-momentum.py`
   Input: raw momentum records and rubric.
   Output: verified JSON fields: signal_id, company, category, momentum_score, strategic_relevance, competitor_flag, evidence_url.
   Where output goes: `data/verified/madison-market-momentum-funding-monitor/`.
3. Step name: Produce momentum report. Labor: AI with Human review.
   Script called: `[TODO: DEV] Create scripts/tools/madison-market-momentum-funding-monitor__produce-momentum-report.py`
   Input: verified momentum records.
   Output: markdown sections: funding signals, partnerships, competitor momentum, category heat, marketing implications.
   Where output goes: `reports/generated/`.

## Output Contract

### Agent output
File: `logs/madison-market-momentum-funding-monitor-[DATE].json`
Fields: `workflow`, `run_id`, `mode`, `steps_completed`, `records_seen`, `rejects`, `duplicates`, `flags`, `stop_conditions`, `todo_items`, `source_files`, `gate_decisions`, `generated_at`.

### Human report
File: `reports/generated/madison-market-momentum-funding-monitor-[DATE].md`
Reader: growth marketing or strategy lead.
Decision enabled: decide whether to adjust campaign timing, competitor messaging, category claims, or sales enablement.
Sections: Category watchlist, funding events, partnership events, momentum scores, evidence links, recommended marketing response.

## Stop Conditions

- Stop if category watchlist is missing because market momentum cannot be scoped.
- Stop if funding amounts or event dates are missing and treated as facts.
- Stop if report suggests investment advice rather than marketing implications.

## Snickerdoodle

### Run Commands
Full dialogic run: `snickerdoodle run madison-market-momentum-funding-monitor --mode dialogic`
Sample mode: `snickerdoodle run madison-market-momentum-funding-monitor --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Ingest market momentum signals | `snickerdoodle run madison-market-momentum-funding-monitor --step ingest-market-momentum-signals` | `--sample` |
| Score market momentum | `snickerdoodle run madison-market-momentum-funding-monitor --step score-market-momentum` |  |
| Produce momentum report | `snickerdoodle run madison-market-momentum-funding-monitor --step produce-momentum-report` | `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - category approval | `snickerdoodle gate madison-market-momentum-funding-monitor --gate 1 --decision approve --note "..."` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Ingest market momentum signals | `[TODO: DEV] scripts/ingest/madison-market-momentum-funding-monitor__ingest-market-momentum-signals.py` | ingest |
| Score market momentum | `[TODO: DEV] scripts/gigo/madison-market-momentum-funding-monitor__score-market-momentum.py` | gigo |
| Produce momentum report | `[TODO: DEV] scripts/tools/madison-market-momentum-funding-monitor__produce-momentum-report.py` | tool |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/madison-market-momentum-funding-monitor/` | JSON |
| Verified data | `data/verified/madison-market-momentum-funding-monitor/` | JSON |
| Agent log | `logs/madison-market-momentum-funding-monitor-[DATE].json` | JSON |
| Human report | `reports/generated/madison-market-momentum-funding-monitor-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

