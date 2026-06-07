# Madison Innovation Positioning Patent Tracker

## Purpose

Translates patent and invention activity into brand-safe innovation-positioning signals so marketing teams can understand which claims about novelty, technical leadership, or product roadmap momentum are supportable.

## Source Inventory

| Source Node | Node Type | Source URL or Path | Human Check |
|---|---|---|---|
| Recipe specification | Markdown recipe | `recipes/madison-innovation-positioning-patent-tracker.md` | Confirm this specification is current and approved before script generation. |

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Company watchlist | JSON | [TODO: DATA SOURCE] Approved companies, subsidiaries, inventors, and assignees. | Yes |
| Patent records | JSON/API | [TODO: DATA SOURCE] USPTO, Google Patents export, Lens, or approved local patent dataset. | Yes |
| Innovation rubric | JSON | [TODO: DEFINE] Define novelty, velocity, category fit, defensibility, and messaging relevance. | Yes |
| Mycroft adaptation source | Markdown | `/Users/bear/Documents/CoWork/bear-textbooks/books/mycroft/recipes/patent-filing-velocity-tracker.md` | No |

## Phase Gates

1. Source gate: All required source paths are present or explicitly marked with a typed TODO. Test: `test -f "recipes/madison-innovation-positioning-patent-tracker.md" && rg -n "\[TODO: DEFINE]" "recipes/madison-innovation-positioning-patent-tracker.md" || true`. Human capacity: [TO].
2. Scope gate: The run declares `sample` mode or an approved live mode before ingest begins. Test: `python3 -m json.tool data/raw/madison-innovation-positioning-patent-tracker/run-envelope.json`. Human capacity: [PF].
3. Data-shape gate: Every raw and verified JSON output parses before downstream scripts run. Test: `find data/raw/madison-innovation-positioning-patent-tracker data/verified/madison-innovation-positioning-patent-tracker -name "*.json" -print -exec python3 -m json.tool {} \;`. Human capacity: [PA].
4. Script-readiness gate: Every step script exists or is represented by a typed development TODO. Test: `test -f scripts/ingest/madison-innovation-positioning-patent-tracker-ingest-inputs.py || rg --fixed-strings "[TODO: DEV]" "recipes/madison-innovation-positioning-patent-tracker.md"`. Human capacity: [IJ].
5. Approval gate: Live network calls, external writes, credentials, production databases, emails, dashboards, publishing, or model calls with sensitive data require an approval record. Test: `test -f logs/gate-decisions/madison-innovation-positioning-patent-tracker-approval.json || rg --fixed-strings "[TODO: APPROVE]" "recipes/madison-innovation-positioning-patent-tracker.md"`. Human capacity: [EI].
6. Report gate: Agent log and human report are written with the required fields and sections. Test: `test -f logs/madison-innovation-positioning-patent-tracker-[DATE].json && test -f reports/generated/madison-innovation-positioning-patent-tracker-[DATE].md`. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI with Human gate.
   Script called: `scripts/tools/madison-innovation-positioning-patent-tracker-verify-provenance.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `madison-innovation-positioning-patent-tracker`.
   Output: workflow, source_paths, exists, parsed_ok, approval_state, checked_at.
   Where output goes: `logs/`
2. Step name: Ingest declared inputs. Labor: AI with Human gate.
   Script called: `scripts/ingest/madison-innovation-positioning-patent-tracker-ingest-inputs.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `madison-innovation-positioning-patent-tracker`.
   Output: records, source_name, source_type, fetched_at, sample_mode, rejects.
   Where output goes: `data/raw/madison-innovation-positioning-patent-tracker/`
3. Step name: Validate data shape. Labor: AI with Human gate.
   Script called: `scripts/gigo/madison-innovation-positioning-patent-tracker-validate-data-shape.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `madison-innovation-positioning-patent-tracker`.
   Output: record_count, required_fields_present, missing_fields, parse_errors, schema_version.
   Where output goes: `data/verified/madison-innovation-positioning-patent-tracker/`
4. Step name: Transform and quality check. Labor: AI with Human gate.
   Script called: `scripts/gigo/madison-innovation-positioning-patent-tracker-transform-quality-check.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `madison-innovation-positioning-patent-tracker`.
   Output: verified_records, record_count, duplicates, rejects, flags, quality_notes.
   Where output goes: `data/verified/madison-innovation-positioning-patent-tracker/`
5. Step name: Run approved tools. Labor: AI with Human gate.
   Script called: `scripts/tools/madison-innovation-positioning-patent-tracker-run-approved-tools.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `madison-innovation-positioning-patent-tracker`.
   Output: tool_name, input_path, output_path, action_taken, approval_id, no_write_mode.
   Where output goes: `logs/`
6. Step name: Produce human report. Labor: AI with Human gate.
   Script called: `scripts/tools/madison-innovation-positioning-patent-tracker-produce-human-report.py` [TODO: DEV] Define input schema, output schema, transformation logic, and error handling for this script before implementation.
   Input: declared recipe inputs, prior step outputs, and gate decisions for `madison-innovation-positioning-patent-tracker`.
   Output: summary, sources_checked, gate_results, findings, typed_todos, next_decision.
   Where output goes: `reports/generated/`

## Output Contract

### Agent output
File: `logs/madison-innovation-positioning-patent-tracker-[DATE].json`
Fields: workflow, run_id, mode, steps_completed, records_seen, rejects, duplicates, flags, stop_conditions, todo_items, source_files, gate_decisions, generated_at, raw_output_paths, verified_output_paths, report_path.

### Human report
File: `reports/generated/madison-innovation-positioning-patent-tracker-[DATE].md`
Reader: domain lead or human boss responsible for accepting the `Madison Innovation Positioning Patent Tracker` run.
Decision enabled: approve the run for the next phase, request source/schema fixes, or block live execution.
Sections: run summary, purpose, source inventory, inputs used, phase-gate results, steps completed, records seen, rejects, duplicates, flags, typed TODOs, human approvals, verified findings, inferred findings, decision recommendation.

## Stop Conditions

- Stop if assignee mapping is uncertain because company-level conclusions could be wrong.
- Stop if patent data is used to claim shipped product functionality.
- Stop if legal-sensitive innovation claims are requested without human approval.

## Snickerdoodle

### Run Commands
Full dialogic run:
`snickerdoodle run madison-innovation-positioning-patent-tracker --mode dialogic`

Sample mode (no live network calls, no writes):
`snickerdoodle run madison-innovation-positioning-patent-tracker --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Verify provenance | `snickerdoodle run madison-innovation-positioning-patent-tracker --step verify-provenance` | `--sample` `--no-write` |
| Ingest declared inputs | `snickerdoodle run madison-innovation-positioning-patent-tracker --step ingest-inputs` | `--sample` |
| Validate data shape | `snickerdoodle run madison-innovation-positioning-patent-tracker --step validate-data-shape` | `--sample` |
| Transform and quality check | `snickerdoodle run madison-innovation-positioning-patent-tracker --step transform-quality-check` | `--sample` |
| Run approved tools | `snickerdoodle run madison-innovation-positioning-patent-tracker --step run-approved-tools` | `--sample` `--no-write` |
| Produce human report | `snickerdoodle run madison-innovation-positioning-patent-tracker --step produce-human-report` | `--sample` `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - Source gate | `snickerdoodle gate madison-innovation-positioning-patent-tracker --gate 1 --decision approve --note "Sources checked"` |
| Gate 2 - Scope gate | `snickerdoodle gate madison-innovation-positioning-patent-tracker --gate 2 --decision approve --note "Scope and mode approved"` |
| Gate 3 - Data-shape gate | `snickerdoodle gate madison-innovation-positioning-patent-tracker --gate 3 --decision approve --note "Outputs parse"` |
| Gate 4 - Script-readiness gate | `snickerdoodle gate madison-innovation-positioning-patent-tracker --gate 4 --decision approve --note "Scripts ready or TODO DEV accepted"` |
| Gate 5 - Approval gate | `snickerdoodle gate madison-innovation-positioning-patent-tracker --gate 5 --decision approve --note "Live or sensitive actions approved"` |
| Gate 6 - Report gate | `snickerdoodle gate madison-innovation-positioning-patent-tracker --gate 6 --decision approve --note "Report and log complete"` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Verify provenance | `scripts/tools/madison-innovation-positioning-patent-tracker-verify-provenance.py` | tools |
| Ingest declared inputs | `scripts/ingest/madison-innovation-positioning-patent-tracker-ingest-inputs.py` | ingest |
| Validate data shape | `scripts/gigo/madison-innovation-positioning-patent-tracker-validate-data-shape.py` | gigo |
| Transform and quality check | `scripts/gigo/madison-innovation-positioning-patent-tracker-transform-quality-check.py` | gigo |
| Run approved tools | `scripts/tools/madison-innovation-positioning-patent-tracker-run-approved-tools.py` | tools |
| Produce human report | `scripts/tools/madison-innovation-positioning-patent-tracker-produce-human-report.py` | tools |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/madison-innovation-positioning-patent-tracker/` | JSON |
| Verified data | `data/verified/madison-innovation-positioning-patent-tracker/` | JSON |
| Agent log | `logs/madison-innovation-positioning-patent-tracker-[DATE].json` | JSON |
| Human report | `reports/generated/madison-innovation-positioning-patent-tracker-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

## Provenance

| Source | Verification command | Notes |
|---|---|---|
| `recipes/madison-innovation-positioning-patent-tracker.md` | `test -f "recipes/madison-innovation-positioning-patent-tracker.md"` | Current recipe file used as spec-first provenance. |

## Existing Recipe Notes Preserved For Implementation

### Extracted Notes

Translates patent and invention activity into brand-safe innovation-positioning signals so marketing teams can understand which claims about novelty, technical leadership, or product roadmap momentum are supportable.

1. Watchlist gate: assignee and company mappings are approved. Test: `python3 -m json.tool data/raw/madison-innovation-positioning-patent-tracker/company-watchlist.json`. Human capacity: [PF].
2. Patent source gate: patent data source and license are approved. Test: `rg -n "TODO:" recipes/madison-innovation-positioning-patent-tracker.md`. Human capacity: [PA].
3. Messaging gate: patent activity is not treated as product availability. Test: `snickerdoodle run madison-innovation-positioning-patent-tracker --mode dialogic --sample`. Human capacity: [IJ].

1. Step name: Ingest patent records. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/ingest/madison-innovation-positioning-patent-tracker-ingest-patent-records.py`
   Input: company watchlist and approved patent source.
   Output: raw JSON fields: patent_id, assignee, inventor, title, abstract, filing_date, publication_date, source_url.
   Where output goes: `data/raw/madison-innovation-positioning-patent-tracker/`.
2. Step name: Score innovation positioning. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/gigo/madison-innovation-positioning-patent-tracker-score-innovation-positioning.py`
   Input: raw patent records and innovation rubric.
   Output: verified JSON fields: patent_id, company, category, velocity_signal, novelty_signal, messaging_relevance, evidence_url, caution_flags.
   Where output goes: `data/verified/madison-innovation-positioning-patent-tracker/`.
3. Step name: Produce innovation positioning report. Labor: AI with Human review.
   Script called: `[TODO: DEV] Create scripts/tools/madison-innovation-positioning-patent-tracker-produce-innovation-positioning-report.py`
   Input: verified patent signals.
   Output: markdown sections: patent velocity, innovation themes, competitor signals, safe messaging claims, unsupported claims.
   Where output goes: `reports/generated/`.
