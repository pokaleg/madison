# Madison Brand Sentiment Monitor

## Purpose

Classifies brand and category coverage by sentiment and review urgency so marketing teams can see where customer trust, campaign response, or category mood is improving or deteriorating.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Brand query config | JSON | [TODO: DATA SOURCE] Approved brand, competitor, and category terms. | Yes |
| Article or social records | JSON | [TODO: DATA SOURCE] NewsAPI, RSS, reviews, or approved social archive. | Yes |
| Sentiment rubric | JSON | [TODO: DEFINE] Define positive, neutral, negative, mixed, and urgent criteria. | Yes |
| Mycroft adaptation source | Markdown | `/Users/bear/Documents/CoWork/bear-textbooks/books/mycroft/recipes/ai-news-sentiment-agent.md` | No |

## Phase Gates

1. Query gate: brand terms and exclusions are approved. Test: `python3 -m json.tool data/raw/madison-brand-sentiment-monitor/query-config.json`. Human capacity: [PF].
2. Rubric gate: sentiment labels are defined before scoring. Test: `rg -n "TODO:" recipes/madison-brand-sentiment-monitor.md`. Human capacity: [IJ].
3. Sample gate: sample mode runs without email, Airtable, or dashboard writes. Test: `snickerdoodle run madison-brand-sentiment-monitor --mode dialogic --sample`. Human capacity: [TO].

## Steps

1. Step name: Ingest sentiment records. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/ingest/madison-brand-sentiment-monitor__ingest-sentiment-records.py`
   Input: query config and approved local or live source.
   Output: raw JSON fields: record_id, source, title, body_snippet, url, published_at, matched_brand, matched_category.
   Where output goes: `data/raw/madison-brand-sentiment-monitor/`.
2. Step name: Score brand sentiment. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/gigo/madison-brand-sentiment-monitor__score-brand-sentiment.py`
   Input: raw records and sentiment rubric.
   Output: verified JSON fields: record_id, sentiment_label, confidence, urgency_flag, rationale, source_url, review_required.
   Where output goes: `data/verified/madison-brand-sentiment-monitor/`.
3. Step name: Produce sentiment report. Labor: AI with Human review.
   Script called: `[TODO: DEV] Create scripts/tools/madison-brand-sentiment-monitor__produce-sentiment-report.py`
   Input: verified sentiment records.
   Output: markdown sections: sentiment counts, urgent negative items, evidence links, campaign implications, next actions.
   Where output goes: `reports/generated/`.

## Output Contract

### Agent output
File: `logs/madison-brand-sentiment-monitor-[DATE].json`
Fields: `workflow`, `run_id`, `mode`, `steps_completed`, `records_seen`, `rejects`, `duplicates`, `flags`, `stop_conditions`, `todo_items`, `source_files`, `gate_decisions`, `generated_at`.

### Human report
File: `reports/generated/madison-brand-sentiment-monitor-[DATE].md`
Reader: brand strategist or marketing analyst.
Decision enabled: decide whether sentiment requires messaging changes, escalation, or continued monitoring.
Sections: Source coverage, sentiment summary, urgent items, representative evidence, limitations, recommended action.

## Stop Conditions

- Stop if sentiment rubric is undefined because labels would be arbitrary.
- Stop if records lack source URLs because findings cannot be audited.
- Stop if sentiment output is used as investment or legal advice.

## Snickerdoodle

### Run Commands
Full dialogic run: `snickerdoodle run madison-brand-sentiment-monitor --mode dialogic`
Sample mode: `snickerdoodle run madison-brand-sentiment-monitor --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Ingest sentiment records | `snickerdoodle run madison-brand-sentiment-monitor --step ingest-sentiment-records` | `--sample` |
| Score brand sentiment | `snickerdoodle run madison-brand-sentiment-monitor --step score-brand-sentiment` |  |
| Produce sentiment report | `snickerdoodle run madison-brand-sentiment-monitor --step produce-sentiment-report` | `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - query approval | `snickerdoodle gate madison-brand-sentiment-monitor --gate 1 --decision approve --note "..."` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Ingest sentiment records | `[TODO: DEV] scripts/ingest/madison-brand-sentiment-monitor__ingest-sentiment-records.py` | ingest |
| Score brand sentiment | `[TODO: DEV] scripts/gigo/madison-brand-sentiment-monitor__score-brand-sentiment.py` | gigo |
| Produce sentiment report | `[TODO: DEV] scripts/tools/madison-brand-sentiment-monitor__produce-sentiment-report.py` | tool |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/madison-brand-sentiment-monitor/` | JSON |
| Verified data | `data/verified/madison-brand-sentiment-monitor/` | JSON |
| Agent log | `logs/madison-brand-sentiment-monitor-[DATE].json` | JSON |
| Human report | `reports/generated/madison-brand-sentiment-monitor-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

