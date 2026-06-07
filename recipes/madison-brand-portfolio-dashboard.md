# Madison Brand Portfolio Dashboard

## Purpose

Tracks multiple brands, products, or campaigns as a portfolio so leadership can compare reputation, sentiment, momentum, risk, and readiness across the whole marketing estate.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Brand portfolio list | JSON | [TODO: DATA SOURCE] Approved brands, products, campaigns, or business units. | Yes |
| Portfolio metrics | JSON/CSV | [TODO: DATA SOURCE] Reputation, sentiment, campaign, traffic, sales, or service metrics. | Yes |
| Dashboard metric schema | JSON | [TODO: DEV] Define metric names, formulas, source priority, and rollup rules. | Yes |
| Mycroft adaptation source | Markdown | `/Users/bear/Documents/CoWork/bear-textbooks/books/mycroft/recipes/portfolio-dashboard.md` | No |

## Phase Gates

1. Portfolio gate: brands and campaigns are approved. Test: `python3 -m json.tool data/raw/madison-brand-portfolio-dashboard/portfolio-list.json`. Human capacity: [PF].
2. Metric gate: metric schema defines formulas and source priority. Test: `rg -n "TODO:" recipes/madison-brand-portfolio-dashboard.md`. Human capacity: [PA].
3. Sample gate: sample mode produces local dashboard JSON only. Test: `snickerdoodle run madison-brand-portfolio-dashboard --mode dialogic --sample`. Human capacity: [TO].

## Steps

1. Step name: Ingest portfolio metrics. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/ingest/madison-brand-portfolio-dashboard__ingest-portfolio-metrics.py`
   Input: portfolio list and approved metric sources.
   Output: raw JSON fields: portfolio_item, metric_name, metric_value, source, period_start, period_end, source_url_or_path.
   Where output goes: `data/raw/madison-brand-portfolio-dashboard/`.
2. Step name: Build portfolio dashboard data. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/gigo/madison-brand-portfolio-dashboard__build-portfolio-dashboard-data.py`
   Input: raw portfolio metrics and metric schema.
   Output: verified JSON fields: portfolio_item, health_score, sentiment_score, momentum_score, risk_score, missing_metrics, flags.
   Where output goes: `data/verified/madison-brand-portfolio-dashboard/`.
3. Step name: Produce portfolio dashboard report. Labor: AI with Human review.
   Script called: `[TODO: DEV] Create scripts/tools/madison-brand-portfolio-dashboard__produce-portfolio-dashboard-report.py`
   Input: verified dashboard data.
   Output: markdown sections: portfolio summary, winners, risks, missing data, leadership decisions.
   Where output goes: `reports/generated/`.

## Output Contract

### Agent output
File: `logs/madison-brand-portfolio-dashboard-[DATE].json`
Fields: `workflow`, `run_id`, `mode`, `steps_completed`, `records_seen`, `rejects`, `duplicates`, `flags`, `stop_conditions`, `todo_items`, `source_files`, `gate_decisions`, `generated_at`.

### Human report
File: `reports/generated/madison-brand-portfolio-dashboard-[DATE].md`
Reader: marketing executive or portfolio lead.
Decision enabled: decide which brands or campaigns need investment, intervention, deeper research, or pause.
Sections: Portfolio coverage, metric definitions, score table, high-risk items, growth opportunities, missing data, recommended decisions.

## Stop Conditions

- Stop if metric formulas are undefined because scores would be misleading.
- Stop if portfolio items are not approved because dashboard scope would be unstable.
- Stop if dashboard output is used to allocate budget without human review.

## Snickerdoodle

### Run Commands
Full dialogic run: `snickerdoodle run madison-brand-portfolio-dashboard --mode dialogic`
Sample mode: `snickerdoodle run madison-brand-portfolio-dashboard --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Ingest portfolio metrics | `snickerdoodle run madison-brand-portfolio-dashboard --step ingest-portfolio-metrics` | `--sample` |
| Build portfolio dashboard data | `snickerdoodle run madison-brand-portfolio-dashboard --step build-portfolio-dashboard-data` |  |
| Produce portfolio dashboard report | `snickerdoodle run madison-brand-portfolio-dashboard --step produce-portfolio-dashboard-report` | `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - portfolio approval | `snickerdoodle gate madison-brand-portfolio-dashboard --gate 1 --decision approve --note "..."` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Ingest portfolio metrics | `[TODO: DEV] scripts/ingest/madison-brand-portfolio-dashboard__ingest-portfolio-metrics.py` | ingest |
| Build portfolio dashboard data | `[TODO: DEV] scripts/gigo/madison-brand-portfolio-dashboard__build-portfolio-dashboard-data.py` | gigo |
| Produce portfolio dashboard report | `[TODO: DEV] scripts/tools/madison-brand-portfolio-dashboard__produce-portfolio-dashboard-report.py` | tool |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/madison-brand-portfolio-dashboard/` | JSON |
| Verified data | `data/verified/madison-brand-portfolio-dashboard/` | JSON |
| Agent log | `logs/madison-brand-portfolio-dashboard-[DATE].json` | JSON |
| Human report | `reports/generated/madison-brand-portfolio-dashboard-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

