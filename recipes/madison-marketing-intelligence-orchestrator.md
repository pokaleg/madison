# Madison Marketing Intelligence Orchestrator

## Purpose

Routes marketing intelligence questions to the right Madison recipe family so brand, campaign, audience, sentiment, competitive, and portfolio work can be coordinated without skipping human gates.

## Inputs

| Input | Type | Source | Required? |
|---|---|---|---|
| User request | Text/JSON | Chat, brief, or conductor request. | Yes |
| Available recipe registry | JSON | [TODO: DEV] Define Madison marketing recipe registry. | Yes |
| Gate state | JSON | `logs/gate-decisions/` | No |
| Mycroft adaptation source | Markdown | `/Users/bear/Documents/CoWork/bear-textbooks/books/mycroft/recipes/orchestrator.md` and `orchestrator-v2-enhanced.md` | No |

## Phase Gates

1. Registry gate: available recipes and allowed routes are defined. Test: `python3 -m json.tool data/verified/madison-marketing-intelligence-orchestrator/recipe-registry.json`. Human capacity: [PF].
2. Safety gate: no downstream recipe runs in live mode unless its gates pass. Test: `rg -n "TODO:" recipes/madison-marketing-intelligence-orchestrator.md`. Human capacity: [EI].
3. Sample gate: sample mode routes only and performs no live action. Test: `snickerdoodle run madison-marketing-intelligence-orchestrator --mode dialogic --sample`. Human capacity: [TO].

## Steps

1. Step name: Classify marketing request. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/gigo/madison-marketing-intelligence-orchestrator__classify-marketing-request.py`
   Input: user request and recipe registry.
   Output: verified JSON fields: request_type, candidate_recipes, confidence, missing_inputs, gate_requirements.
   Where output goes: `data/verified/madison-marketing-intelligence-orchestrator/`.
2. Step name: Build routing plan. Labor: AI with Human gate.
   Script called: `[TODO: DEV] Create scripts/gigo/madison-marketing-intelligence-orchestrator__build-routing-plan.py`
   Input: classified request and gate state.
   Output: verified JSON fields: ordered_recipes, required_inputs, blocked_steps, gate_checks, sample_commands.
   Where output goes: `data/verified/madison-marketing-intelligence-orchestrator/`.
3. Step name: Produce orchestrator handoff. Labor: AI with Human review.
   Script called: `[TODO: DEV] Create scripts/tools/madison-marketing-intelligence-orchestrator__produce-orchestrator-handoff.py`
   Input: routing plan.
   Output: markdown sections: request summary, recommended recipes, blocked gates, sample commands, human decisions required.
   Where output goes: `reports/generated/`.

## Output Contract

### Agent output
File: `logs/madison-marketing-intelligence-orchestrator-[DATE].json`
Fields: `workflow`, `run_id`, `mode`, `steps_completed`, `records_seen`, `rejects`, `duplicates`, `flags`, `stop_conditions`, `todo_items`, `source_files`, `gate_decisions`, `generated_at`.

### Human report
File: `reports/generated/madison-marketing-intelligence-orchestrator-[DATE].md`
Reader: marketing operations lead or conductor operator.
Decision enabled: decide which recipe to run next, what inputs are missing, and which gates must be approved first.
Sections: Request classification, candidate recipes, routing plan, missing inputs, gate blockers, next commands.

## Stop Conditions

- Stop if the request maps to no approved recipe because the orchestrator would invent workflow behavior.
- Stop if a downstream recipe has unresolved live-action gates.
- Stop if activation, email, publishing, or API writes are requested without human approval.

## Snickerdoodle

### Run Commands
Full dialogic run: `snickerdoodle run madison-marketing-intelligence-orchestrator --mode dialogic`
Sample mode: `snickerdoodle run madison-marketing-intelligence-orchestrator --mode dialogic --sample`

### Step Commands

| Step | CLI Command | Flags |
|---|---|---|
| Classify marketing request | `snickerdoodle run madison-marketing-intelligence-orchestrator --step classify-marketing-request` |  |
| Build routing plan | `snickerdoodle run madison-marketing-intelligence-orchestrator --step build-routing-plan` |  |
| Produce orchestrator handoff | `snickerdoodle run madison-marketing-intelligence-orchestrator --step produce-orchestrator-handoff` | `--no-write` |

### Gate Commands

| Gate | CLI Command |
|---|---|
| Gate 1 - registry approval | `snickerdoodle gate madison-marketing-intelligence-orchestrator --gate 1 --decision approve --note "..."` |

### Script Locations

| Step | Script Path | Layer |
|---|---|---|
| Classify marketing request | `[TODO: DEV] scripts/gigo/madison-marketing-intelligence-orchestrator__classify-marketing-request.py` | gigo |
| Build routing plan | `[TODO: DEV] scripts/gigo/madison-marketing-intelligence-orchestrator__build-routing-plan.py` | gigo |
| Produce orchestrator handoff | `[TODO: DEV] scripts/tools/madison-marketing-intelligence-orchestrator__produce-orchestrator-handoff.py` | tool |

### Output Locations

| Output | Path | Format |
|---|---|---|
| Raw ingest | `data/raw/madison-marketing-intelligence-orchestrator/` | JSON |
| Verified data | `data/verified/madison-marketing-intelligence-orchestrator/` | JSON |
| Agent log | `logs/madison-marketing-intelligence-orchestrator-[DATE].json` | JSON |
| Human report | `reports/generated/madison-marketing-intelligence-orchestrator-[DATE].md` | Markdown |
| Gate decisions | `logs/gate-decisions/` | JSON |

