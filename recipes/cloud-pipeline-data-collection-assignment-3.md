# Cloud Pipeline Data Collection - Assignment 3

## Purpose

The Cloud Pipeline Data Collection - Assignment 3 workflow turns source material from 3 ingest node(s) into a locally auditable Madison intelligence artifact. It preserves the original n8n intent by separating collection, cleanup, analysis, and delivery so a human can verify brand, market, accessibility, persona, or public-signal claims before any live system action occurs. The converted recipe replaces hidden workflow side effects with explicit files, phase gates, and reviewable output contracts.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Original n8n workflow JSON | JSON | `pantry/manyaratanaka_312461_41801533_Tanaka_A3_Workflow.json` | Yes |
| Source 1: AWS Blog RSS | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |
| Source 2: Google Cloud RSS | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |
| Source 3: Cloud Jobs CSV (HTTP) | External or local source payload | node `n8n-nodes-base.httpRequest` | Yes |

## Phase Gates

1. Source gate: the original workflow JSON must exist at `pantry/manyaratanaka_312461_41801533_Tanaka_A3_Workflow.json`; verify with `test -f "pantry/manyaratanaka_312461_41801533_Tanaka_A3_Workflow.json"`. Human capacity: [TO].
2. Scope gate: the run must declare sample mode or approved live-source mode before ingest begins; verify by checking the run envelope in `logs/`. Human capacity: [PF].
3. Data-shape gate: every ingest output must parse as JSON before GIGO or tool scripts run; verify with `python3 -m json.tool <path>`. Human capacity: [PA].
4. Cleanup gate: GIGO outputs must include `record_count` and no empty required source records; verify by reading the generated `data/verified/cloud-pipeline-data-collection-assignment-3/` files. Human capacity: [IJ].
5. Live-action gate: any HTTP, file export, email, dashboard, model, or database action remains a local handoff until explicitly approved. Human capacity: [EI].
6. Report gate: every run must leave a log and a report linkable to the source JSON. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI. Script called: none. Input: `pantry/manyaratanaka_312461_41801533_Tanaka_A3_Workflow.json`. Output: provenance check. Where output goes: `logs/`.
2. Step name: Source 1: AWS Blog RSS. Labor: AI. Script called: `scripts/ingest/cloud-pipeline-data-collection-assignment-3__source-1-aws-blog-rss.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
3. Step name: Source 2: Google Cloud RSS. Labor: AI. Script called: `scripts/ingest/cloud-pipeline-data-collection-assignment-3__source-2-google-cloud-rss.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
4. Step name: Source 3: Cloud Jobs CSV (HTTP). Labor: AI. Script called: `scripts/ingest/cloud-pipeline-data-collection-assignment-3__source-3-cloud-jobs-csv-http.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
5. Step name: Clean & Standardize. Labor: AI. Script called: `scripts/gigo/cloud-pipeline-data-collection-assignment-3__clean-and-standardize.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
6. Step name: Quality Check. Labor: AI. Script called: `scripts/gigo/cloud-pipeline-data-collection-assignment-3__quality-check.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
7. Step name: Save to CSV. Labor: AI. Script called: `scripts/tools/cloud-pipeline-data-collection-assignment-3__save-to-csv.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
8. Step name: Write File to Disk. Labor: AI. Script called: `scripts/tools/cloud-pipeline-data-collection-assignment-3__write-file-to-disk.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
9. Step name: Produce human report. Labor: AI. Script called: none; conductor fills `reports/templates/cloud-pipeline-data-collection-assignment-3.md`. Input: run log and verified outputs. Output: concise decision report. Where output goes: `reports/generated/`.

## Output Contract

### Agent output

The agent output goes to `logs/cloud-pipeline-data-collection-assignment-3-[DATE].json` and contains `workflow`, `workflow_slug`, `source_json`, `mode`, `steps_completed`, `records_seen`, `handoffs`, `flags`, `stop_conditions`, and `generated_at`.

### Human report

The human report goes to `reports/generated/cloud-pipeline-data-collection-assignment-3-[DATE].md`. It surfaces the verified signal, any missing or malformed source data, the decisions enabled by the workflow, and which live actions still require approval.

## Stop Conditions

- Stop if `pantry/manyaratanaka_312461_41801533_Tanaka_A3_Workflow.json` is missing or cannot be parsed.
- Stop if a live source, model, database, email, dashboard, or file export is requested without explicit approval.
- Stop if an ingest result cannot be represented as JSON under `data/raw/`.
- Stop if GIGO scripts produce zero records when the source should contain records.
- Stop if generated reports would expose credentials, private tokens, or unapproved personal data.
- Stop if the final decision claim cannot be traced to source, verified data, or a logged handoff.

## Provenance

Original workflow JSON: `pantry/manyaratanaka_312461_41801533_Tanaka_A3_Workflow.json`
