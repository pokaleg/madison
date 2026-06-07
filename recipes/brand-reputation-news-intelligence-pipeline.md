# Brand Reputation News Intelligence Pipeline

## Purpose

Combines TechCrunch, Ars Technica, The Verge, Google News brand queries, NewsAPI, and Hugging Face text rows into a deduplicated brand-reputation intelligence dataset. The business question is: what signals from these specific sources are reliable enough for a human boss to use in brand reputation intelligence decisions?

## Source Inventory

| Source Node | Node Type | Source URL or Path | Human Check |
|---|---|---|---|
| RSS - TechCrunch | `rssFeedRead` | `https://techcrunch.com/feed/` | Confirm source is allowed, current, and rate-safe before live fetch. |
| RSS - Ars Technica | `rssFeedRead` | `https://feeds.arstechnica.com/arstechnica/index` | Confirm source is allowed, current, and rate-safe before live fetch. |
| RSS - The Verge | `rssFeedRead` | `https://www.theverge.com/rss/index.xml` | Confirm source is allowed, current, and rate-safe before live fetch. |
| RSS - Google News (Brand) | `rssFeedRead` | `https://news.google.com/rss/search?q=brand+reputation+OR+brand+monitoring+OR+brand+voice+AI&hl=en-US&gl=US&ceid=US:en` | Confirm source is allowed, current, and rate-safe before live fetch. |
| Fetch NewsAPI brand-reputation articles | `httpRequest` | `https://newsapi.org/v2/everything` | Confirm source is allowed, current, and rate-safe before live fetch. |
| Fetch Hugging Face text dataset rows | `httpRequest` | `https://datasets-server.huggingface.co/rows?dataset=SetFit%2F20_newsgroups&config=default&split=train&offset=0&length=80` | Confirm source is allowed, current, and rate-safe before live fetch. |

| Node Name | Node Type | Classification |
|---|---|---|
| Run Workflow | `manualTrigger` | conductor |
| RSS - TechCrunch | `rssFeedRead` | ingest |
| RSS - Ars Technica | `rssFeedRead` | ingest |
| RSS - The Verge | `rssFeedRead` | ingest |
| RSS - Google News (Brand) | `rssFeedRead` | ingest |
| Fetch NewsAPI brand-reputation articles | `httpRequest` | ingest |
| Fetch Hugging Face text dataset rows | `httpRequest` | ingest |
| Norm TechCrunch | `code` | tool |
| Norm Ars Technica | `code` | tool |
| Norm The Verge | `code` | tool |
| Norm Google News | `code` | tool |
| Norm NewsAPI | `code` | tool |
| Norm HuggingFace | `code` | gigo |
| Merge TC+Ars | `merge` | conductor |
| Merge +Verge | `merge` | conductor |
| Merge +GNews | `merge` | conductor |
| Merge +NewsAPI | `merge` | conductor |
| Merge +HF | `merge` | conductor |
| Deduplicate & Validate | `code` | gigo |
| Prepare brand-reputation CSV export | `convertToFile` | tool |
| Write brand-reputation CSV handoff | `readWriteFile` | tool |
## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Original n8n workflow JSON | JSON | [TODO: DATA SOURCE] Restore or move original workflow JSON to a repo-local path. Last documented path: pantry/singhvaibhav_351998_41799855_Singh_Vaibhav_A3_workflow.json | Yes |
| RSS - TechCrunch | Source payload | `https://techcrunch.com/feed/` | Yes |
| RSS - Ars Technica | Source payload | `https://feeds.arstechnica.com/arstechnica/index` | Yes |
| RSS - The Verge | Source payload | `https://www.theverge.com/rss/index.xml` | Yes |
| RSS - Google News (Brand) | Source payload | `https://news.google.com/rss/search?q=brand+reputation+OR+brand+monitoring+OR+brand+voice+AI&hl=en-US&gl=US&ceid=US:en` | Yes |
| Fetch NewsAPI brand-reputation articles | Source payload | `https://newsapi.org/v2/everything` | Yes |
| Fetch Hugging Face text dataset rows | Source payload | `https://datasets-server.huggingface.co/rows?dataset=SetFit%2F20_newsgroups&config=default&split=train&offset=0&length=80` | Yes |

## Phase Gates

1. Source gate: All required source paths are present or explicitly marked with a typed TODO. Test: `test -f "recipes/brand-reputation-news-intelligence-pipeline.md" && rg -n "\[TODO: DEFINE]" "recipes/brand-reputation-news-intelligence-pipeline.md" || true`. Human capacity: [TO].
2. Scope gate: The run declares `sample` mode or an approved live mode before ingest begins. Test: `python3 -m json.tool data/raw/brand-reputation-news-intelligence-pipeline/run-envelope.json`. Human capacity: [PF].
3. Data-shape gate: Every raw and verified JSON output parses before downstream scripts run. Test: `find data/raw/brand-reputation-news-intelligence-pipeline data/verified/brand-reputation-news-intelligence-pipeline -name "*.json" -print -exec python3 -m json.tool {} \;`. Human capacity: [PA].
4. Script-readiness gate: Every step script exists or is represented by a typed development TODO. Test: `test -f scripts/ingest/brand-reputation-news-intelligence-pipeline-ingest-inputs.py || rg --fixed-strings "[TODO: DEV]" "recipes/brand-reputation-news-intelligence-pipeline.md"`. Human capacity: [IJ].
5. Approval gate: Live network calls, external writes, credentials, production databases, emails, dashboards, publishing, or model calls with sensitive data require an approval record. Test: `test -f logs/gate-decisions/brand-reputation-news-intelligence-pipeline-approval.json || rg --fixed-strings "[TODO: APPROVE]" "recipes/brand-reputation-news-intelligence-pipeline.md"`. Human capacity: [EI].
6. Report gate: Agent log and human report are written with the required fields and sections. Test: `test -f logs/brand-reputation-news-intelligence-pipeline-[DATE].json && test -f reports/generated/brand-reputation-news-intelligence-pipeline-[DATE].md`. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI with Human gate.
   Script called: `scripts/tools/brand-reputation-news-intelligence-pipeline-verify-provenance.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `brand-reputation-news-intelligence-pipeline`.
   Output: workflow, source_paths, exists, parsed_ok, approval_state, checked_at.
   Where output goes: `logs/`
2. Step name: Ingest declared inputs. Labor: AI with Human gate.
   Script called: `scripts/ingest/brand-reputation-news-intelligence-pipeline-ingest-inputs.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `brand-reputation-news-intelligence-pipeline`.
   Output: records, source_name, source_type, fetched_at, sample_mode, rejects.
   Where output goes: `data/raw/brand-reputation-news-intelligence-pipeline/`
3. Step name: Validate data shape. Labor: AI with Human gate.
   Script called: `scripts/gigo/brand-reputation-news-intelligence-pipeline-validate-data-shape.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `brand-reputation-news-intelligence-pipeline`.
   Output: record_count, required_fields_present, missing_fields, parse_errors, schema_version.
   Where output goes: `data/verified/brand-reputation-news-intelligence-pipeline/`
4. Step name: Transform and quality check. Labor: AI with Human gate.
   Script called: `scripts/gigo/brand-reputation-news-intelligence-pipeline-transform-quality-check.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `brand-reputation-news-intelligence-pipeline`.
   Output: verified_records, record_count, duplicates, rejects, flags, quality_notes.
   Where output goes: `data/verified/brand-reputation-news-intelligence-pipeline/`
5. Step name: Run approved tools. Labor: AI with Human gate.
   Script called: `scripts/tools/brand-reputation-news-intelligence-pipeline-run-approved-tools.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `brand-reputation-news-intelligence-pipeline`.
   Output: tool_name, input_path, output_path, action_taken, approval_id, no_write_mode.
   Where output goes: `logs/`
6. Step name: Produce human report. Labor: AI with Human gate.
   Script called: `scripts/tools/brand-reputation-news-intelligence-pipeline-produce-human-report.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `brand-reputation-news-intelligence-pipeline`.
   Output: summary, sources_checked, gate_results, findings, typed_todos, next_decision.
   Where output goes: `reports/generated/`

## Output Contract

### Agent output
File: `logs/brand-reputation-news-intelligence-pipeline-[DATE].json`
Fields: workflow, run_id, mode, steps_completed, records_seen, rejects, duplicates, flags, stop_conditions, todo_items, source_files, gate_decisions, generated_at, raw_output_paths, verified_output_paths, report_path.

### Human report
File: `reports/generated/brand-reputation-news-intelligence-pipeline-[DATE].md`
Reader: domain lead or human boss responsible for accepting the `Brand Reputation News Intelligence Pipeline` run.
Decision enabled: approve the run for the next phase, request source/schema fixes, or block live execution.
Sections: run summary, purpose, source inventory, inputs used, phase-gate results, steps completed, records seen, rejects, duplicates, flags, typed TODOs, human approvals, verified findings, inferred findings, decision recommendation.

## Stop Conditions

- Stop if the recipe title or purpose does not match the original workflow intent.
- Stop if `pantry/singhvaibhav_351998_41799855_Singh_Vaibhav_A3_workflow.json` is missing or cannot be parsed.
- Stop if a source URL/path is unknown, stale, private, machine-specific, credential-bearing, or not approved; add `[TODO: APPROVE] replace source` and halt live mode.
- Stop if the workflow does not define critical fields for validation; add `[TODO: DEFINE] define required fields` before production.
- Stop if GIGO outputs do not expose record counts, rejects, duplicates, or missing fields.
- Stop if a final claim is not traceable to source or verified records.
- Stop if generated reports would expose credentials, private tokens, private local paths, or unapproved personal data.
- Stop if any live model, database, email, dashboard, file export, or API write is requested without explicit human approval.

## Snickerdoodle

### Run Commands
Full dialogic run:
`snickerdoodle run brand-reputation-news-intelligence-pipeline --mode dialogic`

Sample mode (no live network calls, no writes):
`snickerdoodle run brand-reputation-news-intelligence-pipeline --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Verify provenance | `snickerdoodle run brand-reputation-news-intelligence-pipeline --step verify-provenance` | `--sample` `--no-write` |
| Ingest declared inputs | `snickerdoodle run brand-reputation-news-intelligence-pipeline --step ingest-inputs` | `--sample` |
| Validate data shape | `snickerdoodle run brand-reputation-news-intelligence-pipeline --step validate-data-shape` | `--sample` |
| Transform and quality check | `snickerdoodle run brand-reputation-news-intelligence-pipeline --step transform-quality-check` | `--sample` |
| Run approved tools | `snickerdoodle run brand-reputation-news-intelligence-pipeline --step run-approved-tools` | `--sample` `--no-write` |
| Produce human report | `snickerdoodle run brand-reputation-news-intelligence-pipeline --step produce-human-report` | `--sample` `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - Source gate | `snickerdoodle gate brand-reputation-news-intelligence-pipeline --gate 1 --decision approve --note "Sources checked"` |
| Gate 2 - Scope gate | `snickerdoodle gate brand-reputation-news-intelligence-pipeline --gate 2 --decision approve --note "Scope and mode approved"` |
| Gate 3 - Data-shape gate | `snickerdoodle gate brand-reputation-news-intelligence-pipeline --gate 3 --decision approve --note "Outputs parse"` |
| Gate 4 - Script-readiness gate | `snickerdoodle gate brand-reputation-news-intelligence-pipeline --gate 4 --decision approve --note "Scripts ready or TODO DEV accepted"` |
| Gate 5 - Approval gate | `snickerdoodle gate brand-reputation-news-intelligence-pipeline --gate 5 --decision approve --note "Live or sensitive actions approved"` |
| Gate 6 - Report gate | `snickerdoodle gate brand-reputation-news-intelligence-pipeline --gate 6 --decision approve --note "Report and log complete"` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Verify provenance | `scripts/tools/brand-reputation-news-intelligence-pipeline-verify-provenance.py` | tools |
| Ingest declared inputs | `scripts/ingest/brand-reputation-news-intelligence-pipeline-ingest-inputs.py` | ingest |
| Validate data shape | `scripts/gigo/brand-reputation-news-intelligence-pipeline-validate-data-shape.py` | gigo |
| Transform and quality check | `scripts/gigo/brand-reputation-news-intelligence-pipeline-transform-quality-check.py` | gigo |
| Run approved tools | `scripts/tools/brand-reputation-news-intelligence-pipeline-run-approved-tools.py` | tools |
| Produce human report | `scripts/tools/brand-reputation-news-intelligence-pipeline-produce-human-report.py` | tools |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/brand-reputation-news-intelligence-pipeline/` | JSON |
| Verified data | `data/verified/brand-reputation-news-intelligence-pipeline/` | JSON |
| Agent log | `logs/brand-reputation-news-intelligence-pipeline-[DATE].json` | JSON |
| Human report | `reports/generated/brand-reputation-news-intelligence-pipeline-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

## Provenance

| Source | Verification command | Notes |
|---|---|---|
| `pantry/singhvaibhav_351998_41799855_Singh_Vaibhav_A3_workflow.json` | `test -f "pantry/singhvaibhav_351998_41799855_Singh_Vaibhav_A3_workflow.json"` | Referenced source/evidence path from prior recipe text. |

## Existing Recipe Notes Preserved For Implementation

### Extracted Notes

Combines TechCrunch, Ars Technica, The Verge, Google News brand queries, NewsAPI, and Hugging Face text rows into a deduplicated brand-reputation intelligence dataset. The business question is: what signals from these specific sources are reliable enough for a human boss to use in brand reputation intelligence decisions?

1. Source identity gate: Original workflow JSON exists and is the intended source. Test: `test -f "pantry/singhvaibhav_351998_41799855_Singh_Vaibhav_A3_workflow.json"`; if this fails, close [TODO: DATA SOURCE] by restoring or moving the workflow JSON before live mode.
   Human capacity: [PF].
2. Input readiness gate: Every required input in this recipe exists or is marked with a typed TODO. Test: `rg -n "TODO:" recipes/brand-reputation-news-intelligence-pipeline.md`.
   Human capacity: [PA].
3. Sample run gate: Ingest and tool steps run without live side effects before live mode. Test: `snickerdoodle run brand-reputation-news-intelligence-pipeline --mode dialogic --sample`.
   Human capacity: [TO].
4. Data-shape gate: Raw and verified outputs parse as JSON where applicable. Test: `find data/raw/brand-reputation-news-intelligence-pipeline data/verified/brand-reputation-news-intelligence-pipeline -name "*.json" -print -exec python3 -m json.tool {} \;`.
   Human capacity: [IJ].
5. Report contract gate: Human report defines reader, decision enabled, and sections. Test: `rg -n "Reader:|Decision enabled:|Sections:" recipes/brand-reputation-news-intelligence-pipeline.md`.
   Human capacity: [EI].

1. Step name: Verify provenance and source intent. Labor: Human.
   Human action: Record approval, rejection, or requested changes with supervisory capacity label [TODO: DEFINE].
   Input: pantry/singhvaibhav_351998_41799855_Singh_Vaibhav_A3_workflow.json.
   Output: provenance fields: workflow_path, exists, parsed_ok, title_matches_pipeline, source_inventory_checked.
   Where output goes: logs/gate-decisions/.
2. Step name: RSS - TechCrunch. Labor: AI with Human gate.
   Script called: `scripts/ingest/brand-reputation-news-intelligence-pipeline-rss-techcrunch.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
3. Step name: RSS - Ars Technica. Labor: AI with Human gate.
   Script called: `scripts/ingest/brand-reputation-news-intelligence-pipeline-rss-ars-technica.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
4. Step name: RSS - The Verge. Labor: AI with Human gate.
   Script called: `scripts/ingest/brand-reputation-news-intelligence-pipeline-rss-the-verge.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
5. Step name: RSS - Google News (Brand). Labor: AI with Human gate.
   Script called: `scripts/ingest/brand-reputation-news-intelligence-pipeline-rss-google-news-brand.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
6. Step name: Fetch NewsAPI brand-reputation articles. Labor: AI with Human gate.
   Script called: `scripts/ingest/brand-reputation-news-intelligence-pipeline-fetch-newsapi-brand-reputation-articles.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
7. Step name: Fetch Hugging Face text dataset rows. Labor: AI with Human gate.
   Script called: `scripts/ingest/brand-reputation-news-intelligence-pipeline-fetch-hugging-face-text-dataset-rows.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
8. Step name: Norm TechCrunch. Labor: AI with Human gate.
   Script called: `scripts/tools/brand-reputation-news-intelligence-pipeline-norm-techcrunch.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
9. Step name: Norm Ars Technica. Labor: AI with Human gate.
   Script called: `scripts/tools/brand-reputation-news-intelligence-pipeline-norm-ars-technica.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
10. Step name: Norm The Verge. Labor: AI with Human gate.
   Script called: `scripts/tools/brand-reputation-news-intelligence-pipeline-norm-the-verge.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
11. Step name: Norm Google News. Labor: AI with Human gate.
   Script called: `scripts/tools/brand-reputation-news-intelligence-pipeline-norm-google-news.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
12. Step name: Norm NewsAPI. Labor: AI with Human gate.
   Script called: `scripts/tools/brand-reputation-news-intelligence-pipeline-norm-newsapi.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
13. Step name: Norm HuggingFace. Labor: AI with Human gate.
   Script called: `scripts/gigo/brand-reputation-news-intelligence-pipeline-norm-huggingface.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
14. Step name: Deduplicate & Validate. Labor: AI with Human gate.
   Script called: `scripts/gigo/brand-reputation-news-intelligence-pipeline-deduplicate-and-validate.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
15. Step name: Prepare brand-reputation CSV export. Labor: AI with Human gate.
   Script called: `scripts/tools/brand-reputation-news-intelligence-pipeline-prepare-brand-reputation-csv-export.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
16. Step name: Write brand-reputation CSV handoff. Labor: AI with Human gate.
   Script called: `scripts/tools/brand-reputation-news-intelligence-pipeline-write-brand-reputation-csv-handoff.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
17. Step name: Produce human report. Labor: AI with Human review.
   Script called: `scripts/tools/brand-reputation-news-intelligence-pipeline-produce-human-report.py`
   Input: agent log plus raw and verified outputs.
   Output: markdown report sections: run summary, source inventory, inputs used, validation results, flags, typed TODOs, decision recommendation.
   Where output goes: reports/generated/.
