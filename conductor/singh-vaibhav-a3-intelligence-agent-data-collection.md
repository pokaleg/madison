# Singh Vaibhav A3 - Intelligence Agent Data Collection - Conductor Flow

## Mode

Dialogic (default). Silent mode is not available until this flow is in `conductor/verified/`.

## Entry Point

Triggered when a human asks to run or test the converted `Singh Vaibhav A3 - Intelligence Agent Data Collection` n8n workflow from local Madison data, a sample payload, or an explicitly approved live source.

## Flow Steps

### Step 1 - Confirm Scope

- Labor: Human
- Depends on: none
- Human task: Confirm sample/live mode, source files, privacy boundary, and whether any external side effects are approved.
- Handoff condition: Scope states data source, allowed outputs, and live-action approvals.
- On failure: Stop and ask for scope clarification.

### Step 2 - Verify Provenance

- Labor: AI
- Depends on: Step 1
- AI task: Run `test -f "pantry/singhvaibhav_351998_41799855_Singh_Vaibhav_A3_workflow.json"`.
- Handoff condition: Original JSON exists at the documented path.
- On failure: Stop and report missing provenance.

### Step 3 - RSS - TechCrunch

- Labor: AI
- Depends on: Step 2
- AI task: Run `python3 scripts/ingest/singh-vaibhav-a3-intelligence-agent-data-collection__rss-techcrunch.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 4 - RSS - Ars Technica

- Labor: AI
- Depends on: Step 3
- AI task: Run `python3 scripts/ingest/singh-vaibhav-a3-intelligence-agent-data-collection__rss-ars-technica.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 5 - RSS - The Verge

- Labor: AI
- Depends on: Step 4
- AI task: Run `python3 scripts/ingest/singh-vaibhav-a3-intelligence-agent-data-collection__rss-the-verge.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 6 - RSS - Google News (Brand)

- Labor: AI
- Depends on: Step 5
- AI task: Run `python3 scripts/ingest/singh-vaibhav-a3-intelligence-agent-data-collection__rss-google-news-brand.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 7 - HTTP - NewsAPI

- Labor: AI
- Depends on: Step 6
- AI task: Run `python3 scripts/ingest/singh-vaibhav-a3-intelligence-agent-data-collection__http-newsapi.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 8 - HTTP - HuggingFace

- Labor: AI
- Depends on: Step 7
- AI task: Run `python3 scripts/ingest/singh-vaibhav-a3-intelligence-agent-data-collection__http-huggingface.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 9 - Norm TechCrunch

- Labor: AI
- Depends on: Step 8
- AI task: Run `python3 scripts/tools/singh-vaibhav-a3-intelligence-agent-data-collection__norm-techcrunch.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 10 - Norm Ars Technica

- Labor: AI
- Depends on: Step 9
- AI task: Run `python3 scripts/tools/singh-vaibhav-a3-intelligence-agent-data-collection__norm-ars-technica.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 11 - Norm The Verge

- Labor: AI
- Depends on: Step 10
- AI task: Run `python3 scripts/tools/singh-vaibhav-a3-intelligence-agent-data-collection__norm-the-verge.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 12 - Norm Google News

- Labor: AI
- Depends on: Step 11
- AI task: Run `python3 scripts/tools/singh-vaibhav-a3-intelligence-agent-data-collection__norm-google-news.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 13 - Norm NewsAPI

- Labor: AI
- Depends on: Step 12
- AI task: Run `python3 scripts/tools/singh-vaibhav-a3-intelligence-agent-data-collection__norm-newsapi.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 14 - Norm HuggingFace

- Labor: AI
- Depends on: Step 13
- AI task: Run `python3 scripts/gigo/singh-vaibhav-a3-intelligence-agent-data-collection__norm-huggingface.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 15 - Deduplicate & Validate

- Labor: AI
- Depends on: Step 14
- AI task: Run `python3 scripts/gigo/singh-vaibhav-a3-intelligence-agent-data-collection__deduplicate-and-validate.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 16 - Convert to CSV

- Labor: AI
- Depends on: Step 15
- AI task: Run `python3 scripts/tools/singh-vaibhav-a3-intelligence-agent-data-collection__convert-to-csv.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 17 - Save CSV

- Labor: AI
- Depends on: Step 16
- AI task: Run `python3 scripts/tools/singh-vaibhav-a3-intelligence-agent-data-collection__save-csv.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 18 - Write Human Report

- Labor: AI
- Depends on: Step 17
- AI task: Fill `reports/templates/singh-vaibhav-a3-intelligence-agent-data-collection.md` and save the completed report under `reports/generated/`.
- Handoff condition: Report links to source JSON, generated logs, and any verified data outputs.
- On failure: Stop and report missing report fields.

## Phase Gates

Steps 1, 2, live-action approval points, and the final report are hard gates. The conductor stops and waits for explicit human confirmation before crossing any gate in dialogic mode.

## Silent Mode Requirements

- At least three successful dialogic sample runs.
- Gate decisions logged in `logs/gate-decisions/`.
- Human sign-off documented for any live source or external side effect.
- Completed flow moved to `conductor/verified/` only after the evidence above exists.
