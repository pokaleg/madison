# Madison Persona Pipeline A3 - Conductor Flow

## Mode

Dialogic (default). Silent mode is not available until this flow is in `conductor/verified/`.

## Entry Point

Triggered when a human asks to run or test the converted `Madison Persona Pipeline A3` n8n workflow from local Madison data, a sample payload, or an explicitly approved live source.

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
- AI task: Run `test -f "pantry/krishnamoorthyraksha_333078_41797107_KrishnaMoorthy_Raksha_A3_Workflow-1.json"`.
- Handoff condition: Original JSON exists at the documented path.
- On failure: Stop and report missing provenance.

### Step 3 - HTTP Request: CDC

- Labor: AI
- Depends on: Step 2
- AI task: Run `python3 scripts/ingest/madison-persona-pipeline-a3__http-request-cdc.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 4 - Code: Parse CDC

- Labor: AI
- Depends on: Step 3
- AI task: Run `python3 scripts/gigo/madison-persona-pipeline-a3__code-parse-cdc.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 5 - Code: Parse Kaggle

- Labor: AI
- Depends on: Step 4
- AI task: Run `python3 scripts/gigo/madison-persona-pipeline-a3__code-parse-kaggle.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 6 - HTTP Request: HuggingFace

- Labor: AI
- Depends on: Step 5
- AI task: Run `python3 scripts/ingest/madison-persona-pipeline-a3__http-request-huggingface.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 7 - Code: Parse HuggingFace

- Labor: AI
- Depends on: Step 6
- AI task: Run `python3 scripts/gigo/madison-persona-pipeline-a3__code-parse-huggingface.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 8 - HTTP Request: RSS Feed

- Labor: AI
- Depends on: Step 7
- AI task: Run `python3 scripts/ingest/madison-persona-pipeline-a3__http-request-rss-feed.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 9 - Code: Parse RSS

- Labor: AI
- Depends on: Step 8
- AI task: Run `python3 scripts/gigo/madison-persona-pipeline-a3__code-parse-rss.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 10 - Code: Merge + Quality Check

- Labor: AI
- Depends on: Step 9
- AI task: Run `python3 scripts/gigo/madison-persona-pipeline-a3__code-merge-quality-check.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 11 - Code: Summary Report

- Labor: AI
- Depends on: Step 10
- AI task: Run `python3 scripts/gigo/madison-persona-pipeline-a3__code-summary-report.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 12 - Read/Write Files from Disk

- Labor: AI
- Depends on: Step 11
- AI task: Run `python3 scripts/ingest/madison-persona-pipeline-a3__read-write-files-from-disk.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 13 - Extract from File

- Labor: AI
- Depends on: Step 12
- AI task: Run `python3 scripts/ingest/madison-persona-pipeline-a3__extract-from-file.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 14 - Code: Generate HTML Report

- Labor: AI
- Depends on: Step 13
- AI task: Run `python3 scripts/gigo/madison-persona-pipeline-a3__code-generate-html-report.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 15 - Read/Write Files from Disk1

- Labor: AI
- Depends on: Step 14
- AI task: Run `python3 scripts/tools/madison-persona-pipeline-a3__read-write-files-from-disk1.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 16 - Write Human Report

- Labor: AI
- Depends on: Step 15
- AI task: Fill `reports/templates/madison-persona-pipeline-a3.md` and save the completed report under `reports/generated/`.
- Handoff condition: Report links to source JSON, generated logs, and any verified data outputs.
- On failure: Stop and report missing report fields.

## Phase Gates

Steps 1, 2, live-action approval points, and the final report are hard gates. The conductor stops and waits for explicit human confirmation before crossing any gate in dialogic mode.

## Silent Mode Requirements

- At least three successful dialogic sample runs.
- Gate decisions logged in `logs/gate-decisions/`.
- Human sign-off documented for any live source or external side effect.
- Completed flow moved to `conductor/verified/` only after the evidence above exists.
