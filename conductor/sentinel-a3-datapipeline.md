# Sentinel A3 DataPipeline - Conductor Flow

## Mode

Dialogic (default). Silent mode is not available until this flow is in `conductor/verified/`.

## Entry Point

Triggered when a human asks to run or test the converted `Sentinel A3 DataPipeline` n8n workflow from local Madison data, a sample payload, or an explicitly approved live source.

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
- AI task: Run `test -f "pantry/ranahammad_320831_41799387_Rana_Hammad_A3_Workflow.json"`.
- Handoff condition: Original JSON exists at the documented path.
- On failure: Stop and report missing provenance.

### Step 3 - Read/Write Files from Disk

- Labor: AI
- Depends on: Step 2
- AI task: Run `python3 scripts/ingest/sentinel-a3-datapipeline__read-write-files-from-disk.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 4 - Extract from File

- Labor: AI
- Depends on: Step 3
- AI task: Run `python3 scripts/ingest/sentinel-a3-datapipeline__extract-from-file.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 5 - Code in JavaScript

- Labor: AI
- Depends on: Step 4
- AI task: Run `python3 scripts/gigo/sentinel-a3-datapipeline__code-in-javascript.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 6 - Convert to File

- Labor: AI
- Depends on: Step 5
- AI task: Run `python3 scripts/tools/sentinel-a3-datapipeline__convert-to-file.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 7 - Read/Write Files from Disk1

- Labor: AI
- Depends on: Step 6
- AI task: Run `python3 scripts/tools/sentinel-a3-datapipeline__read-write-files-from-disk1.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 8 - CISA RSS Read

- Labor: AI
- Depends on: Step 7
- AI task: Run `python3 scripts/ingest/sentinel-a3-datapipeline__cisa-rss-read.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 9 - Code in JavaScript1

- Labor: AI
- Depends on: Step 8
- AI task: Run `python3 scripts/gigo/sentinel-a3-datapipeline__code-in-javascript1.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 10 - Convert to File1

- Labor: AI
- Depends on: Step 9
- AI task: Run `python3 scripts/tools/sentinel-a3-datapipeline__convert-to-file1.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 11 - Read/Write Files from Disk2

- Labor: AI
- Depends on: Step 10
- AI task: Run `python3 scripts/tools/sentinel-a3-datapipeline__read-write-files-from-disk2.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 12 - HTTP Request

- Labor: AI
- Depends on: Step 11
- AI task: Run `python3 scripts/ingest/sentinel-a3-datapipeline__http-request.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 13 - Code in JavaScript2

- Labor: AI
- Depends on: Step 12
- AI task: Run `python3 scripts/gigo/sentinel-a3-datapipeline__code-in-javascript2.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 14 - Convert to File2

- Labor: AI
- Depends on: Step 13
- AI task: Run `python3 scripts/tools/sentinel-a3-datapipeline__convert-to-file2.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 15 - Read/Write Files from Disk3

- Labor: AI
- Depends on: Step 14
- AI task: Run `python3 scripts/tools/sentinel-a3-datapipeline__read-write-files-from-disk3.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 16 - Code in JavaScript3

- Labor: AI
- Depends on: Step 15
- AI task: Run `python3 scripts/gigo/sentinel-a3-datapipeline__code-in-javascript3.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 17 - Code in JavaScript4

- Labor: AI
- Depends on: Step 16
- AI task: Run `python3 scripts/gigo/sentinel-a3-datapipeline__code-in-javascript4.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 18 - Convert to File3

- Labor: AI
- Depends on: Step 17
- AI task: Run `python3 scripts/tools/sentinel-a3-datapipeline__convert-to-file3.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 19 - Read/Write Files from Disk4

- Labor: AI
- Depends on: Step 18
- AI task: Run `python3 scripts/tools/sentinel-a3-datapipeline__read-write-files-from-disk4.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 20 - Convert to File4

- Labor: AI
- Depends on: Step 19
- AI task: Run `python3 scripts/tools/sentinel-a3-datapipeline__convert-to-file4.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 21 - Read/Write Files from Disk5

- Labor: AI
- Depends on: Step 20
- AI task: Run `python3 scripts/tools/sentinel-a3-datapipeline__read-write-files-from-disk5.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 22 - Write Human Report

- Labor: AI
- Depends on: Step 21
- AI task: Fill `reports/templates/sentinel-a3-datapipeline.md` and save the completed report under `reports/generated/`.
- Handoff condition: Report links to source JSON, generated logs, and any verified data outputs.
- On failure: Stop and report missing report fields.

## Phase Gates

Steps 1, 2, live-action approval points, and the final report are hard gates. The conductor stops and waits for explicit human confirmation before crossing any gate in dialogic mode.

## Silent Mode Requirements

- At least three successful dialogic sample runs.
- Gate decisions logged in `logs/gate-decisions/`.
- Human sign-off documented for any live source or external side effect.
- Completed flow moved to `conductor/verified/` only after the evidence above exists.
