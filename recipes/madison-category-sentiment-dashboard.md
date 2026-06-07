# Madison Category Sentiment Dashboard

## Purpose

Aggregates public and owned-channel sentiment across a product category so marketers can see whether the category climate supports promotion, education, repositioning, or caution.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Category query config | JSON | [TODO: DATA SOURCE] Approved category terms, exclusions, competitors, and channels. | Yes |
| Sentiment records | JSON/CSV/RSS | [TODO: DATA SOURCE] News, review, survey, social archive, or support-theme records. | Yes |
| Dashboard schema | JSON | [TODO: DEV] Define chart fields, grouping keys, and date buckets. | Yes |
| Mycroft adaptation source | Markdown | `/Users/bear/Documents/CoWork/bear-textbooks/books/mycroft/recipes/market-sentiment-analysis-part-1.md` | No |

## Phase Gates

1. Category gate: query config is approved. Test: `python3 -m json.tool data/raw/madison-category-sentiment-dashboard/category-query-config.json`. Human capacity: [PF].
2. Dashboard gate: chart fields and date buckets are defined. Test: `rg -n "TODO:" recipes/madison-category-sentiment-dashboard.md`. Human capacity: [PA].
3. Sample gate: sample mode creates local dashboard data only. Test: `snickerdoodle run madison-category-sentiment-dashboard --mode dialogic --sample`. Human capacity: [TO].

## Steps

1. Step name: Ingest category sentiment records. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/ingest/madison-category-sentiment-dashboard__ingest-category-sentiment-records.py`
   Input: category query config and approved sentiment sources.
   Output: raw JSON fields: source, channel, text, url_or_record_id, published_at, category_term, brand_term.
   Where output goes: `data/raw/madison-category-sentiment-dashboard/`.
2. Step name: Aggregate category sentiment. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/gigo/madison-category-sentiment-dashboard__aggregate-category-sentiment.py`
   Input: raw sentiment records and dashboard schema.
   Output: verified JSON fields: date_bucket, channel, category, sentiment_counts, volume, confidence_notes, flags.
   Where output goes: `data/verified/madison-category-sentiment-dashboard/`.
3. Step name: Produce category dashboard report. Labor: AI with Human review.
   Script called: `[TODO: DEV] Create scripts/tools/madison-category-sentiment-dashboard__produce-category-dashboard-report.py`
   Input: verified dashboard data.
   Output: markdown sections: category mood, channel breakdown, sentiment trends, evidence samples, campaign timing recommendation.
   Where output goes: `reports/generated/`.

## Output Contract

### Agent output
File: `logs/madison-category-sentiment-dashboard-[DATE].json`
Fields: `workflow`, `run_id`, `mode`, `steps_completed`, `records_seen`, `rejects`, `duplicates`, `flags`, `stop_conditions`, `todo_items`, `source_files`, `gate_decisions`, `generated_at`.

### Human report
File: `reports/generated/madison-category-sentiment-dashboard-[DATE].md`
Reader: marketing planning lead.
Decision enabled: decide whether the category climate supports launch, pause, education, or messaging adjustment.
Sections: Category scope, data coverage, sentiment trend table, channel breakdown, evidence samples, limitations, recommendation.

## Stop Conditions

- Stop if category query config is missing because trends would be unscoped.
- Stop if dashboard schema is undefined because charts would be arbitrary.
- Stop if sentiment trends are reported without date buckets or source coverage.

## Snickerdoodle

### Run Commands
Full dialogic run: `snickerdoodle run madison-category-sentiment-dashboard --mode dialogic`
Sample mode: `snickerdoodle run madison-category-sentiment-dashboard --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Ingest category sentiment records | `snickerdoodle run madison-category-sentiment-dashboard --step ingest-category-sentiment-records` | `--sample` |
| Aggregate category sentiment | `snickerdoodle run madison-category-sentiment-dashboard --step aggregate-category-sentiment` |  |
| Produce category dashboard report | `snickerdoodle run madison-category-sentiment-dashboard --step produce-category-dashboard-report` | `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - category approval | `snickerdoodle gate madison-category-sentiment-dashboard --gate 1 --decision approve --note "..."` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Ingest category sentiment records | `[TODO: DEV] scripts/ingest/madison-category-sentiment-dashboard__ingest-category-sentiment-records.py` | ingest |
| Aggregate category sentiment | `[TODO: DEV] scripts/gigo/madison-category-sentiment-dashboard__aggregate-category-sentiment.py` | gigo |
| Produce category dashboard report | `[TODO: DEV] scripts/tools/madison-category-sentiment-dashboard__produce-category-dashboard-report.py` | tool |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/madison-category-sentiment-dashboard/` | JSON |
| Verified data | `data/verified/madison-category-sentiment-dashboard/` | JSON |
| Agent log | `logs/madison-category-sentiment-dashboard-[DATE].json` | JSON |
| Human report | `reports/generated/madison-category-sentiment-dashboard-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

