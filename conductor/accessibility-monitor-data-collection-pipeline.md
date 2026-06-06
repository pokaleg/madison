# Accessibility Monitor - Data Collection Pipeline - Conductor Flow

## Mode

Dialogic (default). Silent mode is not available until this flow is in `conductor/verified/`.

## Entry Point

Triggered when a human asks to run or test the converted `Accessibility Monitor - Data Collection Pipeline` n8n workflow from local Madison data, a sample payload, or an explicitly approved live source.

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
- AI task: Run `test -f "pantry/singhkanishknagendra_348738_41749683_Singh_Kanishk_A3_Workflow.json"`.
- Handoff condition: Original JSON exists at the documented path.
- On failure: Stop and report missing provenance.

### Step 3 - GitHub API - Axe-core Rules

- Labor: AI
- Depends on: Step 2
- AI task: Run `python3 scripts/gigo/accessibility-monitor-data-collection-pipeline__github-api-axe-core-rules.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 4 - W3C WCAG JSON - Success Criteria

- Labor: AI
- Depends on: Step 3
- AI task: Run `python3 scripts/ingest/accessibility-monitor-data-collection-pipeline__w3c-wcag-json-success-criteria.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 5 - RSS - WebAIM Blog

- Labor: AI
- Depends on: Step 4
- AI task: Run `python3 scripts/ingest/accessibility-monitor-data-collection-pipeline__rss-webaim-blog.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 6 - RSS - A11y Project

- Labor: AI
- Depends on: Step 5
- AI task: Run `python3 scripts/ingest/accessibility-monitor-data-collection-pipeline__rss-a11y-project.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 7 - Merge + Normalize + Deduplicate

- Labor: AI
- Depends on: Step 6
- AI task: Run `python3 scripts/gigo/accessibility-monitor-data-collection-pipeline__merge-normalize-deduplicate.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 8 - Save to CSV

- Labor: AI
- Depends on: Step 7
- AI task: Run `python3 scripts/tools/accessibility-monitor-data-collection-pipeline__save-to-csv.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 9 - Write Error Log

- Labor: AI
- Depends on: Step 8
- AI task: Run `python3 scripts/gigo/accessibility-monitor-data-collection-pipeline__write-error-log.py --no-write` for a dry run, then run without `--no-write` after the prior handoff passes.
- Handoff condition: The script exits successfully and writes parseable JSON to its default destination.
- On failure: Stop, preserve the failing payload, and report the node name plus script path.

### Step 10 - Write Human Report

- Labor: AI
- Depends on: Step 9
- AI task: Fill `reports/templates/accessibility-monitor-data-collection-pipeline.md` and save the completed report under `reports/generated/`.
- Handoff condition: Report links to source JSON, generated logs, and any verified data outputs.
- On failure: Stop and report missing report fields.

## Phase Gates

Steps 1, 2, live-action approval points, and the final report are hard gates. The conductor stops and waits for explicit human confirmation before crossing any gate in dialogic mode.

## Silent Mode Requirements

- At least three successful dialogic sample runs.
- Gate decisions logged in `logs/gate-decisions/`.
- Human sign-off documented for any live source or external side effect.
- Completed flow moved to `conductor/verified/` only after the evidence above exists.
