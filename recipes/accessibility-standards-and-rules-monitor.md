# Accessibility Standards And Rules Monitor

## Purpose

Collects axe-core rule metadata, W3C WCAG criteria, WebAIM posts, and A11y Project posts into a deduplicated accessibility monitoring dataset. The business question is: what signals from these specific sources are reliable enough for a human boss to use in accessibility intelligence decisions?

## Source Inventory

| Source Node | Node Type | Source URL or Path | Human Check |
|---|---|---|---|
| W3C WCAG JSON - Success Criteria | `httpRequest` | `https://www.w3.org/WAI/WCAG21/wcag.json` | Confirm source is allowed, current, and rate-safe before live fetch. |
| RSS - WebAIM Blog | `rssFeedRead` | `https://webaim.org/blog/feed/` | Confirm source is allowed, current, and rate-safe before live fetch. |
| RSS - A11y Project | `rssFeedRead` | `https://www.a11yproject.com/feed/feed.xml` | Confirm source is allowed, current, and rate-safe before live fetch. |

| Node Name | Node Type | Classification |
|---|---|---|
| Manual Trigger | `manualTrigger` | conductor |
| GitHub API - Axe-core Rules | `code` | gigo |
| W3C WCAG JSON - Success Criteria | `httpRequest` | ingest |
| RSS - WebAIM Blog | `rssFeedRead` | ingest |
| RSS - A11y Project | `rssFeedRead` | ingest |
| Merge + Normalize + Deduplicate | `code` | gigo |
| Quality Gate - Min 50 Records | `if` | conductor |
| Save to CSV | `spreadsheetFile` | tool |
| Write Error Log | `set` | gigo |
## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Original n8n workflow JSON | JSON | [TODO: DATA SOURCE] Restore or move original workflow JSON to a repo-local path. Last documented path: pantry/singhkanishknagendra_348738_41749683_Singh_Kanishk_A3_Workflow.json | Yes |
| W3C WCAG JSON - Success Criteria | Source payload | `https://www.w3.org/WAI/WCAG21/wcag.json` | Yes |
| RSS - WebAIM Blog | Source payload | `https://webaim.org/blog/feed/` | Yes |
| RSS - A11y Project | Source payload | `https://www.a11yproject.com/feed/feed.xml` | Yes |

## Phase Gates

1. Source gate: All required source paths are present or explicitly marked with a typed TODO. Test: `test -f "recipes/accessibility-standards-and-rules-monitor.md" && rg -n "\[TODO: DEFINE]" "recipes/accessibility-standards-and-rules-monitor.md" || true`. Human capacity: [TO].
2. Scope gate: The run declares `sample` mode or an approved live mode before ingest begins. Test: `python3 -m json.tool data/raw/accessibility-standards-and-rules-monitor/run-envelope.json`. Human capacity: [PF].
3. Data-shape gate: Every raw and verified JSON output parses before downstream scripts run. Test: `find data/raw/accessibility-standards-and-rules-monitor data/verified/accessibility-standards-and-rules-monitor -name "*.json" -print -exec python3 -m json.tool {} \;`. Human capacity: [PA].
4. Script-readiness gate: Every step script exists or is represented by a typed development TODO. Test: `test -f scripts/ingest/accessibility-standards-and-rules-monitor-ingest-inputs.py || rg --fixed-strings "[TODO: DEV]" "recipes/accessibility-standards-and-rules-monitor.md"`. Human capacity: [IJ].
5. Approval gate: Live network calls, external writes, credentials, production databases, emails, dashboards, publishing, or model calls with sensitive data require an approval record. Test: `test -f logs/gate-decisions/accessibility-standards-and-rules-monitor-approval.json || rg --fixed-strings "[TODO: APPROVE]" "recipes/accessibility-standards-and-rules-monitor.md"`. Human capacity: [EI].
6. Report gate: Agent log and human report are written with the required fields and sections. Test: `test -f logs/accessibility-standards-and-rules-monitor-[DATE].json && test -f reports/generated/accessibility-standards-and-rules-monitor-[DATE].md`. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI with Human gate.
   Script called: `scripts/tools/accessibility-standards-and-rules-monitor-verify-provenance.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `accessibility-standards-and-rules-monitor`.
   Output: workflow, source_paths, exists, parsed_ok, approval_state, checked_at.
   Where output goes: `logs/`
2. Step name: Ingest declared inputs. Labor: AI with Human gate.
   Script called: `scripts/ingest/accessibility-standards-and-rules-monitor-ingest-inputs.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `accessibility-standards-and-rules-monitor`.
   Output: records, source_name, source_type, fetched_at, sample_mode, rejects.
   Where output goes: `data/raw/accessibility-standards-and-rules-monitor/`
3. Step name: Validate data shape. Labor: AI with Human gate.
   Script called: `scripts/gigo/accessibility-standards-and-rules-monitor-validate-data-shape.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `accessibility-standards-and-rules-monitor`.
   Output: record_count, required_fields_present, missing_fields, parse_errors, schema_version.
   Where output goes: `data/verified/accessibility-standards-and-rules-monitor/`
4. Step name: Transform and quality check. Labor: AI with Human gate.
   Script called: `scripts/gigo/accessibility-standards-and-rules-monitor-transform-quality-check.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `accessibility-standards-and-rules-monitor`.
   Output: verified_records, record_count, duplicates, rejects, flags, quality_notes.
   Where output goes: `data/verified/accessibility-standards-and-rules-monitor/`
5. Step name: Run approved tools. Labor: AI with Human gate.
   Script called: `scripts/tools/accessibility-standards-and-rules-monitor-run-approved-tools.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `accessibility-standards-and-rules-monitor`.
   Output: tool_name, input_path, output_path, action_taken, approval_id, no_write_mode.
   Where output goes: `logs/`
6. Step name: Produce human report. Labor: AI with Human gate.
   Script called: `scripts/tools/accessibility-standards-and-rules-monitor-produce-human-report.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `accessibility-standards-and-rules-monitor`.
   Output: summary, sources_checked, gate_results, findings, typed_todos, next_decision.
   Where output goes: `reports/generated/`

## Output Contract

### Agent output
File: `logs/accessibility-standards-and-rules-monitor-[DATE].json`
Fields: workflow, run_id, mode, steps_completed, records_seen, rejects, duplicates, flags, stop_conditions, todo_items, source_files, gate_decisions, generated_at, raw_output_paths, verified_output_paths, report_path.

### Human report
File: `reports/generated/accessibility-standards-and-rules-monitor-[DATE].md`
Reader: domain lead or human boss responsible for accepting the `Accessibility Standards And Rules Monitor` run.
Decision enabled: approve the run for the next phase, request source/schema fixes, or block live execution.
Sections: run summary, purpose, source inventory, inputs used, phase-gate results, steps completed, records seen, rejects, duplicates, flags, typed TODOs, human approvals, verified findings, inferred findings, decision recommendation.

## Stop Conditions

- Stop if the recipe title or purpose does not match the original workflow intent.
- Stop if `pantry/singhkanishknagendra_348738_41749683_Singh_Kanishk_A3_Workflow.json` is missing or cannot be parsed.
- Stop if a source URL/path is unknown, stale, private, machine-specific, credential-bearing, or not approved; add `[TODO: APPROVE] replace source` and halt live mode.
- Stop if the workflow does not define critical fields for validation; add `[TODO: DEFINE] define required fields` before production.
- Stop if GIGO outputs do not expose record counts, rejects, duplicates, or missing fields.
- Stop if a final claim is not traceable to source or verified records.
- Stop if generated reports would expose credentials, private tokens, private local paths, or unapproved personal data.
- Stop if any live model, database, email, dashboard, file export, or API write is requested without explicit human approval.

## Snickerdoodle

### Run Commands
Full dialogic run:
`snickerdoodle run accessibility-standards-and-rules-monitor --mode dialogic`

Sample mode (no live network calls, no writes):
`snickerdoodle run accessibility-standards-and-rules-monitor --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Verify provenance | `snickerdoodle run accessibility-standards-and-rules-monitor --step verify-provenance` | `--sample` `--no-write` |
| Ingest declared inputs | `snickerdoodle run accessibility-standards-and-rules-monitor --step ingest-inputs` | `--sample` |
| Validate data shape | `snickerdoodle run accessibility-standards-and-rules-monitor --step validate-data-shape` | `--sample` |
| Transform and quality check | `snickerdoodle run accessibility-standards-and-rules-monitor --step transform-quality-check` | `--sample` |
| Run approved tools | `snickerdoodle run accessibility-standards-and-rules-monitor --step run-approved-tools` | `--sample` `--no-write` |
| Produce human report | `snickerdoodle run accessibility-standards-and-rules-monitor --step produce-human-report` | `--sample` `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - Source gate | `snickerdoodle gate accessibility-standards-and-rules-monitor --gate 1 --decision approve --note "Sources checked"` |
| Gate 2 - Scope gate | `snickerdoodle gate accessibility-standards-and-rules-monitor --gate 2 --decision approve --note "Scope and mode approved"` |
| Gate 3 - Data-shape gate | `snickerdoodle gate accessibility-standards-and-rules-monitor --gate 3 --decision approve --note "Outputs parse"` |
| Gate 4 - Script-readiness gate | `snickerdoodle gate accessibility-standards-and-rules-monitor --gate 4 --decision approve --note "Scripts ready or TODO DEV accepted"` |
| Gate 5 - Approval gate | `snickerdoodle gate accessibility-standards-and-rules-monitor --gate 5 --decision approve --note "Live or sensitive actions approved"` |
| Gate 6 - Report gate | `snickerdoodle gate accessibility-standards-and-rules-monitor --gate 6 --decision approve --note "Report and log complete"` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Verify provenance | `scripts/tools/accessibility-standards-and-rules-monitor-verify-provenance.py` | tools |
| Ingest declared inputs | `scripts/ingest/accessibility-standards-and-rules-monitor-ingest-inputs.py` | ingest |
| Validate data shape | `scripts/gigo/accessibility-standards-and-rules-monitor-validate-data-shape.py` | gigo |
| Transform and quality check | `scripts/gigo/accessibility-standards-and-rules-monitor-transform-quality-check.py` | gigo |
| Run approved tools | `scripts/tools/accessibility-standards-and-rules-monitor-run-approved-tools.py` | tools |
| Produce human report | `scripts/tools/accessibility-standards-and-rules-monitor-produce-human-report.py` | tools |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/accessibility-standards-and-rules-monitor/` | JSON |
| Verified data | `data/verified/accessibility-standards-and-rules-monitor/` | JSON |
| Agent log | `logs/accessibility-standards-and-rules-monitor-[DATE].json` | JSON |
| Human report | `reports/generated/accessibility-standards-and-rules-monitor-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

## Provenance

| Source | Verification command | Notes |
|---|---|---|
| `pantry/singhkanishknagendra_348738_41749683_Singh_Kanishk_A3_Workflow.json` | `test -f "pantry/singhkanishknagendra_348738_41749683_Singh_Kanishk_A3_Workflow.json"` | Referenced source/evidence path from prior recipe text. |

## Existing Recipe Notes Preserved For Implementation

### Extracted Notes

Collects axe-core rule metadata, W3C WCAG criteria, WebAIM posts, and A11y Project posts into a deduplicated accessibility monitoring dataset. The business question is: what signals from these specific sources are reliable enough for a human boss to use in accessibility intelligence decisions?

1. Source identity gate: Original workflow JSON exists and is the intended source. Test: `test -f "pantry/singhkanishknagendra_348738_41749683_Singh_Kanishk_A3_Workflow.json"`; if this fails, close [TODO: DATA SOURCE] by restoring or moving the workflow JSON before live mode.
   Human capacity: [PF].
2. Input readiness gate: Every required input in this recipe exists or is marked with a typed TODO. Test: `rg -n "TODO:" recipes/accessibility-standards-and-rules-monitor.md`.
   Human capacity: [PA].
3. Sample run gate: Ingest and tool steps run without live side effects before live mode. Test: `snickerdoodle run accessibility-standards-and-rules-monitor --mode dialogic --sample`.
   Human capacity: [TO].
4. Data-shape gate: Raw and verified outputs parse as JSON where applicable. Test: `find data/raw/accessibility-standards-and-rules-monitor data/verified/accessibility-standards-and-rules-monitor -name "*.json" -print -exec python3 -m json.tool {} \;`.
   Human capacity: [IJ].
5. Report contract gate: Human report defines reader, decision enabled, and sections. Test: `rg -n "Reader:|Decision enabled:|Sections:" recipes/accessibility-standards-and-rules-monitor.md`.
   Human capacity: [EI].

1. Step name: Verify provenance and source intent. Labor: Human.
   Human action: Record approval, rejection, or requested changes with supervisory capacity label [TODO: DEFINE].
   Input: pantry/singhkanishknagendra_348738_41749683_Singh_Kanishk_A3_Workflow.json.
   Output: provenance fields: workflow_path, exists, parsed_ok, title_matches_pipeline, source_inventory_checked.
   Where output goes: logs/gate-decisions/.
2. Step name: GitHub API - Axe-core Rules. Labor: AI with Human gate.
   Script called: `scripts/gigo/accessibility-standards-and-rules-monitor-github-api-axe-core-rules.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
3. Step name: W3C WCAG JSON - Success Criteria. Labor: AI with Human gate.
   Script called: `scripts/ingest/accessibility-standards-and-rules-monitor-w3c-wcag-json-success-criteria.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
4. Step name: RSS - WebAIM Blog. Labor: AI with Human gate.
   Script called: `scripts/ingest/accessibility-standards-and-rules-monitor-rss-webaim-blog.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
5. Step name: RSS - A11y Project. Labor: AI with Human gate.
   Script called: `scripts/ingest/accessibility-standards-and-rules-monitor-rss-a11y-project.py`
   Input: approved upstream output or sample fixture.
   Output: raw JSON fields: source_name, source_url_or_path, fetched_at, record_count, records, errors.
   Where output goes: data/raw/.
6. Step name: Merge + Normalize + Deduplicate. Labor: AI with Human gate.
   Script called: `scripts/gigo/accessibility-standards-and-rules-monitor-merge-normalize-deduplicate.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
7. Step name: Save to CSV. Labor: AI with Human gate.
   Script called: `scripts/tools/accessibility-standards-and-rules-monitor-save-to-csv.py`
   Input: approved upstream output or sample fixture.
   Output: local handoff JSON fields: action, approved_for_live_action:false, input_refs, output_refs, flags.
   Where output goes: logs/.
8. Step name: Write Error Log. Labor: AI with Human gate.
   Script called: `scripts/gigo/accessibility-standards-and-rules-monitor-write-error-log.py`
   Input: approved upstream output or sample fixture.
   Output: verified JSON fields: record_count, records, rejects, duplicates, missing_fields, validation_flags.
   Where output goes: data/verified/.
9. Step name: Produce human report. Labor: AI with Human review.
   Script called: `scripts/tools/accessibility-standards-and-rules-monitor-produce-human-report.py`
   Input: agent log plus raw and verified outputs.
   Output: markdown report sections: run summary, source inventory, inputs used, validation results, flags, typed TODOs, decision recommendation.
   Where output goes: reports/generated/.
