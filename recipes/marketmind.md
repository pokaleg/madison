# marketmind

## Purpose

The marketmind workflow accepts a product-analysis request, normalizes market-analysis inputs, runs the stored marketmind implementation, extracts `outputs/final-market-strategy-report.md`, and returns a webhook-style JSON response. This recipe preserves the imported command flow while adding explicit phase gates around command execution, credentials, generated artifacts, and human-readable reporting.

## Source Inventory

| Source Node | Node Type | Source URL or Path | Human Check |
|---|---|---|---|
| Original workflow sources | [TODO: DEV] Parse original workflow node types. | [TODO: DATA SOURCE] Extract source URLs or paths from original workflow JSON. | Confirm source is allowed, current, and rate-safe before live fetch. |

| Node Name | Node Type | Classification |
|---|---|---|
| Original workflow node map | [TODO: DEV] Parse original n8n JSON. | [TODO: DEFINE] Classify parsed nodes as ingest, gigo, tool, conductor, or report. |
## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Original n8n workflow JSON | JSON | data/madison-main/n8n-workflows/originals/marketmind/marketmind-run-analysis-webhook.json | Yes |
| Product name | Text | Webhook body field `product_name`; default `EcoWave Smart Bottle` | Yes |
| Industry | Text | Webhook body field `industry`; default `Consumer Goods` | Yes |
| Geography | Text | Webhook body field `geography`; default `Global` | Yes |
| Scale | Text | Webhook body field `scale`; default `SME` | Yes |
| Repository path | Path | Stored marketmind code path | Yes |
| OpenAI API key | Environment variable | `OPENAI_API_KEY` | Only for live run |
| Serper API key | Environment variable | `SERPER_API_KEY` | Only for live run |

## Phase Gates

1. Source gate: All required source paths are present or explicitly marked with a typed TODO. Test: `test -f "recipes/marketmind.md" && rg -n "\[TODO: DEFINE]" "recipes/marketmind.md" || true`. Human capacity: [TO].
2. Scope gate: The run declares `sample` mode or an approved live mode before ingest begins. Test: `python3 -m json.tool data/raw/marketmind/run-envelope.json`. Human capacity: [PF].
3. Data-shape gate: Every raw and verified JSON output parses before downstream scripts run. Test: `find data/raw/marketmind data/verified/marketmind -name "*.json" -print -exec python3 -m json.tool {} \;`. Human capacity: [PA].
4. Script-readiness gate: Every step script exists or is represented by a typed development TODO. Test: `test -f scripts/ingest/marketmind-ingest-inputs.py || rg --fixed-strings "[TODO: DEV]" "recipes/marketmind.md"`. Human capacity: [IJ].
5. Approval gate: Live network calls, external writes, credentials, production databases, emails, dashboards, publishing, or model calls with sensitive data require an approval record. Test: `test -f logs/gate-decisions/marketmind-approval.json || rg --fixed-strings "[TODO: APPROVE]" "recipes/marketmind.md"`. Human capacity: [EI].
6. Report gate: Agent log and human report are written with the required fields and sections. Test: `test -f logs/marketmind-[DATE].json && test -f reports/generated/marketmind-[DATE].md`. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI with Human gate.
   Script called: `scripts/tools/marketmind-verify-provenance.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `marketmind`.
   Output: workflow, source_paths, exists, parsed_ok, approval_state, checked_at.
   Where output goes: `logs/`
2. Step name: Ingest declared inputs. Labor: AI with Human gate.
   Script called: `scripts/ingest/marketmind-ingest-inputs.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `marketmind`.
   Output: records, source_name, source_type, fetched_at, sample_mode, rejects.
   Where output goes: `data/raw/marketmind/`
3. Step name: Validate data shape. Labor: AI with Human gate.
   Script called: `scripts/gigo/marketmind-validate-data-shape.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `marketmind`.
   Output: record_count, required_fields_present, missing_fields, parse_errors, schema_version.
   Where output goes: `data/verified/marketmind/`
4. Step name: Transform and quality check. Labor: AI with Human gate.
   Script called: `scripts/gigo/marketmind-transform-quality-check.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `marketmind`.
   Output: verified_records, record_count, duplicates, rejects, flags, quality_notes.
   Where output goes: `data/verified/marketmind/`
5. Step name: Run approved tools. Labor: AI with Human gate.
   Script called: `scripts/tools/marketmind-run-approved-tools.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `marketmind`.
   Output: tool_name, input_path, output_path, action_taken, approval_id, no_write_mode.
   Where output goes: `logs/`
6. Step name: Produce human report. Labor: AI with Human gate.
   Script called: `scripts/tools/marketmind-produce-human-report.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `marketmind`.
   Output: summary, sources_checked, gate_results, findings, typed_todos, next_decision.
   Where output goes: `reports/generated/`

## Output Contract

### Agent output
File: `logs/marketmind-[DATE].json`
Fields: workflow, run_id, mode, steps_completed, records_seen, rejects, duplicates, flags, stop_conditions, todo_items, source_files, gate_decisions, generated_at, raw_output_paths, verified_output_paths, report_path.

### Human report
File: `reports/generated/marketmind-[DATE].md`
Reader: domain lead or human boss responsible for accepting the `marketmind` run.
Decision enabled: approve the run for the next phase, request source/schema fixes, or block live execution.
Sections: run summary, purpose, source inventory, inputs used, phase-gate results, steps completed, records seen, rejects, duplicates, flags, typed TODOs, human approvals, verified findings, inferred findings, decision recommendation.

## Stop Conditions

- Stop if the original workflow JSON is missing.
- Stop if stored marketmind code is missing.
- Stop if live mode is requested without explicit human clearance.
- Stop if live mode is requested without required environment variables.
- Stop if `main.py` exits nonzero or no final report is produced.
- Stop if the response contract would expose API keys, raw credentials, or full unreviewed stdout.
- Stop if the final report contains unverified claims that need human review before publication.

## Snickerdoodle

### Run Commands
Full dialogic run:
`snickerdoodle run marketmind --mode dialogic`

Sample mode (no live network calls, no writes):
`snickerdoodle run marketmind --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Verify provenance | `snickerdoodle run marketmind --step verify-provenance` | `--sample` `--no-write` |
| Ingest declared inputs | `snickerdoodle run marketmind --step ingest-inputs` | `--sample` |
| Validate data shape | `snickerdoodle run marketmind --step validate-data-shape` | `--sample` |
| Transform and quality check | `snickerdoodle run marketmind --step transform-quality-check` | `--sample` |
| Run approved tools | `snickerdoodle run marketmind --step run-approved-tools` | `--sample` `--no-write` |
| Produce human report | `snickerdoodle run marketmind --step produce-human-report` | `--sample` `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - Source gate | `snickerdoodle gate marketmind --gate 1 --decision approve --note "Sources checked"` |
| Gate 2 - Scope gate | `snickerdoodle gate marketmind --gate 2 --decision approve --note "Scope and mode approved"` |
| Gate 3 - Data-shape gate | `snickerdoodle gate marketmind --gate 3 --decision approve --note "Outputs parse"` |
| Gate 4 - Script-readiness gate | `snickerdoodle gate marketmind --gate 4 --decision approve --note "Scripts ready or TODO DEV accepted"` |
| Gate 5 - Approval gate | `snickerdoodle gate marketmind --gate 5 --decision approve --note "Live or sensitive actions approved"` |
| Gate 6 - Report gate | `snickerdoodle gate marketmind --gate 6 --decision approve --note "Report and log complete"` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Verify provenance | `scripts/tools/marketmind-verify-provenance.py` | tools |
| Ingest declared inputs | `scripts/ingest/marketmind-ingest-inputs.py` | ingest |
| Validate data shape | `scripts/gigo/marketmind-validate-data-shape.py` | gigo |
| Transform and quality check | `scripts/gigo/marketmind-transform-quality-check.py` | gigo |
| Run approved tools | `scripts/tools/marketmind-run-approved-tools.py` | tools |
| Produce human report | `scripts/tools/marketmind-produce-human-report.py` | tools |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/marketmind/` | JSON |
| Verified data | `data/verified/marketmind/` | JSON |
| Agent log | `logs/marketmind-[DATE].json` | JSON |
| Human report | `reports/generated/marketmind-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

## Provenance

| Source | Verification command | Notes |
|---|---|---|
| `data/madison-main/n8n-workflows/originals/marketmind/marketmind-run-analysis-webhook.json` | `test -f "data/madison-main/n8n-workflows/originals/marketmind/marketmind-run-analysis-webhook.json"` | Referenced source/evidence path from prior recipe text. |

## Existing Recipe Notes Preserved For Implementation

### Extracted Notes

The marketmind workflow accepts a product-analysis request, normalizes market-analysis inputs, runs the stored marketmind implementation, extracts `outputs/final-market-strategy-report.md`, and returns a webhook-style JSON response. This recipe preserves the imported command flow while adding explicit phase gates around command execution, credentials, generated artifacts, and human-readable reporting.

1. Source identity gate: Original workflow JSON exists and is the intended source. Test: `test -f "data/madison-main/n8n-workflows/originals/marketmind/marketmind-run-analysis-webhook.json"`.
   Human capacity: [PF].
2. Input readiness gate: Every required input in this recipe exists or is marked with a typed TODO. Test: `rg -n "TODO:" recipes/marketmind.md`.
   Human capacity: [PA].
3. Sample run gate: Ingest and tool steps run without live side effects before live mode. Test: `snickerdoodle run marketmind --mode dialogic --sample`.
   Human capacity: [TO].
4. Data-shape gate: Raw and verified outputs parse as JSON where applicable. Test: `find data/raw/marketmind data/verified/marketmind -name "*.json" -print -exec python3 -m json.tool {} \;`.
   Human capacity: [IJ].
5. Report contract gate: Human report defines reader, decision enabled, and sections. Test: `rg -n "Reader:|Decision enabled:|Sections:" recipes/marketmind.md`.
   Human capacity: [EI].

1. Step name: Verify provenance and source intent. Labor: Human.
   Human action: Record approval, rejection, or requested changes with supervisory capacity label [TODO: DEFINE].
   Input: data/madison-main/n8n-workflows/originals/marketmind/marketmind-run-analysis-webhook.json.
   Output: provenance fields: workflow_path, exists, parsed_ok, title_matches_pipeline, source_inventory_checked.
   Where output goes: logs/gate-decisions/.
2. Step name: Map workflow or specification to scripts. Labor: AI with Human gate.
   Script called: `scripts/gigo/marketmind-map-workflow-or-specification-to-scripts.py`
   Input: recipe inputs and provenance evidence.
   Output: implementation map fields: steps, script_paths, missing_specs, typed_todos.
   Where output goes: data/verified/.
3. Step name: Produce human report. Labor: AI with Human review.
   Script called: `scripts/tools/marketmind-produce-human-report.py`
   Input: agent log plus raw and verified outputs.
   Output: markdown report sections: run summary, source inventory, inputs used, validation results, flags, typed TODOs, decision recommendation.
   Where output goes: reports/generated/.
