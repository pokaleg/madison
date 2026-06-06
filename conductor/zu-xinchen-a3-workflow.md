# Zu Xinchen A3 Workflow - Conductor Flow

## Mode

Dialogic (default). Silent mode is not available until this flow is in `conductor/verified/`.

## Entry Point

Triggered when a human asks to run or test the converted `Zu Xinchen A3 Workflow` n8n workflow from local Madison data, a sample payload, or an explicitly approved live source.

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
- AI task: Run `test -f "pantry/zuxinchen_405407_41801846_Zu_Xinchen_A3_Workflow.json"`.
- Handoff condition: Original JSON exists at the documented path.
- On failure: Stop and report missing provenance.

### Step 3 - RSS Read

- Labor: AI
- Depends on: Step 2
- AI task: Run `python3 scripts/ingest/zu-xinchen-a3-workflow__rss-read.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 4 - RSS Read1

- Labor: AI
- Depends on: Step 3
- AI task: Run `python3 scripts/ingest/zu-xinchen-a3-workflow__rss-read1.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 5 - RSS Read2

- Labor: AI
- Depends on: Step 4
- AI task: Run `python3 scripts/ingest/zu-xinchen-a3-workflow__rss-read2.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 6 - Edit Fields

- Labor: AI
- Depends on: Step 5
- AI task: Run `python3 scripts/gigo/zu-xinchen-a3-workflow__edit-fields.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 7 - Convert to File

- Labor: AI
- Depends on: Step 6
- AI task: Run `python3 scripts/tools/zu-xinchen-a3-workflow__convert-to-file.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 8 - RSS Read3

- Labor: AI
- Depends on: Step 7
- AI task: Run `python3 scripts/ingest/zu-xinchen-a3-workflow__rss-read3.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 9 - RSS Read4

- Labor: AI
- Depends on: Step 8
- AI task: Run `python3 scripts/ingest/zu-xinchen-a3-workflow__rss-read4.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 10 - RSS Read5

- Labor: AI
- Depends on: Step 9
- AI task: Run `python3 scripts/ingest/zu-xinchen-a3-workflow__rss-read5.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 11 - Write Human Report

- Labor: AI
- Depends on: Step 10
- AI task: Fill `reports/templates/zu-xinchen-a3-workflow.md` and save the completed report under `reports/generated/`.
- Handoff condition: Report links to source JSON, generated logs, and any verified data outputs.
- On failure: Stop and report missing report fields.

## Phase Gates

Steps 1, 2, live-action approval points, and the final report are hard gates. The conductor stops and waits for explicit human confirmation before crossing any gate in dialogic mode.

## Silent Mode Requirements

- At least three successful dialogic sample runs.
- Gate decisions logged in `logs/gate-decisions/`.
- Human sign-off documented for any live source or external side effect.
- Completed flow moved to `conductor/verified/` only after the evidence above exists.
