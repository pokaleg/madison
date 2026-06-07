# Cybersecurity Breach And Advisory Dataset Pipeline

## Purpose

Normalizes local breach records, CISA advisories, and Kaggle cybersecurity dataset-catalog records into clean and rejected cybersecurity data outputs. The business question is: what signals from these specific sources are reliable enough for a human boss to use in cybersecurity dataset curation decisions?

## Source Inventory

| Source Node | Node Type | Source URL or Path | Human Check |
|---|---|---|---|
| Read local breach CSV source | `readWriteFile` | [TODO: DATA SOURCE] Replace machine-specific local path with repo-local path or confirmed fixture: `C:\Users\Hammad\.n8n-files\breaches_raw.csv` | Confirm local file exists in the Madison repo or replace machine-specific path. |
| Extract local breach CSV rows | `extractFromFile` | `[TODO: DATA SOURCE] Source not explicit in n8n node.` | Human must identify or replace this source before first real run. |
| Fetch CISA cybersecurity advisories | `rssFeedRead` | `https://www.cisa.gov/cybersecurity-advisories/all.xml` | Confirm source is allowed, current, and rate-safe before live fetch. |
| Fetch Kaggle cybersecurity dataset catalog | `httpRequest` | `https://www.kaggle.com/api/v1/datasets/list` | Confirm source is allowed, current, and rate-safe before live fetch. |

| Node Name | Node Type | Classification |
|---|---|---|
| When clicking 'Execute workflow' | `manualTrigger` | conductor |
| Read local breach CSV source | `readWriteFile` | ingest |
| Extract local breach CSV rows | `extractFromFile` | ingest |
| Normalize local breach records | `code` | gigo |
| Prepare normalized breach JSON | `convertToFile` | tool |
| Write normalized breach JSON handoff | `readWriteFile` | tool |
| Fetch CISA cybersecurity advisories | `rssFeedRead` | ingest |
| Normalize CISA advisory records | `code` | gigo |
| Prepare normalized CISA advisory JSON | `convertToFile` | tool |
| Write normalized CISA advisory JSON handoff | `readWriteFile` | tool |
| Fetch Kaggle cybersecurity dataset catalog | `httpRequest` | ingest |
| Normalize Kaggle cybersecurity catalog records | `code` | gigo |
| Prepare normalized cybersecurity catalog JSON | `convertToFile` | tool |
| Write normalized cybersecurity catalog JSON handoff | `readWriteFile` | tool |
| Merge | `merge` | conductor |
| Deduplicate merged cybersecurity records | `code` | gigo |
| Split clean and rejected cybersecurity records | `code` | gigo |
| If | `if` | conductor |
| Prepare clean cybersecurity JSON | `convertToFile` | tool |
| Write clean cybersecurity JSON handoff | `readWriteFile` | tool |
| Prepare rejected cybersecurity JSON | `convertToFile` | tool |
| Write rejected cybersecurity JSON handoff | `readWriteFile` | tool |
## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Original n8n workflow JSON | JSON | [TODO: DATA SOURCE] Restore or move original workflow JSON to a repo-local path. Last documented path: pantry/ranahammad_320831_41799387_Rana_Hammad_A3_Workflow.json | Yes |
| Read local breach CSV source | Source payload | [TODO: DATA SOURCE] Replace machine-specific local path with repo-local path or confirmed fixture: `C:\Users\Hammad\.n8n-files\breaches_raw.csv` | Yes |
| Extract local breach CSV rows | Source payload | `[TODO: DATA SOURCE] Source not explicit in n8n node.` | Yes |
| Fetch CISA cybersecurity advisories | Source payload | `https://www.cisa.gov/cybersecurity-advisories/all.xml` | Yes |
| Fetch Kaggle cybersecurity dataset catalog | Source payload | `https://www.kaggle.com/api/v1/datasets/list` | Yes |

## Phase Gates

1. Source gate: All required source paths are present or explicitly marked with a typed TODO. Test: `test -f "recipes/cybersecurity-breach-and-advisory-dataset-pipeline.md" && rg -n "\[TODO: DEFINE]" "recipes/cybersecurity-breach-and-advisory-dataset-pipeline.md" || true`. Human capacity: [TO].
2. Scope gate: The run declares `sample` mode or an approved live mode before ingest begins. Test: `python3 -m json.tool data/raw/cybersecurity-breach-and-advisory-dataset-pipeline/run-envelope.json`. Human capacity: [PF].
3. Data-shape gate: Every raw and verified JSON output parses before downstream scripts run. Test: `find data/raw/cybersecurity-breach-and-advisory-dataset-pipeline data/verified/cybersecurity-breach-and-advisory-dataset-pipeline -name "*.json" -print -exec python3 -m json.tool {} \;`. Human capacity: [PA].
4. Script-readiness gate: Every step script exists or is represented by a typed development TODO. Test: `test -f scripts/ingest/cybersecurity-breach-and-advisory-dataset-pipeline-ingest-inputs.py || rg --fixed-strings "[TODO: DEV]" "recipes/cybersecurity-breach-and-advisory-dataset-pipeline.md"`. Human capacity: [IJ].
5. Approval gate: Live network calls, external writes, credentials, production databases, emails, dashboards, publishing, or model calls with sensitive data require an approval record. Test: `test -f logs/gate-decisions/cybersecurity-breach-and-advisory-dataset-pipeline-approval.json || rg --fixed-strings "[TODO: APPROVE]" "recipes/cybersecurity-breach-and-advisory-dataset-pipeline.md"`. Human capacity: [EI].
6. Report gate: Agent log and human report are written with the required fields and sections. Test: `test -f logs/cybersecurity-breach-and-advisory-dataset-pipeline-[DATE].json && test -f reports/generated/cybersecurity-breach-and-advisory-dataset-pipeline-[DATE].md`. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI with Human gate.
   Script called: `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-verify-provenance.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `cybersecurity-breach-and-advisory-dataset-pipeline`.
   Output: workflow, source_paths, exists, parsed_ok, approval_state, checked_at.
   Where output goes: `logs/`
2. Step name: Ingest declared inputs. Labor: AI with Human gate.
   Script called: `scripts/ingest/cybersecurity-breach-and-advisory-dataset-pipeline-ingest-inputs.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `cybersecurity-breach-and-advisory-dataset-pipeline`.
   Output: records, source_name, source_type, fetched_at, sample_mode, rejects.
   Where output goes: `data/raw/cybersecurity-breach-and-advisory-dataset-pipeline/`
3. Step name: Validate data shape. Labor: AI with Human gate.
   Script called: `scripts/gigo/cybersecurity-breach-and-advisory-dataset-pipeline-validate-data-shape.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `cybersecurity-breach-and-advisory-dataset-pipeline`.
   Output: record_count, required_fields_present, missing_fields, parse_errors, schema_version.
   Where output goes: `data/verified/cybersecurity-breach-and-advisory-dataset-pipeline/`
4. Step name: Transform and quality check. Labor: AI with Human gate.
   Script called: `scripts/gigo/cybersecurity-breach-and-advisory-dataset-pipeline-transform-quality-check.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `cybersecurity-breach-and-advisory-dataset-pipeline`.
   Output: verified_records, record_count, duplicates, rejects, flags, quality_notes.
   Where output goes: `data/verified/cybersecurity-breach-and-advisory-dataset-pipeline/`
5. Step name: Run approved tools. Labor: AI with Human gate.
   Script called: `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-run-approved-tools.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `cybersecurity-breach-and-advisory-dataset-pipeline`.
   Output: tool_name, input_path, output_path, action_taken, approval_id, no_write_mode.
   Where output goes: `logs/`
6. Step name: Produce human report. Labor: AI with Human gate.
   Script called: `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-produce-human-report.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `cybersecurity-breach-and-advisory-dataset-pipeline`.
   Output: summary, sources_checked, gate_results, findings, typed_todos, next_decision.
   Where output goes: `reports/generated/`

## Output Contract

### Agent output
File: `logs/cybersecurity-breach-and-advisory-dataset-pipeline-[DATE].json`
Fields: workflow, run_id, mode, steps_completed, records_seen, rejects, duplicates, flags, stop_conditions, todo_items, source_files, gate_decisions, generated_at, raw_output_paths, verified_output_paths, report_path.

### Human report
File: `reports/generated/cybersecurity-breach-and-advisory-dataset-pipeline-[DATE].md`
Reader: domain lead or human boss responsible for accepting the `Cybersecurity Breach And Advisory Dataset Pipeline` run.
Decision enabled: approve the run for the next phase, request source/schema fixes, or block live execution.
Sections: run summary, purpose, source inventory, inputs used, phase-gate results, steps completed, records seen, rejects, duplicates, flags, typed TODOs, human approvals, verified findings, inferred findings, decision recommendation.

## Stop Conditions

- Stop if the recipe title or purpose does not match the original workflow intent.
- Stop if `pantry/ranahammad_320831_41799387_Rana_Hammad_A3_Workflow.json` is missing or cannot be parsed.
- Stop if a source URL/path is unknown, stale, private, machine-specific, credential-bearing, or not approved; add `[TODO: APPROVE] replace source` and halt live mode.
- Stop if the workflow does not define critical fields for validation; add `[TODO: DEFINE] define required fields` before production.
- Stop if GIGO outputs do not expose record counts, rejects, duplicates, or missing fields.
- Stop if a final claim is not traceable to source or verified records.
- Stop if generated reports would expose credentials, private tokens, private local paths, or unapproved personal data.
- Stop if any live model, database, email, dashboard, file export, or API write is requested without explicit human approval.

## Snickerdoodle

### Run Commands
Full dialogic run:
`snickerdoodle run cybersecurity-breach-and-advisory-dataset-pipeline --mode dialogic`

Sample mode (no live network calls, no writes):
`snickerdoodle run cybersecurity-breach-and-advisory-dataset-pipeline --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Verify provenance | `snickerdoodle run cybersecurity-breach-and-advisory-dataset-pipeline --step verify-provenance` | `--sample` `--no-write` |
| Ingest declared inputs | `snickerdoodle run cybersecurity-breach-and-advisory-dataset-pipeline --step ingest-inputs` | `--sample` |
| Validate data shape | `snickerdoodle run cybersecurity-breach-and-advisory-dataset-pipeline --step validate-data-shape` | `--sample` |
| Transform and quality check | `snickerdoodle run cybersecurity-breach-and-advisory-dataset-pipeline --step transform-quality-check` | `--sample` |
| Run approved tools | `snickerdoodle run cybersecurity-breach-and-advisory-dataset-pipeline --step run-approved-tools` | `--sample` `--no-write` |
| Produce human report | `snickerdoodle run cybersecurity-breach-and-advisory-dataset-pipeline --step produce-human-report` | `--sample` `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - Source gate | `snickerdoodle gate cybersecurity-breach-and-advisory-dataset-pipeline --gate 1 --decision approve --note "Sources checked"` |
| Gate 2 - Scope gate | `snickerdoodle gate cybersecurity-breach-and-advisory-dataset-pipeline --gate 2 --decision approve --note "Scope and mode approved"` |
| Gate 3 - Data-shape gate | `snickerdoodle gate cybersecurity-breach-and-advisory-dataset-pipeline --gate 3 --decision approve --note "Outputs parse"` |
| Gate 4 - Script-readiness gate | `snickerdoodle gate cybersecurity-breach-and-advisory-dataset-pipeline --gate 4 --decision approve --note "Scripts ready or TODO DEV accepted"` |
| Gate 5 - Approval gate | `snickerdoodle gate cybersecurity-breach-and-advisory-dataset-pipeline --gate 5 --decision approve --note "Live or sensitive actions approved"` |
| Gate 6 - Report gate | `snickerdoodle gate cybersecurity-breach-and-advisory-dataset-pipeline --gate 6 --decision approve --note "Report and log complete"` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Verify provenance | `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-verify-provenance.py` | tools |
| Ingest declared inputs | `scripts/ingest/cybersecurity-breach-and-advisory-dataset-pipeline-ingest-inputs.py` | ingest |
| Validate data shape | `scripts/gigo/cybersecurity-breach-and-advisory-dataset-pipeline-validate-data-shape.py` | gigo |
| Transform and quality check | `scripts/gigo/cybersecurity-breach-and-advisory-dataset-pipeline-transform-quality-check.py` | gigo |
| Run approved tools | `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-run-approved-tools.py` | tools |
| Produce human report | `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-produce-human-report.py` | tools |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/cybersecurity-breach-and-advisory-dataset-pipeline/` | JSON |
| Verified data | `data/verified/cybersecurity-breach-and-advisory-dataset-pipeline/` | JSON |
| Agent log | `logs/cybersecurity-breach-and-advisory-dataset-pipeline-[DATE].json` | JSON |
| Human report | `reports/generated/cybersecurity-breach-and-advisory-dataset-pipeline-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

## Provenance

| Source | Verification command | Notes |
|---|---|---|
| `pantry/ranahammad_320831_41799387_Rana_Hammad_A3_Workflow.json` | `test -f "pantry/ranahammad_320831_41799387_Rana_Hammad_A3_Workflow.json"` | Referenced source/evidence path from prior recipe text. |

## Existing Recipe Notes Preserved For Implementation

### Extracted Notes

Normalizes local breach records, CISA advisories, and Kaggle cybersecurity dataset-catalog records into clean and rejected cybersecurity data outputs. The business question is: what signals from these specific sources are reliable enough for a human boss to use in cybersecurity dataset curation decisions?

1. Source identity gate: Original workflow JSON exists and is the intended source. Test: `test -f "pantry/ranahammad_320831_41799387_Rana_Hammad_A3_Workflow.json"`; if this fails, close [TODO: DATA SOURCE] by restoring or moving the workflow JSON before live mode.
   Human capacity: [PF].
2. Input readiness gate: Every required input in this recipe exists or is marked with a typed TODO. Test: `rg -n "TODO:" recipes/cybersecurity-breach-and-advisory-dataset-pipeline.md`.
   Human capacity: [PA].
3. Sample run gate: Ingest and tool steps run without live side effects before live mode. Test: `snickerdoodle run cybersecurity-breach-and-advisory-dataset-pipeline --mode dialogic --sample`.
   Human capacity: [TO].
4. Data-shape gate: Raw and verified outputs parse as JSON where applicable. Test: `find data/raw/cybersecurity-breach-and-advisory-dataset-pipeline data/verified/cybersecurity-breach-and-advisory-dataset-pipeline -name "*.json" -print -exec python3 -m json.tool {} \;`.
   Human capacity: [IJ].
5. Report contract gate: Human report defines reader, decision enabled, and sections. Test: `rg -n "Reader:|Decision enabled:|Sections:" recipes/cybersecurity-breach-and-advisory-dataset-pipeline.md`.
   Human capacity: [EI].

1. Step name: Verify provenance and source intent. Labor: Human.
   Human action: Record approval, rejection, or requested changes with supervisory capacity label [TODO: DEFINE].
   Input: pantry/ranahammad_320831_41799387_Rana_Hammad_A3_Workflow.json.
   Output: provenance fields: workflow_path, exists, parsed_ok, title_matches_pipeline, source_inventory_checked.
   Where output goes: logs/gate-decisions/.
2. Step name: Read local breach CSV source. Labor: AI with Human gate.
   Script called: `scripts/ingest/cybersecurity-breach-and-advisory-dataset-pipeline-read-local-breach-csv-source.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
3. Step name: Extract local breach CSV rows. Labor: AI with Human gate.
   Script called: `scripts/ingest/cybersecurity-breach-and-advisory-dataset-pipeline-extract-local-breach-csv-rows.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
4. Step name: Normalize local breach records. Labor: AI with Human gate.
   Script called: `scripts/gigo/cybersecurity-breach-and-advisory-dataset-pipeline-normalize-local-breach-records.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
5. Step name: Prepare normalized breach JSON. Labor: AI with Human gate.
   Script called: `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-prepare-normalized-breach-json.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
6. Step name: Write normalized breach JSON handoff. Labor: AI with Human gate.
   Script called: `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-write-normalized-breach-json-handoff.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
7. Step name: Fetch CISA cybersecurity advisories. Labor: AI with Human gate.
   Script called: `scripts/ingest/cybersecurity-breach-and-advisory-dataset-pipeline-fetch-cisa-cybersecurity-advisories.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
8. Step name: Normalize CISA advisory records. Labor: AI with Human gate.
   Script called: `scripts/gigo/cybersecurity-breach-and-advisory-dataset-pipeline-normalize-cisa-advisory-records.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
9. Step name: Prepare normalized CISA advisory JSON. Labor: AI with Human gate.
   Script called: `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-prepare-normalized-cisa-advisory-json.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
10. Step name: Write normalized CISA advisory JSON handoff. Labor: AI with Human gate.
   Script called: `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-write-normalized-cisa-advisory-json-handoff.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
11. Step name: Fetch Kaggle cybersecurity dataset catalog. Labor: AI with Human gate.
   Script called: `scripts/ingest/cybersecurity-breach-and-advisory-dataset-pipeline-fetch-kaggle-cybersecurity-dataset-catalog.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
12. Step name: Normalize Kaggle cybersecurity catalog records. Labor: AI with Human gate.
   Script called: `scripts/gigo/cybersecurity-breach-and-advisory-dataset-pipeline-normalize-kaggle-cybersecurity-catalog-records.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
13. Step name: Prepare normalized cybersecurity catalog JSON. Labor: AI with Human gate.
   Script called: `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-prepare-normalized-cybersecurity-catalog-json.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
14. Step name: Write normalized cybersecurity catalog JSON handoff. Labor: AI with Human gate.
   Script called: `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-write-normalized-cybersecurity-catalog-json-handoff.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
15. Step name: Deduplicate merged cybersecurity records. Labor: AI with Human gate.
   Script called: `scripts/gigo/cybersecurity-breach-and-advisory-dataset-pipeline-deduplicate-merged-cybersecurity-records.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
16. Step name: Split clean and rejected cybersecurity records. Labor: AI with Human gate.
   Script called: `scripts/gigo/cybersecurity-breach-and-advisory-dataset-pipeline-split-clean-and-rejected-cybersecurity-records.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
17. Step name: Prepare clean cybersecurity JSON. Labor: AI with Human gate.
   Script called: `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-prepare-clean-cybersecurity-json.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
18. Step name: Write clean cybersecurity JSON handoff. Labor: AI with Human gate.
   Script called: `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-write-clean-cybersecurity-json-handoff.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
19. Step name: Prepare rejected cybersecurity JSON. Labor: AI with Human gate.
   Script called: `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-prepare-rejected-cybersecurity-json.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
20. Step name: Write rejected cybersecurity JSON handoff. Labor: AI with Human gate.
   Script called: `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-write-rejected-cybersecurity-json-handoff.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
21. Step name: Produce human report. Labor: AI with Human review.
   Script called: `scripts/tools/cybersecurity-breach-and-advisory-dataset-pipeline-produce-human-report.py`
   Input: agent log plus raw and verified outputs.
   Output: markdown report sections: run summary, source inventory, inputs used, validation results, flags, typed TODOs, decision recommendation.
   Where output goes: reports/generated/.
