# Madison Persona Pipeline A3

## Purpose

The Madison Persona Pipeline A3 workflow turns source material from 5 ingest node(s) into a locally auditable Madison intelligence artifact. It preserves the original n8n intent by separating collection, cleanup, analysis, and delivery so a human can verify brand, market, accessibility, persona, or public-signal claims before any live system action occurs. The converted recipe replaces hidden workflow side effects with explicit files, phase gates, and reviewable output contracts.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Original n8n workflow JSON | JSON | `pantry/krishnamoorthyraksha_333078_41797107_KrishnaMoorthy_Raksha_A3_Workflow-1.json` | Yes |
| HTTP Request: CDC | External or local source payload | node `n8n-nodes-base.httpRequest` | Yes |
| HTTP Request: HuggingFace | External or local source payload | node `n8n-nodes-base.httpRequest` | Yes |
| HTTP Request: RSS Feed | External or local source payload | node `n8n-nodes-base.httpRequest` | Yes |
| Read/Write Files from Disk | External or local source payload | node `n8n-nodes-base.readWriteFile` | Yes |
| Extract from File | External or local source payload | node `n8n-nodes-base.extractFromFile` | Yes |

## Phase Gates

1. Source gate: the original workflow JSON must exist at `pantry/krishnamoorthyraksha_333078_41797107_KrishnaMoorthy_Raksha_A3_Workflow-1.json`; verify with `test -f "pantry/krishnamoorthyraksha_333078_41797107_KrishnaMoorthy_Raksha_A3_Workflow-1.json"`. Human capacity: [TO].
2. Scope gate: the run must declare sample mode or approved live-source mode before ingest begins; verify by checking the run envelope in `logs/`. Human capacity: [PF].
3. Data-shape gate: every ingest output must parse as JSON before GIGO or tool scripts run; verify with `python3 -m json.tool <path>`. Human capacity: [PA].
4. Cleanup gate: GIGO outputs must include `record_count` and no empty required source records; verify by reading the generated `data/verified/madison-persona-pipeline-a3/` files. Human capacity: [IJ].
5. Live-action gate: any HTTP, file export, email, dashboard, model, or database action remains a local handoff until explicitly approved. Human capacity: [EI].
6. Report gate: every run must leave a log and a report linkable to the source JSON. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI. Script called: none. Input: `pantry/krishnamoorthyraksha_333078_41797107_KrishnaMoorthy_Raksha_A3_Workflow-1.json`. Output: provenance check. Where output goes: `logs/`.
2. Step name: HTTP Request: CDC. Labor: AI. Script called: `scripts/ingest/madison-persona-pipeline-a3__http-request-cdc.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
3. Step name: Code: Parse CDC. Labor: AI. Script called: `scripts/gigo/madison-persona-pipeline-a3__code-parse-cdc.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
4. Step name: Code: Parse Kaggle. Labor: AI. Script called: `scripts/gigo/madison-persona-pipeline-a3__code-parse-kaggle.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
5. Step name: HTTP Request: HuggingFace. Labor: AI. Script called: `scripts/ingest/madison-persona-pipeline-a3__http-request-huggingface.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
6. Step name: Code: Parse HuggingFace. Labor: AI. Script called: `scripts/gigo/madison-persona-pipeline-a3__code-parse-huggingface.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
7. Step name: HTTP Request: RSS Feed. Labor: AI. Script called: `scripts/ingest/madison-persona-pipeline-a3__http-request-rss-feed.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
8. Step name: Code: Parse RSS. Labor: AI. Script called: `scripts/gigo/madison-persona-pipeline-a3__code-parse-rss.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
9. Step name: Code: Merge + Quality Check. Labor: AI. Script called: `scripts/gigo/madison-persona-pipeline-a3__code-merge-quality-check.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
10. Step name: Code: Summary Report. Labor: AI. Script called: `scripts/gigo/madison-persona-pipeline-a3__code-summary-report.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
11. Step name: Read/Write Files from Disk. Labor: AI. Script called: `scripts/ingest/madison-persona-pipeline-a3__read-write-files-from-disk.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
12. Step name: Extract from File. Labor: AI. Script called: `scripts/ingest/madison-persona-pipeline-a3__extract-from-file.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
13. Step name: Code: Generate HTML Report. Labor: AI. Script called: `scripts/gigo/madison-persona-pipeline-a3__code-generate-html-report.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
14. Step name: Read/Write Files from Disk1. Labor: AI. Script called: `scripts/tools/madison-persona-pipeline-a3__read-write-files-from-disk1.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
15. Step name: Produce human report. Labor: AI. Script called: none; conductor fills `reports/templates/madison-persona-pipeline-a3.md`. Input: run log and verified outputs. Output: concise decision report. Where output goes: `reports/generated/`.

## Output Contract

### Agent output

The agent output goes to `logs/madison-persona-pipeline-a3-[DATE].json` and contains `workflow`, `workflow_slug`, `source_json`, `mode`, `steps_completed`, `records_seen`, `handoffs`, `flags`, `stop_conditions`, and `generated_at`.

### Human report

The human report goes to `reports/generated/madison-persona-pipeline-a3-[DATE].md`. It surfaces the verified signal, any missing or malformed source data, the decisions enabled by the workflow, and which live actions still require approval.

## Stop Conditions

- Stop if `pantry/krishnamoorthyraksha_333078_41797107_KrishnaMoorthy_Raksha_A3_Workflow-1.json` is missing or cannot be parsed.
- Stop if a live source, model, database, email, dashboard, or file export is requested without explicit approval.
- Stop if an ingest result cannot be represented as JSON under `data/raw/`.
- Stop if GIGO scripts produce zero records when the source should contain records.
- Stop if generated reports would expose credentials, private tokens, or unapproved personal data.
- Stop if the final decision claim cannot be traced to source, verified data, or a logged handoff.

## Provenance

Original workflow JSON: `pantry/krishnamoorthyraksha_333078_41797107_KrishnaMoorthy_Raksha_A3_Workflow-1.json`
