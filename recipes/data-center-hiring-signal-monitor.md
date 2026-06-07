# Data Center Hiring Signal Monitor

## Purpose

Combines BLS labor series, NewsAPI coverage about AWS data-center hiring, and local sample job-market records to surface hiring and infrastructure demand signals. The business question is: what signals from these specific sources are reliable enough for a human boss to use in labor and hiring intelligence decisions?

## Source Inventory

| Source Node | Node Type | Source URL or Path | Human Check |
|---|---|---|---|
| Fetch BLS labor time-series data | `httpRequest` | `https://api.bls.gov/publicAPI/v2/timeseries/data/` | Confirm source is allowed, current, and rate-safe before live fetch. |
| Fetch NewsAPI AWS data-center hiring articles | `httpRequest` | [TODO: APPROVE] Migrate embedded credential to env var before live use: `https://newsapi.org/v2/everything?q=data+center+hiring+AWS&pageSize=100&apiKey=[REDACTED_USE_ENV]` | Credential was embedded in the original n8n URL; replace with environment variable and record `[TODO: APPROVE] credential migration` before live use. |

| Node Name | Node Type | Classification |
|---|---|---|
| When clicking 'Execute workflow' | `manualTrigger` | conductor |
| Fetch BLS labor time-series data | `httpRequest` | ingest |
| Fetch NewsAPI AWS data-center hiring articles | `httpRequest` | ingest |
| Parse local data-center job-market sample records | `code` | gigo |
| Merge, clean, and deduplicate hiring signals | `code` | gigo |
| Prepare data-center hiring signal export | `convertToFile` | tool |
## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Original n8n workflow JSON | JSON | [TODO: DATA SOURCE] Restore or move original workflow JSON to a repo-local path. Last documented path: pantry/bykovdenis_454895_41780985_Bykov_Denis_A3_Workflow.json | Yes |
| Fetch BLS labor time-series data | Source payload | `https://api.bls.gov/publicAPI/v2/timeseries/data/` | Yes |
| Fetch NewsAPI AWS data-center hiring articles | Source payload | [TODO: APPROVE] Migrate embedded credential to env var before live use: `https://newsapi.org/v2/everything?q=data+center+hiring+AWS&pageSize=100&apiKey=[REDACTED_USE_ENV]` | Yes |

## Phase Gates

1. Source gate: All required source paths are present or explicitly marked with a typed TODO. Test: `test -f "recipes/data-center-hiring-signal-monitor.md" && rg -n "\[TODO: DEFINE]" "recipes/data-center-hiring-signal-monitor.md" || true`. Human capacity: [TO].
2. Scope gate: The run declares `sample` mode or an approved live mode before ingest begins. Test: `python3 -m json.tool data/raw/data-center-hiring-signal-monitor/run-envelope.json`. Human capacity: [PF].
3. Data-shape gate: Every raw and verified JSON output parses before downstream scripts run. Test: `find data/raw/data-center-hiring-signal-monitor data/verified/data-center-hiring-signal-monitor -name "*.json" -print -exec python3 -m json.tool {} \;`. Human capacity: [PA].
4. Script-readiness gate: Every step script exists or is represented by a typed development TODO. Test: `test -f scripts/ingest/data-center-hiring-signal-monitor-ingest-inputs.py || rg --fixed-strings "[TODO: DEV]" "recipes/data-center-hiring-signal-monitor.md"`. Human capacity: [IJ].
5. Approval gate: Live network calls, external writes, credentials, production databases, emails, dashboards, publishing, or model calls with sensitive data require an approval record. Test: `test -f logs/gate-decisions/data-center-hiring-signal-monitor-approval.json || rg --fixed-strings "[TODO: APPROVE]" "recipes/data-center-hiring-signal-monitor.md"`. Human capacity: [EI].
6. Report gate: Agent log and human report are written with the required fields and sections. Test: `test -f logs/data-center-hiring-signal-monitor-[DATE].json && test -f reports/generated/data-center-hiring-signal-monitor-[DATE].md`. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI with Human gate.
   Script called: `scripts/tools/data-center-hiring-signal-monitor-verify-provenance.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `data-center-hiring-signal-monitor`.
   Output: workflow, source_paths, exists, parsed_ok, approval_state, checked_at.
   Where output goes: `logs/`
2. Step name: Ingest declared inputs. Labor: AI with Human gate.
   Script called: `scripts/ingest/data-center-hiring-signal-monitor-ingest-inputs.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `data-center-hiring-signal-monitor`.
   Output: records, source_name, source_type, fetched_at, sample_mode, rejects.
   Where output goes: `data/raw/data-center-hiring-signal-monitor/`
3. Step name: Validate data shape. Labor: AI with Human gate.
   Script called: `scripts/gigo/data-center-hiring-signal-monitor-validate-data-shape.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `data-center-hiring-signal-monitor`.
   Output: record_count, required_fields_present, missing_fields, parse_errors, schema_version.
   Where output goes: `data/verified/data-center-hiring-signal-monitor/`
4. Step name: Transform and quality check. Labor: AI with Human gate.
   Script called: `scripts/gigo/data-center-hiring-signal-monitor-transform-quality-check.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `data-center-hiring-signal-monitor`.
   Output: verified_records, record_count, duplicates, rejects, flags, quality_notes.
   Where output goes: `data/verified/data-center-hiring-signal-monitor/`
5. Step name: Run approved tools. Labor: AI with Human gate.
   Script called: `scripts/tools/data-center-hiring-signal-monitor-run-approved-tools.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `data-center-hiring-signal-monitor`.
   Output: tool_name, input_path, output_path, action_taken, approval_id, no_write_mode.
   Where output goes: `logs/`
6. Step name: Produce human report. Labor: AI with Human gate.
   Script called: `scripts/tools/data-center-hiring-signal-monitor-produce-human-report.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `data-center-hiring-signal-monitor`.
   Output: summary, sources_checked, gate_results, findings, typed_todos, next_decision.
   Where output goes: `reports/generated/`

## Output Contract

### Agent output
File: `logs/data-center-hiring-signal-monitor-[DATE].json`
Fields: workflow, run_id, mode, steps_completed, records_seen, rejects, duplicates, flags, stop_conditions, todo_items, source_files, gate_decisions, generated_at, raw_output_paths, verified_output_paths, report_path.

### Human report
File: `reports/generated/data-center-hiring-signal-monitor-[DATE].md`
Reader: domain lead or human boss responsible for accepting the `Data Center Hiring Signal Monitor` run.
Decision enabled: approve the run for the next phase, request source/schema fixes, or block live execution.
Sections: run summary, purpose, source inventory, inputs used, phase-gate results, steps completed, records seen, rejects, duplicates, flags, typed TODOs, human approvals, verified findings, inferred findings, decision recommendation.

## Stop Conditions

- Stop if the recipe title or purpose does not match the original workflow intent.
- Stop if `pantry/bykovdenis_454895_41780985_Bykov_Denis_A3_Workflow.json` is missing or cannot be parsed.
- Stop if a source URL/path is unknown, stale, private, machine-specific, credential-bearing, or not approved; add `[TODO: APPROVE] replace source` and halt live mode.
- Stop if the workflow does not define critical fields for validation; add `[TODO: DEFINE] define required fields` before production.
- Stop if GIGO outputs do not expose record counts, rejects, duplicates, or missing fields.
- Stop if a final claim is not traceable to source or verified records.
- Stop if generated reports would expose credentials, private tokens, private local paths, or unapproved personal data.
- Stop if any live model, database, email, dashboard, file export, or API write is requested without explicit human approval.

## Snickerdoodle

### Run Commands
Full dialogic run:
`snickerdoodle run data-center-hiring-signal-monitor --mode dialogic`

Sample mode (no live network calls, no writes):
`snickerdoodle run data-center-hiring-signal-monitor --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Verify provenance | `snickerdoodle run data-center-hiring-signal-monitor --step verify-provenance` | `--sample` `--no-write` |
| Ingest declared inputs | `snickerdoodle run data-center-hiring-signal-monitor --step ingest-inputs` | `--sample` |
| Validate data shape | `snickerdoodle run data-center-hiring-signal-monitor --step validate-data-shape` | `--sample` |
| Transform and quality check | `snickerdoodle run data-center-hiring-signal-monitor --step transform-quality-check` | `--sample` |
| Run approved tools | `snickerdoodle run data-center-hiring-signal-monitor --step run-approved-tools` | `--sample` `--no-write` |
| Produce human report | `snickerdoodle run data-center-hiring-signal-monitor --step produce-human-report` | `--sample` `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - Source gate | `snickerdoodle gate data-center-hiring-signal-monitor --gate 1 --decision approve --note "Sources checked"` |
| Gate 2 - Scope gate | `snickerdoodle gate data-center-hiring-signal-monitor --gate 2 --decision approve --note "Scope and mode approved"` |
| Gate 3 - Data-shape gate | `snickerdoodle gate data-center-hiring-signal-monitor --gate 3 --decision approve --note "Outputs parse"` |
| Gate 4 - Script-readiness gate | `snickerdoodle gate data-center-hiring-signal-monitor --gate 4 --decision approve --note "Scripts ready or TODO DEV accepted"` |
| Gate 5 - Approval gate | `snickerdoodle gate data-center-hiring-signal-monitor --gate 5 --decision approve --note "Live or sensitive actions approved"` |
| Gate 6 - Report gate | `snickerdoodle gate data-center-hiring-signal-monitor --gate 6 --decision approve --note "Report and log complete"` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Verify provenance | `scripts/tools/data-center-hiring-signal-monitor-verify-provenance.py` | tools |
| Ingest declared inputs | `scripts/ingest/data-center-hiring-signal-monitor-ingest-inputs.py` | ingest |
| Validate data shape | `scripts/gigo/data-center-hiring-signal-monitor-validate-data-shape.py` | gigo |
| Transform and quality check | `scripts/gigo/data-center-hiring-signal-monitor-transform-quality-check.py` | gigo |
| Run approved tools | `scripts/tools/data-center-hiring-signal-monitor-run-approved-tools.py` | tools |
| Produce human report | `scripts/tools/data-center-hiring-signal-monitor-produce-human-report.py` | tools |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/data-center-hiring-signal-monitor/` | JSON |
| Verified data | `data/verified/data-center-hiring-signal-monitor/` | JSON |
| Agent log | `logs/data-center-hiring-signal-monitor-[DATE].json` | JSON |
| Human report | `reports/generated/data-center-hiring-signal-monitor-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

## Provenance

| Source | Verification command | Notes |
|---|---|---|
| `pantry/bykovdenis_454895_41780985_Bykov_Denis_A3_Workflow.json` | `test -f "pantry/bykovdenis_454895_41780985_Bykov_Denis_A3_Workflow.json"` | Referenced source/evidence path from prior recipe text. |

## Existing Recipe Notes Preserved For Implementation

### Extracted Notes

Combines BLS labor series, NewsAPI coverage about AWS data-center hiring, and local sample job-market records to surface hiring and infrastructure demand signals. The business question is: what signals from these specific sources are reliable enough for a human boss to use in labor and hiring intelligence decisions?

1. Source identity gate: Original workflow JSON exists and is the intended source. Test: `test -f "pantry/bykovdenis_454895_41780985_Bykov_Denis_A3_Workflow.json"`; if this fails, close [TODO: DATA SOURCE] by restoring or moving the workflow JSON before live mode.
   Human capacity: [PF].
2. Input readiness gate: Every required input in this recipe exists or is marked with a typed TODO. Test: `rg -n "TODO:" recipes/data-center-hiring-signal-monitor.md`.
   Human capacity: [PA].
3. Sample run gate: Ingest and tool steps run without live side effects before live mode. Test: `snickerdoodle run data-center-hiring-signal-monitor --mode dialogic --sample`.
   Human capacity: [TO].
4. Data-shape gate: Raw and verified outputs parse as JSON where applicable. Test: `find data/raw/data-center-hiring-signal-monitor data/verified/data-center-hiring-signal-monitor -name "*.json" -print -exec python3 -m json.tool {} \;`.
   Human capacity: [IJ].
5. Report contract gate: Human report defines reader, decision enabled, and sections. Test: `rg -n "Reader:|Decision enabled:|Sections:" recipes/data-center-hiring-signal-monitor.md`.
   Human capacity: [EI].

1. Step name: Verify provenance and source intent. Labor: Human.
   Human action: Record approval, rejection, or requested changes with supervisory capacity label [TODO: DEFINE].
   Input: pantry/bykovdenis_454895_41780985_Bykov_Denis_A3_Workflow.json.
   Output: provenance fields: workflow_path, exists, parsed_ok, title_matches_pipeline, source_inventory_checked.
   Where output goes: logs/gate-decisions/.
2. Step name: Fetch BLS labor time-series data. Labor: AI with Human gate.
   Script called: `scripts/ingest/data-center-hiring-signal-monitor-fetch-bls-labor-time-series-data.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
3. Step name: Fetch NewsAPI AWS data-center hiring articles. Labor: AI with Human gate.
   Script called: `scripts/ingest/data-center-hiring-signal-monitor-fetch-newsapi-aws-data-center-hiring-articles.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
4. Step name: Parse local data-center job-market sample records. Labor: AI with Human gate.
   Script called: `scripts/gigo/data-center-hiring-signal-monitor-parse-local-data-center-job-market-sample-records.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
5. Step name: Merge, clean, and deduplicate hiring signals. Labor: AI with Human gate.
   Script called: `scripts/gigo/data-center-hiring-signal-monitor-merge-clean-and-deduplicate-hiring-signals.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
6. Step name: Prepare data-center hiring signal export. Labor: AI with Human gate.
   Script called: `scripts/tools/data-center-hiring-signal-monitor-prepare-data-center-hiring-signal-export.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
7. Step name: Produce human report. Labor: AI with Human review.
   Script called: `scripts/tools/data-center-hiring-signal-monitor-produce-human-report.py`
   Input: agent log plus raw and verified outputs.
   Output: markdown report sections: run summary, source inventory, inputs used, validation results, flags, typed TODOs, decision recommendation.
   Where output goes: reports/generated/.
