# Chapter Enrichment Log — madison

**Date:** 2026-06-15
**Pass:** Tables & Figures enrichment (in place, `chapters/`)
**Design authority:** `brutalist/CLAUDE.md` (D3 v7) + `brutalist/DESIGN.md` (visual constitution)

## Totals

| Metric | Count |
|---|---|
| TABLE comments rendered → markdown tables | 31 |
| TABLE comments remaining | 0 |
| FIGURE comments bound + preserved | 21 |
| Figure image references in chapters | 61 |
| Static SVGs (`images/`) | 135 |
| PNGs (300 DPI, `images/`) | 135 |
| Interactive D3 v7 files (`d3/`) | 107 (32 new + 75 pre-existing course files, untouched) |
| Chapters with a `## Prompts` section | 18 |

## What changed

- **Pass 1 — Tables:** every `<!-- [TABLE: …] -->` comment replaced with a GitHub-flavored markdown table inferred from surrounding prose, with an italic `*Table N — caption*` line. No headings added above tables.
- **Pass 2 — Figures:** each `[IMAGE/FIGURE/DIAGRAM/INFOGRAPHIC/CHART]` comment was **preserved** (never removed); an `![alt](images/{slug}-fig-NN.png)` + `*Figure N.N — title*` was inserted directly above it. Each bound figure got a brutalist static SVG and a self-contained D3 v7 HTML companion (pinned cdnjs 7.9.0, `var(--color-*)` theming, dark mode, reduced motion, ResizeObserver, `(event,d)` handlers, zero-baseline bars, inline FALLBACK_DATA, ARIA). Pre-existing unrelated `d3/` course files were left untouched.
- **Pass 3 — CAJAL reconciliation:** figure comments bound to the matching CAJAL figure by content; remaining unreferenced CAJAL figures inserted at semantic spots. One cross-chapter reuse (ch3 supervision diagram → ch2 fig-03, "shared with Chapter 2"). One figure minted where a comment had no CAJAL match (ch6 fig-04).
- **Pass 4 — PNG:** `node scripts/svg-to-png.mjs` regenerated PNGs from updated SVGs. SVG/PNG parity = 135/135.
- **Pass 5 — Prompts:** every enriched chapter carries a `## Prompts` section, one entry per figure.

## Palette remediation

- madison's CAJAL SVG batch had used Okabe-Ito hues; all figure SVGs were remapped to the six-variable brutalist palette (ink/red/secondary/border/ochre/white + permitted neutral grays). Zero off-palette colors remain in `images/*.svg`.

## Invariants honored

- No prose, headings, or exercises altered outside comment regions and the appended `## Prompts` sections.
- No FIGURE comments removed. All image references use `../images/…` (resolve from `chapters/`).

---
*(This file supersedes an earlier auto-generated enrichment stub.)*
