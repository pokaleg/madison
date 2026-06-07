# Madison Consumer Trust Anxiety Index

## Purpose

Measures customer concern, backlash, review stress, and trust erosion signals around a brand or category so marketing teams can decide when reassurance, education, service recovery, or escalation is needed.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Brand/category watchlist | JSON | [TODO: DATA SOURCE] Approved brand, product, issue, and category terms. | Yes |
| Concern signal records | JSON/RSS/CSV | [TODO: DATA SOURCE] Reviews, support themes, social archive, news, forums, or survey exports. | Yes |
| Anxiety rubric | JSON | [TODO: DEFINE] Define concern, confusion, anger, distrust, uncertainty, and escalation criteria. | Yes |
| Mycroft adaptation source | Markdown | `/Users/bear/Documents/CoWork/bear-textbooks/books/mycroft/recipes/retail-investor-anxiety-index.md` | No |

## Phase Gates

1. Scope gate: issue categories and brand terms are approved. Test: `python3 -m json.tool data/raw/madison-consumer-trust-anxiety-index/watchlist.json`. Human capacity: [PF].
2. Privacy gate: no private customer data is ingested without approval. Test: `rg -n "TODO:" recipes/madison-consumer-trust-anxiety-index.md`. Human capacity: [EI].
3. Sample gate: sample mode uses local records only. Test: `snickerdoodle run madison-consumer-trust-anxiety-index --mode dialogic --sample`. Human capacity: [TO].

## Steps

1. Step name: Ingest concern signals. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/ingest/madison-consumer-trust-anxiety-index__ingest-concern-signals.py`
   Input: watchlist and approved concern signal sources.
   Output: raw JSON fields: source, source_type, text, url_or_record_id, published_at, matched_terms, privacy_flags.
   Where output goes: `data/raw/madison-consumer-trust-anxiety-index/`.
2. Step name: Score trust anxiety. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/gigo/madison-consumer-trust-anxiety-index__score-trust-anxiety.py`
   Input: raw concern signals and anxiety rubric.
   Output: verified JSON fields: signal_id, issue_category, anxiety_score, trust_risk_level, evidence_ref, recommended_response_type.
   Where output goes: `data/verified/madison-consumer-trust-anxiety-index/`.
3. Step name: Produce trust anxiety report. Labor: AI with Human review.
   Script called: `[TODO: DEV] Create scripts/tools/madison-consumer-trust-anxiety-index__produce-trust-anxiety-report.py`
   Input: verified anxiety signals.
   Output: markdown sections: trust index, top concerns, evidence samples, affected channels, response recommendation.
   Where output goes: `reports/generated/`.

## Output Contract

### Agent output
File: `logs/madison-consumer-trust-anxiety-index-[DATE].json`
Fields: `workflow`, `run_id`, `mode`, `steps_completed`, `records_seen`, `rejects`, `duplicates`, `flags`, `stop_conditions`, `todo_items`, `source_files`, `gate_decisions`, `generated_at`.

### Human report
File: `reports/generated/madison-consumer-trust-anxiety-index-[DATE].md`
Reader: customer marketing or brand trust lead.
Decision enabled: decide whether to reassure customers, update messaging, escalate to service/legal, or continue monitoring.
Sections: Signal sources, anxiety index, issue categories, evidence examples, privacy flags, recommended response.

## Stop Conditions

- Stop if private customer data appears without approval.
- Stop if anxiety rubric is undefined because scores would not be interpretable.
- Stop if the report recommends customer outreach or public response without human review.

## Snickerdoodle

### Run Commands
Full dialogic run: `snickerdoodle run madison-consumer-trust-anxiety-index --mode dialogic`
Sample mode: `snickerdoodle run madison-consumer-trust-anxiety-index --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Ingest concern signals | `snickerdoodle run madison-consumer-trust-anxiety-index --step ingest-concern-signals` | `--sample` |
| Score trust anxiety | `snickerdoodle run madison-consumer-trust-anxiety-index --step score-trust-anxiety` |  |
| Produce trust anxiety report | `snickerdoodle run madison-consumer-trust-anxiety-index --step produce-trust-anxiety-report` | `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - privacy approval | `snickerdoodle gate madison-consumer-trust-anxiety-index --gate 1 --decision approve --note "..."` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Ingest concern signals | `[TODO: DEV] scripts/ingest/madison-consumer-trust-anxiety-index__ingest-concern-signals.py` | ingest |
| Score trust anxiety | `[TODO: DEV] scripts/gigo/madison-consumer-trust-anxiety-index__score-trust-anxiety.py` | gigo |
| Produce trust anxiety report | `[TODO: DEV] scripts/tools/madison-consumer-trust-anxiety-index__produce-trust-anxiety-report.py` | tool |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/madison-consumer-trust-anxiety-index/` | JSON |
| Verified data | `data/verified/madison-consumer-trust-anxiety-index/` | JSON |
| Agent log | `logs/madison-consumer-trust-anxiety-index-[DATE].json` | JSON |
| Human report | `reports/generated/madison-consumer-trust-anxiety-index-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

