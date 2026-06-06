# Sentinel A3 DataPipeline

## Purpose

The Sentinel A3 DataPipeline workflow turns source material from 4 ingest node(s) into a locally auditable Madison intelligence artifact. It preserves the original n8n intent by separating collection, cleanup, analysis, and delivery so a human can verify brand, market, accessibility, persona, or public-signal claims before any live system action occurs. The converted recipe replaces hidden workflow side effects with explicit files, phase gates, and reviewable output contracts.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Original n8n workflow JSON | JSON | `pantry/ranahammad_320831_41799387_Rana_Hammad_A3_Workflow.json` | Yes |
| Read/Write Files from Disk | External or local source payload | node `n8n-nodes-base.readWriteFile` | Yes |
| Extract from File | External or local source payload | node `n8n-nodes-base.extractFromFile` | Yes |
| CISA RSS Read | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |
| HTTP Request | External or local source payload | node `n8n-nodes-base.httpRequest` | Yes |

## Phase Gates

1. Source gate: the original workflow JSON must exist at `pantry/ranahammad_320831_41799387_Rana_Hammad_A3_Workflow.json`; verify with `test -f "pantry/ranahammad_320831_41799387_Rana_Hammad_A3_Workflow.json"`. Human capacity: [TO].
2. Scope gate: the run must declare sample mode or approved live-source mode before ingest begins; verify by checking the run envelope in `logs/`. Human capacity: [PF].
3. Data-shape gate: every ingest output must parse as JSON before GIGO or tool scripts run; verify with `python3 -m json.tool <path>`. Human capacity: [PA].
4. Cleanup gate: GIGO outputs must include `record_count` and no empty required source records; verify by reading the generated `data/verified/sentinel-a3-datapipeline/` files. Human capacity: [IJ].
5. Live-action gate: any HTTP, file export, email, dashboard, model, or database action remains a local handoff until explicitly approved. Human capacity: [EI].
6. Report gate: every run must leave a log and a report linkable to the source JSON. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI. Script called: none. Input: `pantry/ranahammad_320831_41799387_Rana_Hammad_A3_Workflow.json`. Output: provenance check. Where output goes: `logs/`.
2. Step name: Read/Write Files from Disk. Labor: AI. Script called: `scripts/ingest/sentinel-a3-datapipeline__read-write-files-from-disk.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
3. Step name: Extract from File. Labor: AI. Script called: `scripts/ingest/sentinel-a3-datapipeline__extract-from-file.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
4. Step name: Code in JavaScript. Labor: AI. Script called: `scripts/gigo/sentinel-a3-datapipeline__code-in-javascript.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
5. Step name: Convert to File. Labor: AI. Script called: `scripts/tools/sentinel-a3-datapipeline__convert-to-file.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
6. Step name: Read/Write Files from Disk1. Labor: AI. Script called: `scripts/tools/sentinel-a3-datapipeline__read-write-files-from-disk1.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
7. Step name: CISA RSS Read. Labor: AI. Script called: `scripts/ingest/sentinel-a3-datapipeline__cisa-rss-read.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
8. Step name: Code in JavaScript1. Labor: AI. Script called: `scripts/gigo/sentinel-a3-datapipeline__code-in-javascript1.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
9. Step name: Convert to File1. Labor: AI. Script called: `scripts/tools/sentinel-a3-datapipeline__convert-to-file1.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
10. Step name: Read/Write Files from Disk2. Labor: AI. Script called: `scripts/tools/sentinel-a3-datapipeline__read-write-files-from-disk2.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
11. Step name: HTTP Request. Labor: AI. Script called: `scripts/ingest/sentinel-a3-datapipeline__http-request.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
12. Step name: Code in JavaScript2. Labor: AI. Script called: `scripts/gigo/sentinel-a3-datapipeline__code-in-javascript2.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
13. Step name: Convert to File2. Labor: AI. Script called: `scripts/tools/sentinel-a3-datapipeline__convert-to-file2.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
14. Step name: Read/Write Files from Disk3. Labor: AI. Script called: `scripts/tools/sentinel-a3-datapipeline__read-write-files-from-disk3.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
15. Step name: Code in JavaScript3. Labor: AI. Script called: `scripts/gigo/sentinel-a3-datapipeline__code-in-javascript3.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
16. Step name: Code in JavaScript4. Labor: AI. Script called: `scripts/gigo/sentinel-a3-datapipeline__code-in-javascript4.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
17. Step name: Convert to File3. Labor: AI. Script called: `scripts/tools/sentinel-a3-datapipeline__convert-to-file3.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
18. Step name: Read/Write Files from Disk4. Labor: AI. Script called: `scripts/tools/sentinel-a3-datapipeline__read-write-files-from-disk4.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
19. Step name: Convert to File4. Labor: AI. Script called: `scripts/tools/sentinel-a3-datapipeline__convert-to-file4.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
20. Step name: Read/Write Files from Disk5. Labor: AI. Script called: `scripts/tools/sentinel-a3-datapipeline__read-write-files-from-disk5.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
21. Step name: Produce human report. Labor: AI. Script called: none; conductor fills `reports/templates/sentinel-a3-datapipeline.md`. Input: run log and verified outputs. Output: concise decision report. Where output goes: `reports/generated/`.

## Output Contract

### Agent output

The agent output goes to `logs/sentinel-a3-datapipeline-[DATE].json` and contains `workflow`, `workflow_slug`, `source_json`, `mode`, `steps_completed`, `records_seen`, `handoffs`, `flags`, `stop_conditions`, and `generated_at`.

### Human report

The human report goes to `reports/generated/sentinel-a3-datapipeline-[DATE].md`. It surfaces the verified signal, any missing or malformed source data, the decisions enabled by the workflow, and which live actions still require approval.

## Stop Conditions

- Stop if `pantry/ranahammad_320831_41799387_Rana_Hammad_A3_Workflow.json` is missing or cannot be parsed.
- Stop if a live source, model, database, email, dashboard, or file export is requested without explicit approval.
- Stop if an ingest result cannot be represented as JSON under `data/raw/`.
- Stop if GIGO scripts produce zero records when the source should contain records.
- Stop if generated reports would expose credentials, private tokens, or unapproved personal data.
- Stop if the final decision claim cannot be traced to source, verified data, or a logged handoff.

## Provenance

Original workflow JSON: `pantry/ranahammad_320831_41799387_Rana_Hammad_A3_Workflow.json`
