# Madison Market Momentum Funding Monitor

## Purpose

Tracks funding, acquisitions, partnerships, and category investment signals so marketing teams can identify where a market is heating up, which competitors are gaining narrative momentum, and where campaigns need stronger proof.

## Source Inventory

| Source Node | Node Type | Source URL or Path | Human Check |
|---|---|---|---|
| Recipe specification | Markdown recipe | `recipes/madison-market-momentum-funding-monitor.md` | Confirm this specification is current and approved before script generation. |

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Category watchlist | JSON | [TODO: DATA SOURCE] Approved categories, competitors, and investor keywords. | Yes |
| Funding and company sources | RSS/API/CSV | [TODO: DATA SOURCE] Funding news, SEC/company datasets, press releases, and partnership feeds. | Yes |
| Momentum rubric | JSON | [TODO: DEFINE] Define funding size, strategic relevance, recency, and competitor proximity scoring. | Yes |
| Mycroft adaptation source | Markdown | `/Users/bear/Documents/CoWork/bear-textbooks/books/mycroft/recipes/funding-intelligence-agent.md` | No |

## Phase Gates

1. Source gate: All required source paths are present or explicitly marked with a typed TODO. Test: `test -f "recipes/madison-market-momentum-funding-monitor.md" && rg -n "\[TODO: DEFINE]" "recipes/madison-market-momentum-funding-monitor.md" || true`. Human capacity: [TO].
2. Scope gate: The run declares `sample` mode or an approved live mode before ingest begins. Test: `python3 -m json.tool data/raw/madison-market-momentum-funding-monitor/run-envelope.json`. Human capacity: [PF].
3. Data-shape gate: Every raw and verified JSON output parses before downstream scripts run. Test: `find data/raw/madison-market-momentum-funding-monitor data/verified/madison-market-momentum-funding-monitor -name "*.json" -print -exec python3 -m json.tool {} \;`. Human capacity: [PA].
4. Script-readiness gate: Every step script exists or is represented by a typed development TODO. Test: `test -f scripts/ingest/madison-market-momentum-funding-monitor-ingest-inputs.py || rg --fixed-strings "[TODO: DEV]" "recipes/madison-market-momentum-funding-monitor.md"`. Human capacity: [IJ].
5. Approval gate: Live network calls, external writes, credentials, production databases, emails, dashboards, publishing, or model calls with sensitive data require an approval record. Test: `test -f logs/gate-decisions/madison-market-momentum-funding-monitor-approval.json || rg --fixed-strings "[TODO: APPROVE]" "recipes/madison-market-momentum-funding-monitor.md"`. Human capacity: [EI].
6. Report gate: Agent log and human report are written with the required fields and sections. Test: `test -f logs/madison-market-momentum-funding-monitor-[DATE].json && test -f reports/generated/madison-market-momentum-funding-monitor-[DATE].md`. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI with Human gate.
   Script called: `scripts/tools/madison-market-momentum-funding-monitor-verify-provenance.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `madison-market-momentum-funding-monitor`.
   Output: workflow, source_paths, exists, parsed_ok, approval_state, checked_at.
   Where output goes: `logs/`
2. Step name: Ingest declared inputs. Labor: AI with Human gate.
   Script called: `scripts/ingest/madison-market-momentum-funding-monitor-ingest-inputs.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `madison-market-momentum-funding-monitor`.
   Output: records, source_name, source_type, fetched_at, sample_mode, rejects.
   Where output goes: `data/raw/madison-market-momentum-funding-monitor/`
3. Step name: Validate data shape. Labor: AI with Human gate.
   Script called: `scripts/gigo/madison-market-momentum-funding-monitor-validate-data-shape.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `madison-market-momentum-funding-monitor`.
   Output: record_count, required_fields_present, missing_fields, parse_errors, schema_version.
   Where output goes: `data/verified/madison-market-momentum-funding-monitor/`
4. Step name: Transform and quality check. Labor: AI with Human gate.
   Script called: `scripts/gigo/madison-market-momentum-funding-monitor-transform-quality-check.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `madison-market-momentum-funding-monitor`.
   Output: verified_records, record_count, duplicates, rejects, flags, quality_notes.
   Where output goes: `data/verified/madison-market-momentum-funding-monitor/`
5. Step name: Run approved tools. Labor: AI with Human gate.
   Script called: `scripts/tools/madison-market-momentum-funding-monitor-run-approved-tools.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `madison-market-momentum-funding-monitor`.
   Output: tool_name, input_path, output_path, action_taken, approval_id, no_write_mode.
   Where output goes: `logs/`
6. Step name: Produce human report. Labor: AI with Human gate.
   Script called: `scripts/tools/madison-market-momentum-funding-monitor-produce-human-report.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `madison-market-momentum-funding-monitor`.
   Output: summary, sources_checked, gate_results, findings, typed_todos, next_decision.
   Where output goes: `reports/generated/`

## Output Contract

### Agent output
File: `logs/madison-market-momentum-funding-monitor-[DATE].json`
Fields: workflow, run_id, mode, steps_completed, records_seen, rejects, duplicates, flags, stop_conditions, todo_items, source_files, gate_decisions, generated_at, raw_output_paths, verified_output_paths, report_path.

### Human report
File: `reports/generated/madison-market-momentum-funding-monitor-[DATE].md`
Reader: domain lead or human boss responsible for accepting the `Madison Market Momentum Funding Monitor` run.
Decision enabled: approve the run for the next phase, request source/schema fixes, or block live execution.
Sections: run summary, purpose, source inventory, inputs used, phase-gate results, steps completed, records seen, rejects, duplicates, flags, typed TODOs, human approvals, verified findings, inferred findings, decision recommendation.

## Stop Conditions

- Stop if category watchlist is missing because market momentum cannot be scoped.
- Stop if funding amounts or event dates are missing and treated as facts.
- Stop if report suggests investment advice rather than marketing implications.

## Snickerdoodle

### Run Commands
Full dialogic run:
`snickerdoodle run madison-market-momentum-funding-monitor --mode dialogic`

Sample mode (no live network calls, no writes):
`snickerdoodle run madison-market-momentum-funding-monitor --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Verify provenance | `snickerdoodle run madison-market-momentum-funding-monitor --step verify-provenance` | `--sample` `--no-write` |
| Ingest declared inputs | `snickerdoodle run madison-market-momentum-funding-monitor --step ingest-inputs` | `--sample` |
| Validate data shape | `snickerdoodle run madison-market-momentum-funding-monitor --step validate-data-shape` | `--sample` |
| Transform and quality check | `snickerdoodle run madison-market-momentum-funding-monitor --step transform-quality-check` | `--sample` |
| Run approved tools | `snickerdoodle run madison-market-momentum-funding-monitor --step run-approved-tools` | `--sample` `--no-write` |
| Produce human report | `snickerdoodle run madison-market-momentum-funding-monitor --step produce-human-report` | `--sample` `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - Source gate | `snickerdoodle gate madison-market-momentum-funding-monitor --gate 1 --decision approve --note "Sources checked"` |
| Gate 2 - Scope gate | `snickerdoodle gate madison-market-momentum-funding-monitor --gate 2 --decision approve --note "Scope and mode approved"` |
| Gate 3 - Data-shape gate | `snickerdoodle gate madison-market-momentum-funding-monitor --gate 3 --decision approve --note "Outputs parse"` |
| Gate 4 - Script-readiness gate | `snickerdoodle gate madison-market-momentum-funding-monitor --gate 4 --decision approve --note "Scripts ready or TODO DEV accepted"` |
| Gate 5 - Approval gate | `snickerdoodle gate madison-market-momentum-funding-monitor --gate 5 --decision approve --note "Live or sensitive actions approved"` |
| Gate 6 - Report gate | `snickerdoodle gate madison-market-momentum-funding-monitor --gate 6 --decision approve --note "Report and log complete"` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Verify provenance | `scripts/tools/madison-market-momentum-funding-monitor-verify-provenance.py` | tools |
| Ingest declared inputs | `scripts/ingest/madison-market-momentum-funding-monitor-ingest-inputs.py` | ingest |
| Validate data shape | `scripts/gigo/madison-market-momentum-funding-monitor-validate-data-shape.py` | gigo |
| Transform and quality check | `scripts/gigo/madison-market-momentum-funding-monitor-transform-quality-check.py` | gigo |
| Run approved tools | `scripts/tools/madison-market-momentum-funding-monitor-run-approved-tools.py` | tools |
| Produce human report | `scripts/tools/madison-market-momentum-funding-monitor-produce-human-report.py` | tools |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/madison-market-momentum-funding-monitor/` | JSON |
| Verified data | `data/verified/madison-market-momentum-funding-monitor/` | JSON |
| Agent log | `logs/madison-market-momentum-funding-monitor-[DATE].json` | JSON |
| Human report | `reports/generated/madison-market-momentum-funding-monitor-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

## Provenance

| Source | Verification command | Notes |
|---|---|---|
| `recipes/madison-market-momentum-funding-monitor.md` | `test -f "recipes/madison-market-momentum-funding-monitor.md"` | Current recipe file used as spec-first provenance. |

## Existing Recipe Notes Preserved For Implementation

### Extracted Notes

Tracks funding, acquisitions, partnerships, and category investment signals so marketing teams can identify where a market is heating up, which competitors are gaining narrative momentum, and where campaigns need stronger proof.

1. Category gate: market categories and competitors are approved. Test: `python3 -m json.tool data/raw/madison-market-momentum-funding-monitor/category-watchlist.json`. Human capacity: [PF].
2. Source gate: funding sources are allowed and not paywalled/private. Test: `rg -n "TODO:" recipes/madison-market-momentum-funding-monitor.md`. Human capacity: [PA].
3. Sample gate: sample mode writes only local handoff files. Test: `snickerdoodle run madison-market-momentum-funding-monitor --mode dialogic --sample`. Human capacity: [TO].

1. Step name: Ingest market momentum signals. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/ingest/madison-market-momentum-funding-monitor-ingest-market-momentum-signals.py`
   Input: category watchlist and approved sources.
   Output: raw JSON fields: company, category, event_type, amount, investor_or_partner, source_url, announced_at, snippet.
   Where output goes: `data/raw/madison-market-momentum-funding-monitor/`.
2. Step name: Score market momentum. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/gigo/madison-market-momentum-funding-monitor-score-market-momentum.py`
   Input: raw momentum records and rubric.
   Output: verified JSON fields: signal_id, company, category, momentum_score, strategic_relevance, competitor_flag, evidence_url.
   Where output goes: `data/verified/madison-market-momentum-funding-monitor/`.
3. Step name: Produce momentum report. Labor: AI with Human review.
   Script called: `[TODO: DEV] Create scripts/tools/madison-market-momentum-funding-monitor-produce-momentum-report.py`
   Input: verified momentum records.
   Output: markdown sections: funding signals, partnerships, competitor momentum, category heat, marketing implications.
   Where output goes: `reports/generated/`.
