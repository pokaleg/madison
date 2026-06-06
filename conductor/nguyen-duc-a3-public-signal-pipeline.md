# Nguyen Duc A3 Public Signal Pipeline - Conductor Flow

## Mode

Dialogic (default). Silent mode is not available until this flow is in `conductor/verified/`.

## Entry Point

Triggered when a human asks to run or test the converted `Nguyen Duc A3 Public Signal Pipeline` n8n workflow from local Madison data, a sample payload, or an explicitly approved live source.

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
- AI task: Run `test -f "pantry/Nguyen_Duc_A3_Workflow.json"`.
- Handoff condition: Original JSON exists at the documented path.
- On failure: Stop and report missing provenance.

### Step 3 - HTTP - Hacker News

- Labor: AI
- Depends on: Step 2
- AI task: Run `python3 scripts/ingest/nguyen-duc-a3-public-signal-pipeline__http-hacker-news.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 4 - HTTP - DEV Community

- Labor: AI
- Depends on: Step 3
- AI task: Run `python3 scripts/ingest/nguyen-duc-a3-public-signal-pipeline__http-dev-community.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 5 - HTTP - GitHub Search

- Labor: AI
- Depends on: Step 4
- AI task: Run `python3 scripts/ingest/nguyen-duc-a3-public-signal-pipeline__http-github-search.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 6 - Normalize - Hacker News

- Labor: AI
- Depends on: Step 5
- AI task: Run `python3 scripts/gigo/nguyen-duc-a3-public-signal-pipeline__normalize-hacker-news.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 7 - Normalize - DEV Community

- Labor: AI
- Depends on: Step 6
- AI task: Run `python3 scripts/gigo/nguyen-duc-a3-public-signal-pipeline__normalize-dev-community.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 8 - Normalize - GitHub

- Labor: AI
- Depends on: Step 7
- AI task: Run `python3 scripts/gigo/nguyen-duc-a3-public-signal-pipeline__normalize-github.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 9 - Clean, Deduplicate, Validate

- Labor: AI
- Depends on: Step 8
- AI task: Run `python3 scripts/gigo/nguyen-duc-a3-public-signal-pipeline__clean-deduplicate-validate.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 10 - Convert to CSV

- Labor: AI
- Depends on: Step 9
- AI task: Run `python3 scripts/tools/nguyen-duc-a3-public-signal-pipeline__convert-to-csv.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 11 - Write CSV to Downloads

- Labor: AI
- Depends on: Step 10
- AI task: Run `python3 scripts/tools/nguyen-duc-a3-public-signal-pipeline__write-csv-to-downloads.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 12 - Write Human Report

- Labor: AI
- Depends on: Step 11
- AI task: Fill `reports/templates/nguyen-duc-a3-public-signal-pipeline.md` and save the completed report under `reports/generated/`.
- Handoff condition: Report links to source JSON, generated logs, and any verified data outputs.
- On failure: Stop and report missing report fields.

## Phase Gates

Steps 1, 2, live-action approval points, and the final report are hard gates. The conductor stops and waits for explicit human confirmation before crossing any gate in dialogic mode.

## Silent Mode Requirements

- At least three successful dialogic sample runs.
- Gate decisions logged in `logs/gate-decisions/`.
- Human sign-off documented for any live source or external side effect.
- Completed flow moved to `conductor/verified/` only after the evidence above exists.
