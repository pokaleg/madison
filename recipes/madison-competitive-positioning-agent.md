# Madison Competitive Positioning Agent

## Purpose

Compares brands across messaging, offers, pricing signals, product features, proof points, and audience promises so a strategist can identify where a company is differentiated, overmatched, or unclear.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Competitor list | JSON | [TODO: DATA SOURCE] Approved competitor and comparison-set list. | Yes |
| Brand evidence corpus | JSON/Markdown | [TODO: DATA SOURCE] Websites, landing pages, ads, product pages, press pages, and sales collateral. | Yes |
| Positioning rubric | JSON | [TODO: DEFINE] Define dimensions: promise, audience, price, feature, proof, tone, channel. | Yes |
| Mycroft adaptation source | Markdown | `/Users/bear/Documents/CoWork/bear-textbooks/books/mycroft/recipes/comparativeanalysisagent.md` | No |

## Phase Gates

1. Competitor gate: comparison set is approved. Test: `python3 -m json.tool data/raw/madison-competitive-positioning-agent/competitors.json`. Human capacity: [PF].
2. Evidence gate: every source has a URL or file path. Test: `rg -n "TODO:" recipes/madison-competitive-positioning-agent.md`. Human capacity: [PA].
3. Sample gate: sample mode runs without scraping unapproved sites. Test: `snickerdoodle run madison-competitive-positioning-agent --mode dialogic --sample`. Human capacity: [TO].

## Steps

1. Step name: Ingest competitor evidence. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/ingest/madison-competitive-positioning-agent__ingest-competitor-evidence.py`
   Input: competitor list and evidence corpus.
   Output: raw JSON fields: company, source_type, url_or_path, message_text, offer_text, product_feature, proof_point, collected_at.
   Where output goes: `data/raw/madison-competitive-positioning-agent/`.
2. Step name: Compare positioning. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/gigo/madison-competitive-positioning-agent__compare-positioning.py`
   Input: raw evidence records and positioning rubric.
   Output: verified JSON fields: company, dimension, claim, strength_score, differentiation_flag, evidence_ref, notes.
   Where output goes: `data/verified/madison-competitive-positioning-agent/`.
3. Step name: Produce positioning report. Labor: AI with Human review.
   Script called: `[TODO: DEV] Create scripts/tools/madison-competitive-positioning-agent__produce-positioning-report.py`
   Input: verified positioning comparisons.
   Output: markdown sections: positioning map, competitor strengths, gaps, white-space opportunities, source evidence.
   Where output goes: `reports/generated/`.

## Output Contract

### Agent output
File: `logs/madison-competitive-positioning-agent-[DATE].json`
Fields: `workflow`, `run_id`, `mode`, `steps_completed`, `records_seen`, `rejects`, `duplicates`, `flags`, `stop_conditions`, `todo_items`, `source_files`, `gate_decisions`, `generated_at`.

### Human report
File: `reports/generated/madison-competitive-positioning-agent-[DATE].md`
Reader: brand strategist.
Decision enabled: choose positioning changes, messaging tests, competitor responses, or research gaps.
Sections: Competitor set, dimensions compared, evidence table, positioning gaps, differentiation opportunities, recommended next tests.

## Stop Conditions

- Stop if competitor set is unapproved because comparisons can become misleading.
- Stop if evidence lacks source references because claims cannot be audited.
- Stop if report recommends legal, pricing, or product changes without human review.

## Snickerdoodle

### Run Commands
Full dialogic run: `snickerdoodle run madison-competitive-positioning-agent --mode dialogic`
Sample mode: `snickerdoodle run madison-competitive-positioning-agent --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Ingest competitor evidence | `snickerdoodle run madison-competitive-positioning-agent --step ingest-competitor-evidence` | `--sample` |
| Compare positioning | `snickerdoodle run madison-competitive-positioning-agent --step compare-positioning` |  |
| Produce positioning report | `snickerdoodle run madison-competitive-positioning-agent --step produce-positioning-report` | `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - competitor approval | `snickerdoodle gate madison-competitive-positioning-agent --gate 1 --decision approve --note "..."` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Ingest competitor evidence | `[TODO: DEV] scripts/ingest/madison-competitive-positioning-agent__ingest-competitor-evidence.py` | ingest |
| Compare positioning | `[TODO: DEV] scripts/gigo/madison-competitive-positioning-agent__compare-positioning.py` | gigo |
| Produce positioning report | `[TODO: DEV] scripts/tools/madison-competitive-positioning-agent__produce-positioning-report.py` | tool |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/madison-competitive-positioning-agent/` | JSON |
| Verified data | `data/verified/madison-competitive-positioning-agent/` | JSON |
| Agent log | `logs/madison-competitive-positioning-agent-[DATE].json` | JSON |
| Human report | `reports/generated/madison-competitive-positioning-agent-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

