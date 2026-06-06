# Accessibility Monitor - Data Collection Pipeline

## Purpose

The Accessibility Monitor - Data Collection Pipeline workflow turns source material from 3 ingest node(s) into a locally auditable Madison intelligence artifact. It preserves the original n8n intent by separating collection, cleanup, analysis, and delivery so a human can verify brand, market, accessibility, persona, or public-signal claims before any live system action occurs. The converted recipe replaces hidden workflow side effects with explicit files, phase gates, and reviewable output contracts.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| Original n8n workflow JSON | JSON | `pantry/singhkanishknagendra_348738_41749683_Singh_Kanishk_A3_Workflow.json` | Yes |
| W3C WCAG JSON - Success Criteria | External or local source payload | node `n8n-nodes-base.httpRequest` | Yes |
| RSS - WebAIM Blog | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |
| RSS - A11y Project | External or local source payload | node `n8n-nodes-base.rssFeedRead` | Yes |

## Phase Gates

1. Source gate: the original workflow JSON must exist at `pantry/singhkanishknagendra_348738_41749683_Singh_Kanishk_A3_Workflow.json`; verify with `test -f "pantry/singhkanishknagendra_348738_41749683_Singh_Kanishk_A3_Workflow.json"`. Human capacity: [TO].
2. Scope gate: the run must declare sample mode or approved live-source mode before ingest begins; verify by checking the run envelope in `logs/`. Human capacity: [PF].
3. Data-shape gate: every ingest output must parse as JSON before GIGO or tool scripts run; verify with `python3 -m json.tool <path>`. Human capacity: [PA].
4. Cleanup gate: GIGO outputs must include `record_count` and no empty required source records; verify by reading the generated `data/verified/accessibility-monitor-data-collection-pipeline/` files. Human capacity: [IJ].
5. Live-action gate: any HTTP, file export, email, dashboard, model, or database action remains a local handoff until explicitly approved. Human capacity: [EI].
6. Report gate: every run must leave a log and a report linkable to the source JSON. Human capacity: [TO].

## Steps

1. Step name: Verify provenance. Labor: AI. Script called: none. Input: `pantry/singhkanishknagendra_348738_41749683_Singh_Kanishk_A3_Workflow.json`. Output: provenance check. Where output goes: `logs/`.
2. Step name: GitHub API - Axe-core Rules. Labor: AI. Script called: `scripts/gigo/accessibility-monitor-data-collection-pipeline__github-api-axe-core-rules.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
3. Step name: W3C WCAG JSON - Success Criteria. Labor: AI. Script called: `scripts/ingest/accessibility-monitor-data-collection-pipeline__w3c-wcag-json-success-criteria.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
4. Step name: RSS - WebAIM Blog. Labor: AI. Script called: `scripts/ingest/accessibility-monitor-data-collection-pipeline__rss-webaim-blog.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
5. Step name: RSS - A11y Project. Labor: AI. Script called: `scripts/ingest/accessibility-monitor-data-collection-pipeline__rss-a11y-project.py`. Input: prior step output or approved local sample. Output: ingest result JSON. Where output goes: `data/raw/`.
6. Step name: Merge + Normalize + Deduplicate. Labor: AI. Script called: `scripts/gigo/accessibility-monitor-data-collection-pipeline__merge-normalize-deduplicate.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
7. Step name: Save to CSV. Labor: AI. Script called: `scripts/tools/accessibility-monitor-data-collection-pipeline__save-to-csv.py`. Input: prior step output or approved local sample. Output: tool result JSON. Where output goes: `logs/`.
8. Step name: Write Error Log. Labor: AI. Script called: `scripts/gigo/accessibility-monitor-data-collection-pipeline__write-error-log.py`. Input: prior step output or approved local sample. Output: gigo result JSON. Where output goes: `data/verified/`.
9. Step name: Produce human report. Labor: AI. Script called: none; conductor fills `reports/templates/accessibility-monitor-data-collection-pipeline.md`. Input: run log and verified outputs. Output: concise decision report. Where output goes: `reports/generated/`.

## Output Contract

### Agent output

The agent output goes to `logs/accessibility-monitor-data-collection-pipeline-[DATE].json` and contains `workflow`, `workflow_slug`, `source_json`, `mode`, `steps_completed`, `records_seen`, `handoffs`, `flags`, `stop_conditions`, and `generated_at`.

### Human report

The human report goes to `reports/generated/accessibility-monitor-data-collection-pipeline-[DATE].md`. It surfaces the verified signal, any missing or malformed source data, the decisions enabled by the workflow, and which live actions still require approval.

## Stop Conditions

- Stop if `pantry/singhkanishknagendra_348738_41749683_Singh_Kanishk_A3_Workflow.json` is missing or cannot be parsed.
- Stop if a live source, model, database, email, dashboard, or file export is requested without explicit approval.
- Stop if an ingest result cannot be represented as JSON under `data/raw/`.
- Stop if GIGO scripts produce zero records when the source should contain records.
- Stop if generated reports would expose credentials, private tokens, or unapproved personal data.
- Stop if the final decision claim cannot be traced to source, verified data, or a logged handoff.

## Provenance

Original workflow JSON: `pantry/singhkanishknagendra_348738_41749683_Singh_Kanishk_A3_Workflow.json`
