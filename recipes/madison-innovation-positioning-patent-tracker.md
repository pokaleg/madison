# Madison Innovation Positioning Patent Tracker

## Purpose

Translates patent and invention activity into brand-safe innovation-positioning signals so marketing teams can understand which claims about novelty, technical leadership, or product roadmap momentum are supportable.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Company watchlist | JSON | [TODO: DATA SOURCE] Approved companies, subsidiaries, inventors, and assignees. | Yes |
| Patent records | JSON/API | [TODO: DATA SOURCE] USPTO, Google Patents export, Lens, or approved local patent dataset. | Yes |
| Innovation rubric | JSON | [TODO: DEFINE] Define novelty, velocity, category fit, defensibility, and messaging relevance. | Yes |
| Mycroft adaptation source | Markdown | `/Users/bear/Documents/CoWork/bear-textbooks/books/mycroft/recipes/patent-filing-velocity-tracker.md` | No |

## Phase Gates

1. Watchlist gate: assignee and company mappings are approved. Test: `python3 -m json.tool data/raw/madison-innovation-positioning-patent-tracker/company-watchlist.json`. Human capacity: [PF].
2. Patent source gate: patent data source and license are approved. Test: `rg -n "TODO:" recipes/madison-innovation-positioning-patent-tracker.md`. Human capacity: [PA].
3. Messaging gate: patent activity is not treated as product availability. Test: `snickerdoodle run madison-innovation-positioning-patent-tracker --mode dialogic --sample`. Human capacity: [IJ].

## Steps

1. Step name: Ingest patent records. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/ingest/madison-innovation-positioning-patent-tracker__ingest-patent-records.py`
   Input: company watchlist and approved patent source.
   Output: raw JSON fields: patent_id, assignee, inventor, title, abstract, filing_date, publication_date, source_url.
   Where output goes: `data/raw/madison-innovation-positioning-patent-tracker/`.
2. Step name: Score innovation positioning. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/gigo/madison-innovation-positioning-patent-tracker__score-innovation-positioning.py`
   Input: raw patent records and innovation rubric.
   Output: verified JSON fields: patent_id, company, category, velocity_signal, novelty_signal, messaging_relevance, evidence_url, caution_flags.
   Where output goes: `data/verified/madison-innovation-positioning-patent-tracker/`.
3. Step name: Produce innovation positioning report. Labor: AI with Human review.
   Script called: `[TODO: DEV] Create scripts/tools/madison-innovation-positioning-patent-tracker__produce-innovation-positioning-report.py`
   Input: verified patent signals.
   Output: markdown sections: patent velocity, innovation themes, competitor signals, safe messaging claims, unsupported claims.
   Where output goes: `reports/generated/`.

## Output Contract

### Agent output
File: `logs/madison-innovation-positioning-patent-tracker-[DATE].json`
Fields: `workflow`, `run_id`, `mode`, `steps_completed`, `records_seen`, `rejects`, `duplicates`, `flags`, `stop_conditions`, `todo_items`, `source_files`, `gate_decisions`, `generated_at`.

### Human report
File: `reports/generated/madison-innovation-positioning-patent-tracker-[DATE].md`
Reader: product marketing or innovation communications lead.
Decision enabled: decide which innovation claims are supportable, which need legal review, and which should stay internal.
Sections: Assignee coverage, patent themes, velocity signals, competitor signals, messaging-safe claims, caution flags.

## Stop Conditions

- Stop if assignee mapping is uncertain because company-level conclusions could be wrong.
- Stop if patent data is used to claim shipped product functionality.
- Stop if legal-sensitive innovation claims are requested without human approval.

## Snickerdoodle

### Run Commands
Full dialogic run: `snickerdoodle run madison-innovation-positioning-patent-tracker --mode dialogic`
Sample mode: `snickerdoodle run madison-innovation-positioning-patent-tracker --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Ingest patent records | `snickerdoodle run madison-innovation-positioning-patent-tracker --step ingest-patent-records` | `--sample` |
| Score innovation positioning | `snickerdoodle run madison-innovation-positioning-patent-tracker --step score-innovation-positioning` |  |
| Produce innovation positioning report | `snickerdoodle run madison-innovation-positioning-patent-tracker --step produce-innovation-positioning-report` | `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - patent source approval | `snickerdoodle gate madison-innovation-positioning-patent-tracker --gate 1 --decision approve --note "..."` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Ingest patent records | `[TODO: DEV] scripts/ingest/madison-innovation-positioning-patent-tracker__ingest-patent-records.py` | ingest |
| Score innovation positioning | `[TODO: DEV] scripts/gigo/madison-innovation-positioning-patent-tracker__score-innovation-positioning.py` | gigo |
| Produce innovation positioning report | `[TODO: DEV] scripts/tools/madison-innovation-positioning-patent-tracker__produce-innovation-positioning-report.py` | tool |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/madison-innovation-positioning-patent-tracker/` | JSON |
| Verified data | `data/verified/madison-innovation-positioning-patent-tracker/` | JSON |
| Agent log | `logs/madison-innovation-positioning-patent-tracker-[DATE].json` | JSON |
| Human report | `reports/generated/madison-innovation-positioning-patent-tracker-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

