# Clinical Adaptive Fashion Persona Pipeline

## Purpose

Combines CDC data, local healthcare CSV records, Hugging Face clinical notes, and breast-cancer research RSS to build quality-checked adaptive-fashion persona evidence. The business question is: what signals from these specific sources are reliable enough for a human boss to use in clinical persona synthesis decisions?

## Source Inventory

| Source Node | Node Type | Source URL or Path | Human Check |
|---|---|---|---|
| Fetch data.cdc.gov source | `httpRequest` | `https://data.cdc.gov/resource/hksd-2xuw.json?$limit=100` | Confirm source is allowed, current, and rate-safe before live fetch. |
| Fetch datasets-server.huggingface.co source | `httpRequest` | `https://datasets-server.huggingface.co/rows?dataset=AGBonnet%2Faugmented-clinical-notes&config=default&split=train&offset=0&limit=100` | Confirm source is allowed, current, and rate-safe before live fetch. |
| Fetch sciencedaily.com source | `httpRequest` | `https://www.sciencedaily.com/rss/health_medicine/breast_cancer.xml` | Confirm source is allowed, current, and rate-safe before live fetch. |
| Read/Write Files from Disk | `readWriteFile` | [TODO: DATA SOURCE] Replace machine-specific local path with repo-local path or confirmed fixture: `/Users/rakshakrishnamoorthy/.n8n-files/kaggle_healthcare.csv` | Confirm local file exists in the Madison repo or replace machine-specific path. |
| Extract from File | `extractFromFile` | `[TODO: DATA SOURCE] Source not explicit in n8n node.` | Human must identify or replace this source before first real run. |

| Node Name | Node Type | Classification |
|---|---|---|
| Node Name | Node Type | [TODO: DEFINE] Choose one of ingest, gigo, tool, conductor, report. |
| When clicking 'Execute workflow' | `manualTrigger` | conductor |
| Fetch data.cdc.gov source | `httpRequest` | ingest |
| Code: Parse CDC | `code` | gigo |
| Code: Parse Kaggle | `code` | gigo |
| Fetch datasets-server.huggingface.co source | `httpRequest` | ingest |
| Code: Parse HuggingFace | `code` | gigo |
| Fetch sciencedaily.com source | `httpRequest` | ingest |
| Code: Parse RSS | `code` | gigo |
| Code: Merge + Quality Check | `code` | gigo |
| Code: Summary Report | `code` | gigo |
| Read/Write Files from Disk | `readWriteFile` | ingest |
| Extract from File | `extractFromFile` | ingest |
| Merge | `merge` | conductor |
| Code: Generate HTML Report | `code` | gigo |
| Read/Write Files from Disk1 | `readWriteFile` | tool |
| Sticky Note | `stickyNote` | conductor |
## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Original n8n workflow JSON | JSON | [TODO: DATA SOURCE] Restore or move original workflow JSON to a repo-local path. Last documented path: pantry/krishnamoorthyraksha_333078_41797107_KrishnaMoorthy_Raksha_A3_Workflow-1.json | Yes |
| Fetch data.cdc.gov source | Source payload | `https://data.cdc.gov/resource/hksd-2xuw.json?$limit=100` | Yes |
| Fetch datasets-server.huggingface.co source | Source payload | `https://datasets-server.huggingface.co/rows?dataset=AGBonnet%2Faugmented-clinical-notes&config=default&split=train&offset=0&limit=100` | Yes |
| Fetch sciencedaily.com source | Source payload | `https://www.sciencedaily.com/rss/health_medicine/breast_cancer.xml` | Yes |
| Read/Write Files from Disk | Source payload | [TODO: DATA SOURCE] Replace machine-specific local path with repo-local path or confirmed fixture: `/Users/rakshakrishnamoorthy/.n8n-files/kaggle_healthcare.csv` | Yes |
| Extract from File | Source payload | `[TODO: DATA SOURCE] Source not explicit in n8n node.` | Yes |

## Phase Gates

1. Source gate: All required source paths are present or explicitly marked with a typed TODO. Test: `test -f "recipes/clinical-adaptive-fashion-persona-pipeline.md" && rg -n "\[TODO: DEFINE]" "recipes/clinical-adaptive-fashion-persona-pipeline.md" || true`. Human capacity: [TO].
2. Scope gate: The run declares `sample` mode or an approved live mode before ingest begins. Test: `python3 -m json.tool data/raw/clinical-adaptive-fashion-persona-pipeline/run-envelope.json`. Human capacity: [PF].
3. Data-shape gate: Every raw and verified JSON output parses before downstream scripts run. Test: `find data/raw/clinical-adaptive-fashion-persona-pipeline data/verified/clinical-adaptive-fashion-persona-pipeline -name "*.json" -print -exec python3 -m json.tool {} \;`. Human capacity: [PA].
4. Script-readiness gate: Every step script exists or is represented by a typed development TODO. Test: `test -f scripts/ingest/clinical-adaptive-fashion-persona-pipeline-ingest-inputs.py || rg --fixed-strings "[TODO: DEV]" "recipes/clinical-adaptive-fashion-persona-pipeline.md"`. Human capacity: [IJ].
5. Approval gate: Live network calls, external writes, credentials, production databases, emails, dashboards, publishing, or model calls with sensitive data require an approval record. Test: `test -f logs/gate-decisions/clinical-adaptive-fashion-persona-pipeline-approval.json || rg --fixed-strings "[TODO: APPROVE]" "recipes/clinical-adaptive-fashion-persona-pipeline.md"`. Human capacity: [EI].
6. Report gate: Agent log and human report are written with the required fields and sections. Test: `test -f logs/clinical-adaptive-fashion-persona-pipeline-[DATE].json && test -f reports/generated/clinical-adaptive-fashion-persona-pipeline-[DATE].md`. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI with Human gate.
   Script called: `scripts/tools/clinical-adaptive-fashion-persona-pipeline-verify-provenance.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `clinical-adaptive-fashion-persona-pipeline`.
   Output: workflow, source_paths, exists, parsed_ok, approval_state, checked_at.
   Where output goes: `logs/`
2. Step name: Ingest declared inputs. Labor: AI with Human gate.
   Script called: `scripts/ingest/clinical-adaptive-fashion-persona-pipeline-ingest-inputs.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `clinical-adaptive-fashion-persona-pipeline`.
   Output: records, source_name, source_type, fetched_at, sample_mode, rejects.
   Where output goes: `data/raw/clinical-adaptive-fashion-persona-pipeline/`
3. Step name: Validate data shape. Labor: AI with Human gate.
   Script called: `scripts/gigo/clinical-adaptive-fashion-persona-pipeline-validate-data-shape.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `clinical-adaptive-fashion-persona-pipeline`.
   Output: record_count, required_fields_present, missing_fields, parse_errors, schema_version.
   Where output goes: `data/verified/clinical-adaptive-fashion-persona-pipeline/`
4. Step name: Transform and quality check. Labor: AI with Human gate.
   Script called: `scripts/gigo/clinical-adaptive-fashion-persona-pipeline-transform-quality-check.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `clinical-adaptive-fashion-persona-pipeline`.
   Output: verified_records, record_count, duplicates, rejects, flags, quality_notes.
   Where output goes: `data/verified/clinical-adaptive-fashion-persona-pipeline/`
5. Step name: Run approved tools. Labor: AI with Human gate.
   Script called: `scripts/tools/clinical-adaptive-fashion-persona-pipeline-run-approved-tools.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `clinical-adaptive-fashion-persona-pipeline`.
   Output: tool_name, input_path, output_path, action_taken, approval_id, no_write_mode.
   Where output goes: `logs/`
6. Step name: Produce human report. Labor: AI with Human gate.
   Script called: `scripts/tools/clinical-adaptive-fashion-persona-pipeline-produce-human-report.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `clinical-adaptive-fashion-persona-pipeline`.
   Output: summary, sources_checked, gate_results, findings, typed_todos, next_decision.
   Where output goes: `reports/generated/`

## Output Contract

### Agent output
File: `logs/clinical-adaptive-fashion-persona-pipeline-[DATE].json`
Fields: workflow, run_id, mode, steps_completed, records_seen, rejects, duplicates, flags, stop_conditions, todo_items, source_files, gate_decisions, generated_at, raw_output_paths, verified_output_paths, report_path.

### Human report
File: `reports/generated/clinical-adaptive-fashion-persona-pipeline-[DATE].md`
Reader: domain lead or human boss responsible for accepting the `Clinical Adaptive Fashion Persona Pipeline` run.
Decision enabled: approve the run for the next phase, request source/schema fixes, or block live execution.
Sections: run summary, purpose, source inventory, inputs used, phase-gate results, steps completed, records seen, rejects, duplicates, flags, typed TODOs, human approvals, verified findings, inferred findings, decision recommendation.

## Stop Conditions

- Stop if the recipe title or purpose does not match the original workflow intent.
- Stop if `pantry/krishnamoorthyraksha_333078_41797107_KrishnaMoorthy_Raksha_A3_Workflow-1.json` is missing or cannot be parsed.
- Stop if a source URL/path is unknown, stale, private, machine-specific, credential-bearing, or not approved; add `[TODO: APPROVE] replace source` and halt live mode.
- Stop if the workflow does not define critical fields for validation; add `[TODO: DEFINE] define required fields` before production.
- Stop if GIGO outputs do not expose record counts, rejects, duplicates, or missing fields.
- Stop if a final claim is not traceable to source or verified records.
- Stop if generated reports would expose credentials, private tokens, private local paths, or unapproved personal data.
- Stop if any live model, database, email, dashboard, file export, or API write is requested without explicit human approval.

## Snickerdoodle

### Run Commands
Full dialogic run:
`snickerdoodle run clinical-adaptive-fashion-persona-pipeline --mode dialogic`

Sample mode (no live network calls, no writes):
`snickerdoodle run clinical-adaptive-fashion-persona-pipeline --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Verify provenance | `snickerdoodle run clinical-adaptive-fashion-persona-pipeline --step verify-provenance` | `--sample` `--no-write` |
| Ingest declared inputs | `snickerdoodle run clinical-adaptive-fashion-persona-pipeline --step ingest-inputs` | `--sample` |
| Validate data shape | `snickerdoodle run clinical-adaptive-fashion-persona-pipeline --step validate-data-shape` | `--sample` |
| Transform and quality check | `snickerdoodle run clinical-adaptive-fashion-persona-pipeline --step transform-quality-check` | `--sample` |
| Run approved tools | `snickerdoodle run clinical-adaptive-fashion-persona-pipeline --step run-approved-tools` | `--sample` `--no-write` |
| Produce human report | `snickerdoodle run clinical-adaptive-fashion-persona-pipeline --step produce-human-report` | `--sample` `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - Source gate | `snickerdoodle gate clinical-adaptive-fashion-persona-pipeline --gate 1 --decision approve --note "Sources checked"` |
| Gate 2 - Scope gate | `snickerdoodle gate clinical-adaptive-fashion-persona-pipeline --gate 2 --decision approve --note "Scope and mode approved"` |
| Gate 3 - Data-shape gate | `snickerdoodle gate clinical-adaptive-fashion-persona-pipeline --gate 3 --decision approve --note "Outputs parse"` |
| Gate 4 - Script-readiness gate | `snickerdoodle gate clinical-adaptive-fashion-persona-pipeline --gate 4 --decision approve --note "Scripts ready or TODO DEV accepted"` |
| Gate 5 - Approval gate | `snickerdoodle gate clinical-adaptive-fashion-persona-pipeline --gate 5 --decision approve --note "Live or sensitive actions approved"` |
| Gate 6 - Report gate | `snickerdoodle gate clinical-adaptive-fashion-persona-pipeline --gate 6 --decision approve --note "Report and log complete"` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Verify provenance | `scripts/tools/clinical-adaptive-fashion-persona-pipeline-verify-provenance.py` | tools |
| Ingest declared inputs | `scripts/ingest/clinical-adaptive-fashion-persona-pipeline-ingest-inputs.py` | ingest |
| Validate data shape | `scripts/gigo/clinical-adaptive-fashion-persona-pipeline-validate-data-shape.py` | gigo |
| Transform and quality check | `scripts/gigo/clinical-adaptive-fashion-persona-pipeline-transform-quality-check.py` | gigo |
| Run approved tools | `scripts/tools/clinical-adaptive-fashion-persona-pipeline-run-approved-tools.py` | tools |
| Produce human report | `scripts/tools/clinical-adaptive-fashion-persona-pipeline-produce-human-report.py` | tools |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/clinical-adaptive-fashion-persona-pipeline/` | JSON |
| Verified data | `data/verified/clinical-adaptive-fashion-persona-pipeline/` | JSON |
| Agent log | `logs/clinical-adaptive-fashion-persona-pipeline-[DATE].json` | JSON |
| Human report | `reports/generated/clinical-adaptive-fashion-persona-pipeline-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

## Provenance

| Source | Verification command | Notes |
|---|---|---|
| `pantry/krishnamoorthyraksha_333078_41797107_KrishnaMoorthy_Raksha_A3_Workflow-1.json` | `test -f "pantry/krishnamoorthyraksha_333078_41797107_KrishnaMoorthy_Raksha_A3_Workflow-1.json"` | Referenced source/evidence path from prior recipe text. |

## Existing Recipe Notes Preserved For Implementation

### Extracted Notes

Combines CDC data, local healthcare CSV records, Hugging Face clinical notes, and breast-cancer research RSS to build quality-checked adaptive-fashion persona evidence. The business question is: what signals from these specific sources are reliable enough for a human boss to use in clinical persona synthesis decisions?

1. Source identity gate: Original workflow JSON exists and is the intended source. Test: `test -f "pantry/krishnamoorthyraksha_333078_41797107_KrishnaMoorthy_Raksha_A3_Workflow-1.json"`; if this fails, close [TODO: DATA SOURCE] by restoring or moving the workflow JSON before live mode.
   Human capacity: [PF].
2. Input readiness gate: Every required input in this recipe exists or is marked with a typed TODO. Test: `rg -n "TODO:" recipes/clinical-adaptive-fashion-persona-pipeline.md`.
   Human capacity: [PA].
3. Sample run gate: Ingest and tool steps run without live side effects before live mode. Test: `snickerdoodle run clinical-adaptive-fashion-persona-pipeline --mode dialogic --sample`.
   Human capacity: [TO].
4. Data-shape gate: Raw and verified outputs parse as JSON where applicable. Test: `find data/raw/clinical-adaptive-fashion-persona-pipeline data/verified/clinical-adaptive-fashion-persona-pipeline -name "*.json" -print -exec python3 -m json.tool {} \;`.
   Human capacity: [IJ].
5. Report contract gate: Human report defines reader, decision enabled, and sections. Test: `rg -n "Reader:|Decision enabled:|Sections:" recipes/clinical-adaptive-fashion-persona-pipeline.md`.
   Human capacity: [EI].

1. Step name: Verify provenance and source intent. Labor: Human.
   Human action: Record approval, rejection, or requested changes with supervisory capacity label [TODO: DEFINE].
   Input: pantry/krishnamoorthyraksha_333078_41797107_KrishnaMoorthy_Raksha_A3_Workflow-1.json.
   Output: provenance fields: workflow_path, exists, parsed_ok, title_matches_pipeline, source_inventory_checked.
   Where output goes: logs/gate-decisions/.
2. Step name: Fetch data.cdc.gov source. Labor: AI with Human gate.
   Script called: `scripts/ingest/clinical-adaptive-fashion-persona-pipeline-fetch-data-cdc-gov-source.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
3. Step name: Code: Parse CDC. Labor: AI with Human gate.
   Script called: `scripts/gigo/clinical-adaptive-fashion-persona-pipeline-code-parse-cdc.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
4. Step name: Code: Parse Kaggle. Labor: AI with Human gate.
   Script called: `scripts/gigo/clinical-adaptive-fashion-persona-pipeline-code-parse-kaggle.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
5. Step name: Fetch datasets-server.huggingface.co source. Labor: AI with Human gate.
   Script called: `scripts/ingest/clinical-adaptive-fashion-persona-pipeline-fetch-datasets-server-huggingface-co-source.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
6. Step name: Code: Parse HuggingFace. Labor: AI with Human gate.
   Script called: `scripts/gigo/clinical-adaptive-fashion-persona-pipeline-code-parse-huggingface.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
7. Step name: Fetch sciencedaily.com source. Labor: AI with Human gate.
   Script called: `scripts/ingest/clinical-adaptive-fashion-persona-pipeline-fetch-sciencedaily-com-source.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
8. Step name: Code: Parse RSS. Labor: AI with Human gate.
   Script called: `scripts/gigo/clinical-adaptive-fashion-persona-pipeline-code-parse-rss.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
9. Step name: Code: Merge + Quality Check. Labor: AI with Human gate.
   Script called: `scripts/gigo/clinical-adaptive-fashion-persona-pipeline-code-merge-quality-check.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
10. Step name: Code: Summary Report. Labor: AI with Human gate.
   Script called: `scripts/gigo/clinical-adaptive-fashion-persona-pipeline-code-summary-report.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
11. Step name: Read/Write Files from Disk. Labor: AI with Human gate.
   Script called: `scripts/ingest/clinical-adaptive-fashion-persona-pipeline-read-write-files-from-disk.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
12. Step name: Extract from File. Labor: AI with Human gate.
   Script called: `scripts/ingest/clinical-adaptive-fashion-persona-pipeline-extract-from-file.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
13. Step name: Code: Generate HTML Report. Labor: AI with Human gate.
   Script called: `scripts/gigo/clinical-adaptive-fashion-persona-pipeline-code-generate-html-report.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
14. Step name: Read/Write Files from Disk1. Labor: AI with Human gate.
   Script called: `scripts/tools/clinical-adaptive-fashion-persona-pipeline-read-write-files-from-disk1.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
15. Step name: Produce human report. Labor: AI with Human review.
   Script called: `scripts/tools/clinical-adaptive-fashion-persona-pipeline-produce-human-report.py`
   Input: agent log plus raw and verified outputs.
   Output: markdown report sections: run summary, source inventory, inputs used, validation results, flags, typed TODOs, decision recommendation.
   Where output goes: reports/generated/.
