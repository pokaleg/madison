# Gayatri Market Intelligence Agent - Conductor Flow

## Mode

Dialogic (default). Silent mode is not available until this flow is in `conductor/verified/`.

## Entry Point

Triggered when a human asks to run or test the converted `Gayatri Market Intelligence Agent` n8n workflow from local Madison data, a sample payload, or an explicitly approved live source.

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
- AI task: Run `test -f "pantry/pokalegayatri_333110_41799405_Pokale_Gayatri_A3_Workflow.json"`.
- Handoff condition: Original JSON exists at the documented path.
- On failure: Stop and report missing provenance.

### Step 3 - Amazon News RSS

- Labor: AI
- Depends on: Step 2
- AI task: Run `python3 scripts/ingest/gayatri-market-intelligence-agent__amazon-news-rss.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 4 - Data Cleanup

- Labor: AI
- Depends on: Step 3
- AI task: Run `python3 scripts/gigo/gayatri-market-intelligence-agent__data-cleanup.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 5 - TechCrunch AI RSS

- Labor: AI
- Depends on: Step 4
- AI task: Run `python3 scripts/ingest/gayatri-market-intelligence-agent__techcrunch-ai-rss.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 6 - CNBC Business RSS

- Labor: AI
- Depends on: Step 5
- AI task: Run `python3 scripts/ingest/gayatri-market-intelligence-agent__cnbc-business-rss.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 7 - Write Human Report

- Labor: AI
- Depends on: Step 6
- AI task: Fill `reports/templates/gayatri-market-intelligence-agent.md` and save the completed report under `reports/generated/`.
- Handoff condition: Report links to source JSON, generated logs, and any verified data outputs.
- On failure: Stop and report missing report fields.

## Phase Gates

Steps 1, 2, live-action approval points, and the final report are hard gates. The conductor stops and waits for explicit human confirmation before crossing any gate in dialogic mode.

## Silent Mode Requirements

- At least three successful dialogic sample runs.
- Gate decisions logged in `logs/gate-decisions/`.
- Human sign-off documented for any live source or external side effect.
- Completed flow moved to `conductor/verified/` only after the evidence above exists.
