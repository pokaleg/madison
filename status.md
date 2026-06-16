---
project: madison
status: active
updated: 2026-06-15
canonical: [SNICKERDOODLE.md, DOMAIN.md, AGENTS.md, outline.md, book.md, chapters/]
next:
  - "Editorial pass: expand first-pass chapters (worked examples, diagrams, exercises)"
  - "Promote/verify recipes past DRAFT with logged runs + gate decisions"
blocked_by: null
---

# Status — Madison

_Read this first for current state._ `DOMAIN.md` = what the repo **is**; `logs/RUN_LOG.md` = the full **history**; this file = **where we are now and what's next**.

## Where things stand
- **Domain:** Madison is a Snickerdoodle branding & marketing-intelligence domain (governed by `SNICKERDOODLE.md`), alongside the-reallocation-engine.
- **Manuscript:** *The Madison CLI Framework* — top-level TIKTOC chapters `chapters/01`–`16` + `97` written (coherent first-pass drafts; editorial expansion pending).
- **Operating surface:** 48 recipes (monitor/pipeline, agent, brand, student-project); two-layer `data/raw` → `data/verified` (real, not roadmap).
- **Prompts:** CLI-agnostic prompt sets under `prompts/` (source of truth; compiled by `scripts/build-prompts.mjs`).
- **Context architecture:** `AGENTS.md`/`CLAUDE.md` compile from `instructions/`; portable layer (`_MANIFEST.md`, `.ai/manifest.yaml`, `PROJECT_RULES.md`, this file) + CLI-agnostic tool shims now in place.
- **Enforcement:** `npm run verify` = conformance + manifest-check (adapter drift + canonical existence). `eval/` provides the §19 measurement harness.

## Open questions / decisions pending
- **Editorial depth** — expand chapters with longer worked examples, diagrams, exercises.
- **Recipe lifecycle** — which recipes are ready to promote past DRAFT with a logged, attested run + gate decision.

## Recently done (2026-06-15)
- Brought the repo up to the CLI-agnostic standard: portable read-first layer, generated tool shims (Gemini/Aider/Copilot/Cursor) from one source, `manifest-check` wired into verify + CI, and the §19 eval harness — matching the-reallocation-engine and Mycroft.

_Update this file at the end of each working session: state, decisions, next actions. Keep it short — it's the current-state file, not a log._
