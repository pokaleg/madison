# Zu Xinchen A3 Workflow

## Purpose

The Zu Xinchen A3 Workflow workflow turns source material from 6 ingest node(s) into a locally auditable Madison intelligence artifact. It preserves the original n8n intent by separating collection, cleanup, analysis, and delivery so a human can verify brand, market, accessibility, persona, or public-signal claims before any live system action occurs. The converted recipe replaces hidden workflow side effects with explicit files, phase gates, and reviewable output contracts.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Original n8n workflow JSON | JSON | `pantry/zuxinchen_405407_41801846_Zu_Xinchen_A3_Workflow.json` | Yes |
| RSS Read | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |
| RSS Read1 | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |
| RSS Read2 | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |
| RSS Read3 | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |
| RSS Read4 | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |
| RSS Read5 | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |

## Phase Gates

1. Source gate: the original workflow JSON must exist at `pantry/zuxinchen_405407_41801846_Zu_Xinchen_A3_Workflow.json`; verify with `test -f "pantry/zuxinchen_405407_41801846_Zu_Xinchen_A3_Workflow.json"`. Human capacity: [TO].
2. Scope gate: the run must declare sample mode or approved live-source mode before ingest begins; verify by checking the run envelope in `logs/`. Human capacity: [PF].
3. Data-shape gate: every ingest output must parse as JSON before GIGO or tool scripts run; verify with `python3 -m json.tool <path>`. Human capacity: [PA].
4. Cleanup gate: GIGO outputs must include `record_count` and no empty required source records; verify by reading the generated `data/verified/zu-xinchen-a3-workflow/` files. Human capacity: [IJ].
5. Live-action gate: any HTTP, file export, email, dashboard, model, or database action remains a local handoff until explicitly approved. Human capacity: [EI].
6. Report gate: every run must leave a log and a report linkable to the source JSON. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI. Script called: none. Input: `pantry/zuxinchen_405407_41801846_Zu_Xinchen_A3_Workflow.json`. Output: provenance check. Where output goes: `logs/`.
2. Step name: RSS Read. Labor: AI. Script called: `scripts/ingest/zu-xinchen-a3-workflow__rss-read.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
3. Step name: RSS Read1. Labor: AI. Script called: `scripts/ingest/zu-xinchen-a3-workflow__rss-read1.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
4. Step name: RSS Read2. Labor: AI. Script called: `scripts/ingest/zu-xinchen-a3-workflow__rss-read2.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
5. Step name: Edit Fields. Labor: AI. Script called: `scripts/gigo/zu-xinchen-a3-workflow__edit-fields.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
6. Step name: Convert to File. Labor: AI. Script called: `scripts/tools/zu-xinchen-a3-workflow__convert-to-file.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
7. Step name: RSS Read3. Labor: AI. Script called: `scripts/ingest/zu-xinchen-a3-workflow__rss-read3.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
8. Step name: RSS Read4. Labor: AI. Script called: `scripts/ingest/zu-xinchen-a3-workflow__rss-read4.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
9. Step name: RSS Read5. Labor: AI. Script called: `scripts/ingest/zu-xinchen-a3-workflow__rss-read5.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
10. Step name: Produce human report. Labor: AI. Script called: none; conductor fills `reports/templates/zu-xinchen-a3-workflow.md`. Input: run log and verified outputs. Output: concise decision report. Where output goes: `reports/generated/`.

## Output Contract

### Agent output

The agent output goes to `logs/zu-xinchen-a3-workflow-[DATE].json` and contains `workflow`, `workflow_slug`, `source_json`, `mode`, `steps_completed`, `records_seen`, `handoffs`, `flags`, `stop_conditions`, and `generated_at`.

### Human report

The human report goes to `reports/generated/zu-xinchen-a3-workflow-[DATE].md`. It surfaces the verified signal, any missing or malformed source data, the decisions enabled by the workflow, and which live actions still require approval.

## Stop Conditions

- Stop if `pantry/zuxinchen_405407_41801846_Zu_Xinchen_A3_Workflow.json` is missing or cannot be parsed.
- Stop if a live source, model, database, email, dashboard, or file export is requested without explicit approval.
- Stop if an ingest result cannot be represented as JSON under `data/raw/`.
- Stop if GIGO scripts produce zero records when the source should contain records.
- Stop if generated reports would expose credentials, private tokens, or unapproved personal data.
- Stop if the final decision claim cannot be traced to source, verified data, or a logged handoff.

## Provenance

Original workflow JSON: `pantry/zuxinchen_405407_41801846_Zu_Xinchen_A3_Workflow.json`
