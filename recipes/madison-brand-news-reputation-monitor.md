# Madison Brand News Reputation Monitor

## Purpose

Tracks company, brand, product, and competitor mentions across approved news sources so a marketing lead can distinguish reputation-moving coverage from ordinary category noise and decide whether to respond, monitor, or escalate.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Brand watchlist | JSON | [TODO: DATA SOURCE] Define approved brand, product, competitor, and executive names. | Yes |
| News feeds | RSS/API JSON | [TODO: DATA SOURCE] Approved business, trade, local, and category news feeds. | Yes |
| Source reliability rubric | JSON | [TODO: DEFINE] Define reliability tiers for source types. | Yes |
| Mycroft adaptation source | Markdown | `/Users/bear/Documents/CoWork/bear-textbooks/books/mycroft/recipes/news-monitoring-agent.md` and `mycroft-news-intelligence-agent.md` | No |

## Phase Gates

1. Watchlist gate: brand and competitor terms are approved. Test: `python3 -m json.tool data/raw/madison-brand-news-reputation-monitor/watchlist.json`. Human capacity: [PF].
2. Source gate: every feed is approved and rate-safe. Test: `rg -n "TODO:" recipes/madison-brand-news-reputation-monitor.md`. Human capacity: [PA].
3. Sample gate: sample mode runs without live posting or alerts. Test: `snickerdoodle run madison-brand-news-reputation-monitor --mode dialogic --sample`. Human capacity: [TO].
4. Report gate: report separates sourced mentions from interpretation. Test: `rg -n "Reader:|Decision enabled:|Sections:" recipes/madison-brand-news-reputation-monitor.md`. Human capacity: [IJ].

## Steps

1. Step name: Ingest brand news. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/ingest/madison-brand-news-reputation-monitor__ingest-brand-news.py`
   Input: watchlist and approved feed list.
   Output: raw JSON fields: source, title, url, published_at, matched_terms, snippet, author, source_type.
   Where output goes: `data/raw/madison-brand-news-reputation-monitor/`.
2. Step name: Score reputation signal. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/gigo/madison-brand-news-reputation-monitor__score-reputation-signal.py`
   Input: raw news records and reliability rubric.
   Output: verified JSON fields: mention_id, brand, topic, sentiment_label, reliability_score, severity, evidence_url, flags.
   Where output goes: `data/verified/madison-brand-news-reputation-monitor/`.
3. Step name: Produce reputation report. Labor: AI with Human review.
   Script called: `[TODO: DEV] Create scripts/tools/madison-brand-news-reputation-monitor__produce-reputation-report.py`
   Input: verified mentions and run log.
   Output: markdown sections: reputation summary, high-risk mentions, competitor moves, source reliability, recommended action.
   Where output goes: `reports/generated/`.

## Output Contract

### Agent output
File: `logs/madison-brand-news-reputation-monitor-[DATE].json`
Fields: `workflow`, `run_id`, `mode`, `steps_completed`, `records_seen`, `rejects`, `duplicates`, `flags`, `stop_conditions`, `todo_items`, `source_files`, `gate_decisions`, `generated_at`.

### Human report
File: `reports/generated/madison-brand-news-reputation-monitor-[DATE].md`
Reader: marketing communications lead.
Decision enabled: decide whether to respond publicly, monitor quietly, brief leadership, or update campaign messaging.
Sections: Run summary, source list, reputation-moving mentions, competitor mentions, sentiment labels, reliability scores, evidence links, recommended action.

## Stop Conditions

- Stop if watchlist terms are not approved because false matches can distort reputation decisions.
- Stop if source reliability cannot be scored because the report would overstate weak sources.
- Stop if an alert or public response is requested without human approval.

## Snickerdoodle

### Run Commands
Full dialogic run: `snickerdoodle run madison-brand-news-reputation-monitor --mode dialogic`
Sample mode: `snickerdoodle run madison-brand-news-reputation-monitor --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Ingest brand news | `snickerdoodle run madison-brand-news-reputation-monitor --step ingest-brand-news` | `--sample` |
| Score reputation signal | `snickerdoodle run madison-brand-news-reputation-monitor --step score-reputation-signal` |  |
| Produce reputation report | `snickerdoodle run madison-brand-news-reputation-monitor --step produce-reputation-report` | `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - watchlist approval | `snickerdoodle gate madison-brand-news-reputation-monitor --gate 1 --decision approve --note "..."` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Ingest brand news | `[TODO: DEV] scripts/ingest/madison-brand-news-reputation-monitor__ingest-brand-news.py` | ingest |
| Score reputation signal | `[TODO: DEV] scripts/gigo/madison-brand-news-reputation-monitor__score-reputation-signal.py` | gigo |
| Produce reputation report | `[TODO: DEV] scripts/tools/madison-brand-news-reputation-monitor__produce-reputation-report.py` | tool |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/madison-brand-news-reputation-monitor/` | JSON |
| Verified data | `data/verified/madison-brand-news-reputation-monitor/` | JSON |
| Agent log | `logs/madison-brand-news-reputation-monitor-[DATE].json` | JSON |
| Human report | `reports/generated/madison-brand-news-reputation-monitor-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

