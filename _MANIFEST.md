# _MANIFEST.md — read this first

> Portable read-first map for any agent, CLI, or human. A thin **index over the
> existing system**, not a second source of truth. If it conflicts with what you
> find on disk, trust the canonical file and flag the discrepancy in
> `logs/RUN_LOG.md`.
>
> **Governance:** `SNICKERDOODLE.md` is the constitution and governs all conflicts
> (Madison is a Snickerdoodle branding/marketing domain). `DOMAIN.md` is this repo's map.
> `AGENTS.md` (generated) is the cross-agent operating contract.

## Tier 1 — Canonical (read first)

| File | Purpose |
|------|---------|
| `SNICKERDOODLE.md` | Constitution: principles, verification stack, recipe lifecycle, gates, logging. Governs all conflicts. |
| `DOMAIN.md` | This domain's map — layout, what is runnable today, the relationship to the Snickerdoodle framework. |
| `AGENTS.md` | Generated cross-agent instructions (built from `instructions/`). |
| `PROJECT_RULES.md` | Thin precedence/compatibility pointer to the files above. |
| `DATA_CONTRACT.md` | What data exists, where it lives, the raw→verified rule. |
| `status.md` | Current state, latest decisions, next actions (where we are *now*). |
| `logs/RUN_LOG.md` | Ground-truth run history (what actually happened). |

## Tier 2 — Task-relevant (load only when the task needs it)

| Path | Use when |
|------|----------|
| `recipes/` | The operating surface — 48 recipes (monitor/pipeline + agent + brand + student-project). |
| `prompts/` | CLI-agnostic prompt sets (source of truth; compiled by `scripts/build-prompts.mjs`). |
| `brand/` | Brand strategy/identity working material (note: `brand/private-reflection.md` is private). |
| `scripts/` | Executable code (conformance, build-instructions, build-prompts, manifest-check, to-markdown, …). |
| `chapters/` | Manuscript — *The Madison CLI Framework*. |
| `data/raw/`, `data/verified/` | Two-layer data; nothing enters `verified/` unvalidated. |
| `pantry/` | Provenance inputs (n8n-derived skill files + old shared contract). |
| `reports/` | Report templates the recipes emit. |
| `docs/` | Durable human docs. Design reference (not governing): `docs/cli-agnostic-ai-tooling-grade.md`. |
| `instructions/` | Source for the generated `AGENTS.md`/`CLAUDE.md` — edit here, then rebuild. |
| `eval/` | §19 measurement harness — does the instruction scaffolding actually help? (`npm run eval:score` / `eval:report`). |
| `session-handoff.md` | Resume point when continuing a prior session. |

## Tier 3 — Generated / quarantined / private (ignore unless explicitly requested)

| Path | Rule |
|------|------|
| `output/` | Generated deliverables; **not** a source of truth. |
| `instructions/.build/`, `prompts/**/.build/`, `**/__pycache__/`, `*.pyc`, `*.bak` | Rebuildable; the only safe `rm` targets (see `instructions/_shared/no-delete.md`). |
| `people/`, `brand/private-reflection.md`, `logs/student-recipe-evidence/` | **Private by default** — contain personal/student data; never commit; read only when the task requires it. |
| `scripts/madison-main/`, `docs/madison-main/`, `data/madison-main/` | **Quarantined Tier 3** (vendored upstream app) — provenance only; do not load or treat as source. |

## Maintenance

- Machine-readable twin: `.ai/manifest.yaml` (keep in sync with this file).
- Update this manifest when Tier 1 files or top-level structure change.
- `_Last updated: 2026-06-15._`
