# Singh Vaibhav A3 - Intelligence Agent Data Collection

## Purpose

The Singh Vaibhav A3 - Intelligence Agent Data Collection workflow turns source material from 6 ingest node(s) into a locally auditable Madison intelligence artifact. It preserves the original n8n intent by separating collection, cleanup, analysis, and delivery so a human can verify brand, market, accessibility, persona, or public-signal claims before any live system action occurs. The converted recipe replaces hidden workflow side effects with explicit files, phase gates, and reviewable output contracts.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Original n8n workflow JSON | JSON | `pantry/singhvaibhav_351998_41799855_Singh_Vaibhav_A3_workflow.json` | Yes |
| RSS - TechCrunch | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |
| RSS - Ars Technica | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |
| RSS - The Verge | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |
| RSS - Google News (Brand) | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |
| HTTP - NewsAPI | External or local source payload | node `n8n-nodes-base.httpRequest` | Yes |
| HTTP - HuggingFace | External or local source payload | node `n8n-nodes-base.httpRequest` | Yes |

## Phase Gates

1. Source gate: the original workflow JSON must exist at `pantry/singhvaibhav_351998_41799855_Singh_Vaibhav_A3_workflow.json`; verify with `test -f "pantry/singhvaibhav_351998_41799855_Singh_Vaibhav_A3_workflow.json"`. Human capacity: [TO].
2. Scope gate: the run must declare sample mode or approved live-source mode before ingest begins; verify by checking the run envelope in `logs/`. Human capacity: [PF].
3. Data-shape gate: every ingest output must parse as JSON before GIGO or tool scripts run; verify with `python3 -m json.tool <path>`. Human capacity: [PA].
4. Cleanup gate: GIGO outputs must include `record_count` and no empty required source records; verify by reading the generated `data/verified/singh-vaibhav-a3-intelligence-agent-data-collection/` files. Human capacity: [IJ].
5. Live-action gate: any HTTP, file export, email, dashboard, model, or database action remains a local handoff until explicitly approved. Human capacity: [EI].
6. Report gate: every run must leave a log and a report linkable to the source JSON. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI. Script called: none. Input: `pantry/singhvaibhav_351998_41799855_Singh_Vaibhav_A3_workflow.json`. Output: provenance check. Where output goes: `logs/`.
2. Step name: RSS - TechCrunch. Labor: AI. Script called: `scripts/ingest/singh-vaibhav-a3-intelligence-agent-data-collection__rss-techcrunch.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
3. Step name: RSS - Ars Technica. Labor: AI. Script called: `scripts/ingest/singh-vaibhav-a3-intelligence-agent-data-collection__rss-ars-technica.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
4. Step name: RSS - The Verge. Labor: AI. Script called: `scripts/ingest/singh-vaibhav-a3-intelligence-agent-data-collection__rss-the-verge.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
5. Step name: RSS - Google News (Brand). Labor: AI. Script called: `scripts/ingest/singh-vaibhav-a3-intelligence-agent-data-collection__rss-google-news-brand.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
6. Step name: HTTP - NewsAPI. Labor: AI. Script called: `scripts/ingest/singh-vaibhav-a3-intelligence-agent-data-collection__http-newsapi.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
7. Step name: HTTP - HuggingFace. Labor: AI. Script called: `scripts/ingest/singh-vaibhav-a3-intelligence-agent-data-collection__http-huggingface.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
8. Step name: Norm TechCrunch. Labor: AI. Script called: `scripts/tools/singh-vaibhav-a3-intelligence-agent-data-collection__norm-techcrunch.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
9. Step name: Norm Ars Technica. Labor: AI. Script called: `scripts/tools/singh-vaibhav-a3-intelligence-agent-data-collection__norm-ars-technica.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
10. Step name: Norm The Verge. Labor: AI. Script called: `scripts/tools/singh-vaibhav-a3-intelligence-agent-data-collection__norm-the-verge.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
11. Step name: Norm Google News. Labor: AI. Script called: `scripts/tools/singh-vaibhav-a3-intelligence-agent-data-collection__norm-google-news.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
12. Step name: Norm NewsAPI. Labor: AI. Script called: `scripts/tools/singh-vaibhav-a3-intelligence-agent-data-collection__norm-newsapi.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
13. Step name: Norm HuggingFace. Labor: AI. Script called: `scripts/gigo/singh-vaibhav-a3-intelligence-agent-data-collection__norm-huggingface.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
14. Step name: Deduplicate & Validate. Labor: AI. Script called: `scripts/gigo/singh-vaibhav-a3-intelligence-agent-data-collection__deduplicate-and-validate.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
15. Step name: Convert to CSV. Labor: AI. Script called: `scripts/tools/singh-vaibhav-a3-intelligence-agent-data-collection__convert-to-csv.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
16. Step name: Save CSV. Labor: AI. Script called: `scripts/tools/singh-vaibhav-a3-intelligence-agent-data-collection__save-csv.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
17. Step name: Produce human report. Labor: AI. Script called: none; conductor fills `reports/templates/singh-vaibhav-a3-intelligence-agent-data-collection.md`. Input: run log and verified outputs. Output: concise decision report. Where output goes: `reports/generated/`.

## Output Contract

### Agent output

The agent output goes to `logs/singh-vaibhav-a3-intelligence-agent-data-collection-[DATE].json` and contains `workflow`, `workflow_slug`, `source_json`, `mode`, `steps_completed`, `records_seen`, `handoffs`, `flags`, `stop_conditions`, and `generated_at`.

### Human report

The human report goes to `reports/generated/singh-vaibhav-a3-intelligence-agent-data-collection-[DATE].md`. It surfaces the verified signal, any missing or malformed source data, the decisions enabled by the workflow, and which live actions still require approval.

## Stop Conditions

- Stop if `pantry/singhvaibhav_351998_41799855_Singh_Vaibhav_A3_workflow.json` is missing or cannot be parsed.
- Stop if a live source, model, database, email, dashboard, or file export is requested without explicit approval.
- Stop if an ingest result cannot be represented as JSON under `data/raw/`.
- Stop if GIGO scripts produce zero records when the source should contain records.
- Stop if generated reports would expose credentials, private tokens, or unapproved personal data.
- Stop if the final decision claim cannot be traced to source, verified data, or a logged handoff.

## Provenance

Original workflow JSON: `pantry/singhvaibhav_351998_41799855_Singh_Vaibhav_A3_workflow.json`
