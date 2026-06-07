# Madison Brand Consistency Contradiction Checker

## Purpose

Compares brand claims across websites, ads, press releases, decks, social posts, and investor-facing materials so a brand owner can find contradictions before customers, regulators, or partners do.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Brand claim corpus | JSON/Markdown | [TODO: DATA SOURCE] Approved website, ad, press, deck, and social claim files. | Yes |
| Claim taxonomy | JSON | [TODO: DEFINE] Define product, price, availability, ESG, privacy, safety, and performance claim types. | Yes |
| Contradiction rubric | JSON | [TODO: DEFINE] Define direct conflict, stale claim, scope mismatch, and unsupported claim. | Yes |
| Mycroft adaptation source | Markdown | `/Users/bear/Documents/CoWork/bear-textbooks/books/mycroft/recipes/contradiction-detection-agent.md` | No |

## Phase Gates

1. Corpus gate: all claim sources are approved and current. Test: `rg -n "TODO:" recipes/madison-brand-consistency-contradiction-checker.md`. Human capacity: [PF].
2. Taxonomy gate: claim types are defined before extraction. Test: `python3 -m json.tool data/raw/madison-brand-consistency-contradiction-checker/claim-taxonomy.json`. Human capacity: [IJ].
3. Sample gate: sample mode produces local contradiction records only. Test: `snickerdoodle run madison-brand-consistency-contradiction-checker --mode dialogic --sample`. Human capacity: [TO].

## Steps

1. Step name: Ingest brand claims. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/ingest/madison-brand-consistency-contradiction-checker__ingest-brand-claims.py`
   Input: approved claim corpus.
   Output: raw JSON fields: source_id, source_type, title, url_or_path, claim_text, collected_at.
   Where output goes: `data/raw/madison-brand-consistency-contradiction-checker/`.
2. Step name: Detect contradictions. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/gigo/madison-brand-consistency-contradiction-checker__detect-contradictions.py`
   Input: raw claim records, claim taxonomy, contradiction rubric.
   Output: verified JSON fields: contradiction_id, claim_a, claim_b, conflict_type, severity, evidence_refs, recommended_owner.
   Where output goes: `data/verified/madison-brand-consistency-contradiction-checker/`.
3. Step name: Produce contradiction report. Labor: AI with Human review.
   Script called: `[TODO: DEV] Create scripts/tools/madison-brand-consistency-contradiction-checker__produce-contradiction-report.py`
   Input: verified contradiction records.
   Output: markdown sections: high-risk contradictions, stale claims, unsupported claims, source links, remediation owner.
   Where output goes: `reports/generated/`.

## Output Contract

### Agent output
File: `logs/madison-brand-consistency-contradiction-checker-[DATE].json`
Fields: `workflow`, `run_id`, `mode`, `steps_completed`, `records_seen`, `rejects`, `duplicates`, `flags`, `stop_conditions`, `todo_items`, `source_files`, `gate_decisions`, `generated_at`.

### Human report
File: `reports/generated/madison-brand-consistency-contradiction-checker-[DATE].md`
Reader: brand governance lead.
Decision enabled: decide which claims must be corrected, retired, escalated to legal, or approved for campaign use.
Sections: Claim corpus summary, contradiction table, severity, evidence references, remediation owner, approval blockers.

## Stop Conditions

- Stop if claim sources are not approved because the checker could audit drafts as live claims.
- Stop if contradiction rubric is undefined because severity would be subjective.
- Stop if legal or public correction actions are requested without human approval.

## Snickerdoodle

### Run Commands
Full dialogic run: `snickerdoodle run madison-brand-consistency-contradiction-checker --mode dialogic`
Sample mode: `snickerdoodle run madison-brand-consistency-contradiction-checker --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Ingest brand claims | `snickerdoodle run madison-brand-consistency-contradiction-checker --step ingest-brand-claims` | `--sample` |
| Detect contradictions | `snickerdoodle run madison-brand-consistency-contradiction-checker --step detect-contradictions` |  |
| Produce contradiction report | `snickerdoodle run madison-brand-consistency-contradiction-checker --step produce-contradiction-report` | `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - corpus approval | `snickerdoodle gate madison-brand-consistency-contradiction-checker --gate 1 --decision approve --note "..."` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Ingest brand claims | `[TODO: DEV] scripts/ingest/madison-brand-consistency-contradiction-checker__ingest-brand-claims.py` | ingest |
| Detect contradictions | `[TODO: DEV] scripts/gigo/madison-brand-consistency-contradiction-checker__detect-contradictions.py` | gigo |
| Produce contradiction report | `[TODO: DEV] scripts/tools/madison-brand-consistency-contradiction-checker__produce-contradiction-report.py` | tool |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/madison-brand-consistency-contradiction-checker/` | JSON |
| Verified data | `data/verified/madison-brand-consistency-contradiction-checker/` | JSON |
| Agent log | `logs/madison-brand-consistency-contradiction-checker-[DATE].json` | JSON |
| Human report | `reports/generated/madison-brand-consistency-contradiction-checker-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

