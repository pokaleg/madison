# Cloud Platform Release And Jobs Monitor

## Purpose

Combines AWS blog RSS, Google Cloud release notes, and a public cloud-jobs CSV to build a cleaned cloud-platform signal dataset. The business question is: what signals from these specific sources are reliable enough for a human boss to use in cloud market intelligence decisions?

## Source Inventory

| Source Node | Node Type | Source URL or Path | Human Check |
|---|---|---|---|
| Source 1: AWS Blog RSS | `rssFeedRead` | `https://aws.amazon.com/blogs/aws/feed/` | Confirm source is allowed, current, and rate-safe before live fetch. |
| Source 2: Google Cloud RSS | `rssFeedRead` | `https://cloud.google.com/feeds/gcp-release-notes.xml` | Confirm source is allowed, current, and rate-safe before live fetch. |
| Source 3: Cloud Jobs CSV (HTTP) | `httpRequest` | `https://raw.githubusercontent.com/cloudcertdata/public-datasets/main/cloud_jobs_sample.csv` | Confirm source is allowed, current, and rate-safe before live fetch. |

| Node Name | Node Type | Classification |
|---|---|---|
| Manual Trigger | `manualTrigger` | conductor |
| Source 1: AWS Blog RSS | `rssFeedRead` | ingest |
| Source 2: Google Cloud RSS | `rssFeedRead` | ingest |
| Source 3: Cloud Jobs CSV (HTTP) | `httpRequest` | ingest |
| Merge All Sources | `merge` | conductor |
| Clean & Standardize | `code` | gigo |
| Quality Check | `code` | gigo |
| Save to CSV | `spreadsheetFile` | tool |
| Write File to Disk | `writeBinaryFile` | tool |
## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Original n8n workflow JSON | JSON | [TODO: DATA SOURCE] Restore or move original workflow JSON to a repo-local path. Last documented path: pantry/manyaratanaka_312461_41801533_Tanaka_A3_Workflow.json | Yes |
| Source 1: AWS Blog RSS | Source payload | `https://aws.amazon.com/blogs/aws/feed/` | Yes |
| Source 2: Google Cloud RSS | Source payload | `https://cloud.google.com/feeds/gcp-release-notes.xml` | Yes |
| Source 3: Cloud Jobs CSV (HTTP) | Source payload | `https://raw.githubusercontent.com/cloudcertdata/public-datasets/main/cloud_jobs_sample.csv` | Yes |

## Phase Gates

1. Source gate: All required source paths are present or explicitly marked with a typed TODO. Test: `test -f "recipes/cloud-platform-release-and-jobs-monitor.md" && rg -n "\[TODO: DEFINE]" "recipes/cloud-platform-release-and-jobs-monitor.md" || true`. Human capacity: [TO].
2. Scope gate: The run declares `sample` mode or an approved live mode before ingest begins. Test: `python3 -m json.tool data/raw/cloud-platform-release-and-jobs-monitor/run-envelope.json`. Human capacity: [PF].
3. Data-shape gate: Every raw and verified JSON output parses before downstream scripts run. Test: `find data/raw/cloud-platform-release-and-jobs-monitor data/verified/cloud-platform-release-and-jobs-monitor -name "*.json" -print -exec python3 -m json.tool {} \;`. Human capacity: [PA].
4. Script-readiness gate: Every step script exists or is represented by a typed development TODO. Test: `test -f scripts/ingest/cloud-platform-release-and-jobs-monitor-ingest-inputs.py || rg --fixed-strings "[TODO: DEV]" "recipes/cloud-platform-release-and-jobs-monitor.md"`. Human capacity: [IJ].
5. Approval gate: Live network calls, external writes, credentials, production databases, emails, dashboards, publishing, or model calls with sensitive data require an approval record. Test: `test -f logs/gate-decisions/cloud-platform-release-and-jobs-monitor-approval.json || rg --fixed-strings "[TODO: APPROVE]" "recipes/cloud-platform-release-and-jobs-monitor.md"`. Human capacity: [EI].
6. Report gate: Agent log and human report are written with the required fields and sections. Test: `test -f logs/cloud-platform-release-and-jobs-monitor-[DATE].json && test -f reports/generated/cloud-platform-release-and-jobs-monitor-[DATE].md`. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI with Human gate.
   Script called: `scripts/tools/cloud-platform-release-and-jobs-monitor-verify-provenance.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `cloud-platform-release-and-jobs-monitor`.
   Output: workflow, source_paths, exists, parsed_ok, approval_state, checked_at.
   Where output goes: `logs/`
2. Step name: Ingest declared inputs. Labor: AI with Human gate.
   Script called: `scripts/ingest/cloud-platform-release-and-jobs-monitor-ingest-inputs.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `cloud-platform-release-and-jobs-monitor`.
   Output: records, source_name, source_type, fetched_at, sample_mode, rejects.
   Where output goes: `data/raw/cloud-platform-release-and-jobs-monitor/`
3. Step name: Validate data shape. Labor: AI with Human gate.
   Script called: `scripts/gigo/cloud-platform-release-and-jobs-monitor-validate-data-shape.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `cloud-platform-release-and-jobs-monitor`.
   Output: record_count, required_fields_present, missing_fields, parse_errors, schema_version.
   Where output goes: `data/verified/cloud-platform-release-and-jobs-monitor/`
4. Step name: Transform and quality check. Labor: AI with Human gate.
   Script called: `scripts/gigo/cloud-platform-release-and-jobs-monitor-transform-quality-check.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `cloud-platform-release-and-jobs-monitor`.
   Output: verified_records, record_count, duplicates, rejects, flags, quality_notes.
   Where output goes: `data/verified/cloud-platform-release-and-jobs-monitor/`
5. Step name: Run approved tools. Labor: AI with Human gate.
   Script called: `scripts/tools/cloud-platform-release-and-jobs-monitor-run-approved-tools.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `cloud-platform-release-and-jobs-monitor`.
   Output: tool_name, input_path, output_path, action_taken, approval_id, no_write_mode.
   Where output goes: `logs/`
6. Step name: Produce human report. Labor: AI with Human gate.
   Script called: `scripts/tools/cloud-platform-release-and-jobs-monitor-produce-human-report.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `cloud-platform-release-and-jobs-monitor`.
   Output: summary, sources_checked, gate_results, findings, typed_todos, next_decision.
   Where output goes: `reports/generated/`

## Output Contract

### Agent output
File: `logs/cloud-platform-release-and-jobs-monitor-[DATE].json`
Fields: workflow, run_id, mode, steps_completed, records_seen, rejects, duplicates, flags, stop_conditions, todo_items, source_files, gate_decisions, generated_at, raw_output_paths, verified_output_paths, report_path.

### Human report
File: `reports/generated/cloud-platform-release-and-jobs-monitor-[DATE].md`
Reader: domain lead or human boss responsible for accepting the `Cloud Platform Release And Jobs Monitor` run.
Decision enabled: approve the run for the next phase, request source/schema fixes, or block live execution.
Sections: run summary, purpose, source inventory, inputs used, phase-gate results, steps completed, records seen, rejects, duplicates, flags, typed TODOs, human approvals, verified findings, inferred findings, decision recommendation.

## Stop Conditions

- Stop if the recipe title or purpose does not match the original workflow intent.
- Stop if `pantry/manyaratanaka_312461_41801533_Tanaka_A3_Workflow.json` is missing or cannot be parsed.
- Stop if a source URL/path is unknown, stale, private, machine-specific, credential-bearing, or not approved; add `[TODO: APPROVE] replace source` and halt live mode.
- Stop if the workflow does not define critical fields for validation; add `[TODO: DEFINE] define required fields` before production.
- Stop if GIGO outputs do not expose record counts, rejects, duplicates, or missing fields.
- Stop if a final claim is not traceable to source or verified records.
- Stop if generated reports would expose credentials, private tokens, private local paths, or unapproved personal data.
- Stop if any live model, database, email, dashboard, file export, or API write is requested without explicit human approval.

## Snickerdoodle

### Run Commands
Full dialogic run:
`snickerdoodle run cloud-platform-release-and-jobs-monitor --mode dialogic`

Sample mode (no live network calls, no writes):
`snickerdoodle run cloud-platform-release-and-jobs-monitor --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Verify provenance | `snickerdoodle run cloud-platform-release-and-jobs-monitor --step verify-provenance` | `--sample` `--no-write` |
| Ingest declared inputs | `snickerdoodle run cloud-platform-release-and-jobs-monitor --step ingest-inputs` | `--sample` |
| Validate data shape | `snickerdoodle run cloud-platform-release-and-jobs-monitor --step validate-data-shape` | `--sample` |
| Transform and quality check | `snickerdoodle run cloud-platform-release-and-jobs-monitor --step transform-quality-check` | `--sample` |
| Run approved tools | `snickerdoodle run cloud-platform-release-and-jobs-monitor --step run-approved-tools` | `--sample` `--no-write` |
| Produce human report | `snickerdoodle run cloud-platform-release-and-jobs-monitor --step produce-human-report` | `--sample` `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - Source gate | `snickerdoodle gate cloud-platform-release-and-jobs-monitor --gate 1 --decision approve --note "Sources checked"` |
| Gate 2 - Scope gate | `snickerdoodle gate cloud-platform-release-and-jobs-monitor --gate 2 --decision approve --note "Scope and mode approved"` |
| Gate 3 - Data-shape gate | `snickerdoodle gate cloud-platform-release-and-jobs-monitor --gate 3 --decision approve --note "Outputs parse"` |
| Gate 4 - Script-readiness gate | `snickerdoodle gate cloud-platform-release-and-jobs-monitor --gate 4 --decision approve --note "Scripts ready or TODO DEV accepted"` |
| Gate 5 - Approval gate | `snickerdoodle gate cloud-platform-release-and-jobs-monitor --gate 5 --decision approve --note "Live or sensitive actions approved"` |
| Gate 6 - Report gate | `snickerdoodle gate cloud-platform-release-and-jobs-monitor --gate 6 --decision approve --note "Report and log complete"` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Verify provenance | `scripts/tools/cloud-platform-release-and-jobs-monitor-verify-provenance.py` | tools |
| Ingest declared inputs | `scripts/ingest/cloud-platform-release-and-jobs-monitor-ingest-inputs.py` | ingest |
| Validate data shape | `scripts/gigo/cloud-platform-release-and-jobs-monitor-validate-data-shape.py` | gigo |
| Transform and quality check | `scripts/gigo/cloud-platform-release-and-jobs-monitor-transform-quality-check.py` | gigo |
| Run approved tools | `scripts/tools/cloud-platform-release-and-jobs-monitor-run-approved-tools.py` | tools |
| Produce human report | `scripts/tools/cloud-platform-release-and-jobs-monitor-produce-human-report.py` | tools |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/cloud-platform-release-and-jobs-monitor/` | JSON |
| Verified data | `data/verified/cloud-platform-release-and-jobs-monitor/` | JSON |
| Agent log | `logs/cloud-platform-release-and-jobs-monitor-[DATE].json` | JSON |
| Human report | `reports/generated/cloud-platform-release-and-jobs-monitor-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

## Provenance

| Source | Verification command | Notes |
|---|---|---|
| `pantry/manyaratanaka_312461_41801533_Tanaka_A3_Workflow.json` | `test -f "pantry/manyaratanaka_312461_41801533_Tanaka_A3_Workflow.json"` | Referenced source/evidence path from prior recipe text. |

## Existing Recipe Notes Preserved For Implementation

### Extracted Notes

Combines AWS blog RSS, Google Cloud release notes, and a public cloud-jobs CSV to build a cleaned cloud-platform signal dataset. The business question is: what signals from these specific sources are reliable enough for a human boss to use in cloud market intelligence decisions?

1. Source identity gate: Original workflow JSON exists and is the intended source. Test: `test -f "pantry/manyaratanaka_312461_41801533_Tanaka_A3_Workflow.json"`; if this fails, close [TODO: DATA SOURCE] by restoring or moving the workflow JSON before live mode.
   Human capacity: [PF].
2. Input readiness gate: Every required input in this recipe exists or is marked with a typed TODO. Test: `rg -n "TODO:" recipes/cloud-platform-release-and-jobs-monitor.md`.
   Human capacity: [PA].
3. Sample run gate: Ingest and tool steps run without live side effects before live mode. Test: `snickerdoodle run cloud-platform-release-and-jobs-monitor --mode dialogic --sample`.
   Human capacity: [TO].
4. Data-shape gate: Raw and verified outputs parse as JSON where applicable. Test: `find data/raw/cloud-platform-release-and-jobs-monitor data/verified/cloud-platform-release-and-jobs-monitor -name "*.json" -print -exec python3 -m json.tool {} \;`.
   Human capacity: [IJ].
5. Report contract gate: Human report defines reader, decision enabled, and sections. Test: `rg -n "Reader:|Decision enabled:|Sections:" recipes/cloud-platform-release-and-jobs-monitor.md`.
   Human capacity: [EI].

1. Step name: Verify provenance and source intent. Labor: Human.
   Human action: Record approval, rejection, or requested changes with supervisory capacity label [TODO: DEFINE].
   Input: pantry/manyaratanaka_312461_41801533_Tanaka_A3_Workflow.json.
   Output: provenance fields: workflow_path, exists, parsed_ok, title_matches_pipeline, source_inventory_checked.
   Where output goes: logs/gate-decisions/.
2. Step name: Source 1: AWS Blog RSS. Labor: AI with Human gate.
   Script called: `scripts/ingest/cloud-platform-release-and-jobs-monitor-source-1-aws-blog-rss.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
3. Step name: Source 2: Google Cloud RSS. Labor: AI with Human gate.
   Script called: `scripts/ingest/cloud-platform-release-and-jobs-monitor-source-2-google-cloud-rss.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
4. Step name: Source 3: Cloud Jobs CSV (HTTP). Labor: AI with Human gate.
   Script called: `scripts/ingest/cloud-platform-release-and-jobs-monitor-source-3-cloud-jobs-csv-http.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
5. Step name: Clean & Standardize. Labor: AI with Human gate.
   Script called: `scripts/gigo/cloud-platform-release-and-jobs-monitor-clean-and-standardize.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
6. Step name: Quality Check. Labor: AI with Human gate.
   Script called: `scripts/gigo/cloud-platform-release-and-jobs-monitor-quality-check.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
7. Step name: Save to CSV. Labor: AI with Human gate.
   Script called: `scripts/tools/cloud-platform-release-and-jobs-monitor-save-to-csv.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
8. Step name: Write File to Disk. Labor: AI with Human gate.
   Script called: `scripts/tools/cloud-platform-release-and-jobs-monitor-write-file-to-disk.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
9. Step name: Produce human report. Labor: AI with Human review.
   Script called: `scripts/tools/cloud-platform-release-and-jobs-monitor-produce-human-report.py`
   Input: agent log plus raw and verified outputs.
   Output: markdown report sections: run summary, source inventory, inputs used, validation results, flags, typed TODOs, decision recommendation.
   Where output goes: reports/generated/.
