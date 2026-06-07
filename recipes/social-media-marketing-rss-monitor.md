# Social Media Marketing RSS Monitor

## Purpose

Aggregates social-media and marketing RSS sources from HubSpot, Sprout Social, Hootsuite, Social Media Examiner, and Search Engine Journal. The business question is: what signals from these specific sources are reliable enough for a human boss to use in social media marketing monitoring decisions?

## Source Inventory

| Source Node | Node Type | Source URL or Path | Human Check |
|---|---|---|---|
| Fetch HubSpot marketing RSS | `rssFeedRead` | `https://blog.hubspot.com/marketing/rss.xml` | Confirm source is allowed, current, and rate-safe before live fetch. |
| Fetch Sprout Social insights RSS | `rssFeedRead` | `https://sproutsocial.com/insights/feed/` | Confirm source is allowed, current, and rate-safe before live fetch. |
| Fetch Hootsuite blog RSS | `rssFeedRead` | `https://blog.hootsuite.com/feed/` | Confirm source is allowed, current, and rate-safe before live fetch. |
| Fetch Social Media Examiner RSS | `rssFeedRead` | `https://www.socialmediaexaminer.com/feed/` | Confirm source is allowed, current, and rate-safe before live fetch. |
| Fetch Search Engine Journal RSS | `rssFeedRead` | `https://www.searchenginejournal.com/feed/` | Confirm source is allowed, current, and rate-safe before live fetch. |
| Fetch Search Engine Journal duplicate RSS source | `rssFeedRead` | `https://www.searchenginejournal.com/feed/` | Confirm source is allowed, current, and rate-safe before live fetch. |

| Node Name | Node Type | Classification |
|---|---|---|
| When clicking 'Execute workflow' | `manualTrigger` | conductor |
| Fetch HubSpot marketing RSS | `rssFeedRead` | ingest |
| Fetch Sprout Social insights RSS | `rssFeedRead` | ingest |
| Fetch Hootsuite blog RSS | `rssFeedRead` | ingest |
| Merge | `merge` | conductor |
| Merge1 | `merge` | conductor |
| Normalize social-media marketing RSS fields | `set` | gigo |
| Prepare social-media marketing feed export | `convertToFile` | tool |
| Fetch Social Media Examiner RSS | `rssFeedRead` | ingest |
| Fetch Search Engine Journal RSS | `rssFeedRead` | ingest |
| Fetch Search Engine Journal duplicate RSS source | `rssFeedRead` | ingest |
| Merge2 | `merge` | conductor |
| Merge3 | `merge` | conductor |
| Merge4 | `merge` | conductor |
## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Original n8n workflow JSON | JSON | [TODO: DATA SOURCE] Restore or move original workflow JSON to a repo-local path. Last documented path: pantry/zuxinchen_405407_41801846_Zu_Xinchen_A3_Workflow.json | Yes |
| Fetch HubSpot marketing RSS | Source payload | `https://blog.hubspot.com/marketing/rss.xml` | Yes |
| Fetch Sprout Social insights RSS | Source payload | `https://sproutsocial.com/insights/feed/` | Yes |
| Fetch Hootsuite blog RSS | Source payload | `https://blog.hootsuite.com/feed/` | Yes |
| Fetch Social Media Examiner RSS | Source payload | `https://www.socialmediaexaminer.com/feed/` | Yes |
| Fetch Search Engine Journal RSS | Source payload | `https://www.searchenginejournal.com/feed/` | Yes |
| Fetch Search Engine Journal duplicate RSS source | Source payload | `https://www.searchenginejournal.com/feed/` | Yes |

## Phase Gates

1. Source gate: All required source paths are present or explicitly marked with a typed TODO. Test: `test -f "recipes/social-media-marketing-rss-monitor.md" && rg -n "\[TODO: DEFINE]" "recipes/social-media-marketing-rss-monitor.md" || true`. Human capacity: [TO].
2. Scope gate: The run declares `sample` mode or an approved live mode before ingest begins. Test: `python3 -m json.tool data/raw/social-media-marketing-rss-monitor/run-envelope.json`. Human capacity: [PF].
3. Data-shape gate: Every raw and verified JSON output parses before downstream scripts run. Test: `find data/raw/social-media-marketing-rss-monitor data/verified/social-media-marketing-rss-monitor -name "*.json" -print -exec python3 -m json.tool {} \;`. Human capacity: [PA].
4. Script-readiness gate: Every step script exists or is represented by a typed development TODO. Test: `test -f scripts/ingest/social-media-marketing-rss-monitor-ingest-inputs.py || rg --fixed-strings "[TODO: DEV]" "recipes/social-media-marketing-rss-monitor.md"`. Human capacity: [IJ].
5. Approval gate: Live network calls, external writes, credentials, production databases, emails, dashboards, publishing, or model calls with sensitive data require an approval record. Test: `test -f logs/gate-decisions/social-media-marketing-rss-monitor-approval.json || rg --fixed-strings "[TODO: APPROVE]" "recipes/social-media-marketing-rss-monitor.md"`. Human capacity: [EI].
6. Report gate: Agent log and human report are written with the required fields and sections. Test: `test -f logs/social-media-marketing-rss-monitor-[DATE].json && test -f reports/generated/social-media-marketing-rss-monitor-[DATE].md`. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI with Human gate.
   Script called: `scripts/tools/social-media-marketing-rss-monitor-verify-provenance.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `social-media-marketing-rss-monitor`.
   Output: workflow, source_paths, exists, parsed_ok, approval_state, checked_at.
   Where output goes: `logs/`
2. Step name: Ingest declared inputs. Labor: AI with Human gate.
   Script called: `scripts/ingest/social-media-marketing-rss-monitor-ingest-inputs.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `social-media-marketing-rss-monitor`.
   Output: records, source_name, source_type, fetched_at, sample_mode, rejects.
   Where output goes: `data/raw/social-media-marketing-rss-monitor/`
3. Step name: Validate data shape. Labor: AI with Human gate.
   Script called: `scripts/gigo/social-media-marketing-rss-monitor-validate-data-shape.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `social-media-marketing-rss-monitor`.
   Output: record_count, required_fields_present, missing_fields, parse_errors, schema_version.
   Where output goes: `data/verified/social-media-marketing-rss-monitor/`
4. Step name: Transform and quality check. Labor: AI with Human gate.
   Script called: `scripts/gigo/social-media-marketing-rss-monitor-transform-quality-check.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `social-media-marketing-rss-monitor`.
   Output: verified_records, record_count, duplicates, rejects, flags, quality_notes.
   Where output goes: `data/verified/social-media-marketing-rss-monitor/`
5. Step name: Run approved tools. Labor: AI with Human gate.
   Script called: `scripts/tools/social-media-marketing-rss-monitor-run-approved-tools.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `social-media-marketing-rss-monitor`.
   Output: tool_name, input_path, output_path, action_taken, approval_id, no_write_mode.
   Where output goes: `logs/`
6. Step name: Produce human report. Labor: AI with Human gate.
   Script called: `scripts/tools/social-media-marketing-rss-monitor-produce-human-report.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `social-media-marketing-rss-monitor`.
   Output: summary, sources_checked, gate_results, findings, typed_todos, next_decision.
   Where output goes: `reports/generated/`

## Output Contract

### Agent output
File: `logs/social-media-marketing-rss-monitor-[DATE].json`
Fields: workflow, run_id, mode, steps_completed, records_seen, rejects, duplicates, flags, stop_conditions, todo_items, source_files, gate_decisions, generated_at, raw_output_paths, verified_output_paths, report_path.

### Human report
File: `reports/generated/social-media-marketing-rss-monitor-[DATE].md`
Reader: domain lead or human boss responsible for accepting the `Social Media Marketing RSS Monitor` run.
Decision enabled: approve the run for the next phase, request source/schema fixes, or block live execution.
Sections: run summary, purpose, source inventory, inputs used, phase-gate results, steps completed, records seen, rejects, duplicates, flags, typed TODOs, human approvals, verified findings, inferred findings, decision recommendation.

## Stop Conditions

- Stop if the recipe title or purpose does not match the original workflow intent.
- Stop if `pantry/zuxinchen_405407_41801846_Zu_Xinchen_A3_Workflow.json` is missing or cannot be parsed.
- Stop if a source URL/path is unknown, stale, private, machine-specific, credential-bearing, or not approved; add `[TODO: APPROVE] replace source` and halt live mode.
- Stop if the workflow does not define critical fields for validation; add `[TODO: DEFINE] define required fields` before production.
- Stop if GIGO outputs do not expose record counts, rejects, duplicates, or missing fields.
- Stop if a final claim is not traceable to source or verified records.
- Stop if generated reports would expose credentials, private tokens, private local paths, or unapproved personal data.
- Stop if any live model, database, email, dashboard, file export, or API write is requested without explicit human approval.

## Snickerdoodle

### Run Commands
Full dialogic run:
`snickerdoodle run social-media-marketing-rss-monitor --mode dialogic`

Sample mode (no live network calls, no writes):
`snickerdoodle run social-media-marketing-rss-monitor --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Verify provenance | `snickerdoodle run social-media-marketing-rss-monitor --step verify-provenance` | `--sample` `--no-write` |
| Ingest declared inputs | `snickerdoodle run social-media-marketing-rss-monitor --step ingest-inputs` | `--sample` |
| Validate data shape | `snickerdoodle run social-media-marketing-rss-monitor --step validate-data-shape` | `--sample` |
| Transform and quality check | `snickerdoodle run social-media-marketing-rss-monitor --step transform-quality-check` | `--sample` |
| Run approved tools | `snickerdoodle run social-media-marketing-rss-monitor --step run-approved-tools` | `--sample` `--no-write` |
| Produce human report | `snickerdoodle run social-media-marketing-rss-monitor --step produce-human-report` | `--sample` `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - Source gate | `snickerdoodle gate social-media-marketing-rss-monitor --gate 1 --decision approve --note "Sources checked"` |
| Gate 2 - Scope gate | `snickerdoodle gate social-media-marketing-rss-monitor --gate 2 --decision approve --note "Scope and mode approved"` |
| Gate 3 - Data-shape gate | `snickerdoodle gate social-media-marketing-rss-monitor --gate 3 --decision approve --note "Outputs parse"` |
| Gate 4 - Script-readiness gate | `snickerdoodle gate social-media-marketing-rss-monitor --gate 4 --decision approve --note "Scripts ready or TODO DEV accepted"` |
| Gate 5 - Approval gate | `snickerdoodle gate social-media-marketing-rss-monitor --gate 5 --decision approve --note "Live or sensitive actions approved"` |
| Gate 6 - Report gate | `snickerdoodle gate social-media-marketing-rss-monitor --gate 6 --decision approve --note "Report and log complete"` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Verify provenance | `scripts/tools/social-media-marketing-rss-monitor-verify-provenance.py` | tools |
| Ingest declared inputs | `scripts/ingest/social-media-marketing-rss-monitor-ingest-inputs.py` | ingest |
| Validate data shape | `scripts/gigo/social-media-marketing-rss-monitor-validate-data-shape.py` | gigo |
| Transform and quality check | `scripts/gigo/social-media-marketing-rss-monitor-transform-quality-check.py` | gigo |
| Run approved tools | `scripts/tools/social-media-marketing-rss-monitor-run-approved-tools.py` | tools |
| Produce human report | `scripts/tools/social-media-marketing-rss-monitor-produce-human-report.py` | tools |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/social-media-marketing-rss-monitor/` | JSON |
| Verified data | `data/verified/social-media-marketing-rss-monitor/` | JSON |
| Agent log | `logs/social-media-marketing-rss-monitor-[DATE].json` | JSON |
| Human report | `reports/generated/social-media-marketing-rss-monitor-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

## Provenance

| Source | Verification command | Notes |
|---|---|---|
| `pantry/zuxinchen_405407_41801846_Zu_Xinchen_A3_Workflow.json` | `test -f "pantry/zuxinchen_405407_41801846_Zu_Xinchen_A3_Workflow.json"` | Referenced source/evidence path from prior recipe text. |

## Existing Recipe Notes Preserved For Implementation

### Extracted Notes

Aggregates social-media and marketing RSS sources from HubSpot, Sprout Social, Hootsuite, Social Media Examiner, and Search Engine Journal. The business question is: what signals from these specific sources are reliable enough for a human boss to use in social media marketing monitoring decisions?

1. Source identity gate: Original workflow JSON exists and is the intended source. Test: `test -f "pantry/zuxinchen_405407_41801846_Zu_Xinchen_A3_Workflow.json"`; if this fails, close [TODO: DATA SOURCE] by restoring or moving the workflow JSON before live mode.
   Human capacity: [PF].
2. Input readiness gate: Every required input in this recipe exists or is marked with a typed TODO. Test: `rg -n "TODO:" recipes/social-media-marketing-rss-monitor.md`.
   Human capacity: [PA].
3. Sample run gate: Ingest and tool steps run without live side effects before live mode. Test: `snickerdoodle run social-media-marketing-rss-monitor --mode dialogic --sample`.
   Human capacity: [TO].
4. Data-shape gate: Raw and verified outputs parse as JSON where applicable. Test: `find data/raw/social-media-marketing-rss-monitor data/verified/social-media-marketing-rss-monitor -name "*.json" -print -exec python3 -m json.tool {} \;`.
   Human capacity: [IJ].
5. Report contract gate: Human report defines reader, decision enabled, and sections. Test: `rg -n "Reader:|Decision enabled:|Sections:" recipes/social-media-marketing-rss-monitor.md`.
   Human capacity: [EI].

1. Step name: Verify provenance and source intent. Labor: Human.
   Human action: Record approval, rejection, or requested changes with supervisory capacity label [TODO: DEFINE].
   Input: pantry/zuxinchen_405407_41801846_Zu_Xinchen_A3_Workflow.json.
   Output: provenance fields: workflow_path, exists, parsed_ok, title_matches_pipeline, source_inventory_checked.
   Where output goes: logs/gate-decisions/.
2. Step name: Fetch HubSpot marketing RSS. Labor: AI with Human gate.
   Script called: `scripts/ingest/social-media-marketing-rss-monitor-fetch-hubspot-marketing-rss.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
3. Step name: Fetch Sprout Social insights RSS. Labor: AI with Human gate.
   Script called: `scripts/ingest/social-media-marketing-rss-monitor-fetch-sprout-social-insights-rss.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
4. Step name: Fetch Hootsuite blog RSS. Labor: AI with Human gate.
   Script called: `scripts/ingest/social-media-marketing-rss-monitor-fetch-hootsuite-blog-rss.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
5. Step name: Normalize social-media marketing RSS fields. Labor: AI with Human gate.
   Script called: `scripts/gigo/social-media-marketing-rss-monitor-normalize-social-media-marketing-rss-fields.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
6. Step name: Prepare social-media marketing feed export. Labor: AI with Human gate.
   Script called: `scripts/tools/social-media-marketing-rss-monitor-prepare-social-media-marketing-feed-export.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
7. Step name: Fetch Social Media Examiner RSS. Labor: AI with Human gate.
   Script called: `scripts/ingest/social-media-marketing-rss-monitor-fetch-social-media-examiner-rss.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
8. Step name: Fetch Search Engine Journal RSS. Labor: AI with Human gate.
   Script called: `scripts/ingest/social-media-marketing-rss-monitor-fetch-search-engine-journal-rss.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
9. Step name: Fetch Search Engine Journal duplicate RSS source. Labor: AI with Human gate.
   Script called: `scripts/ingest/social-media-marketing-rss-monitor-fetch-search-engine-journal-duplicate-rss-source.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
10. Step name: Produce human report. Labor: AI with Human review.
   Script called: `scripts/tools/social-media-marketing-rss-monitor-produce-human-report.py`
   Input: agent log plus raw and verified outputs.
   Output: markdown report sections: run summary, source inventory, inputs used, validation results, flags, typed TODOs, decision recommendation.
   Where output goes: reports/generated/.
