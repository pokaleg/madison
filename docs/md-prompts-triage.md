# MD/prompts triage — what's worth pulling into Madison

Scanned all 33 files in `books/MD/prompts/`. Verdict up front: **most of this folder is earlier or parallel drafts of suites you already reconciled into `madison/prompts/`.** Re-importing them wholesale would fork your source of truth. Three are genuinely new and earn a place; one is a strong tool for building the textbook itself; the rest are already-covered or out-of-scope.

## Port these into `madison/prompts/` (net-new, on-mission)

| File | New suite | Why it belongs |
|---|---|---|
| `business-case-analysis-and-interview-practice.md` (`/caze`, `/mycaze`, `/help`) | `prompts/caze/` | Case-method analysis + mock interview practice. INFO 7375 runs on brand cases, and the interview drill is a clean fit for a branding/strategy course. Well-formed command map (281 lines), nothing in Madison covers it. |
| `ai-project-to-scientific-paper.md` | `prompts/paper/` | Serves *your* credibility play directly — "I can also write a paper about the working tool" — **and** students who productize their Madison tool. Ties straight to the brand thesis in `brand.yml`. New domain. |
| `evidence-based-analytical-writing-and-review-command-map.md` (verdict-essay, scientific-paper-review, venture-diligence, interview-case-study, …) | harvest, don't import whole | 1,955 lines, ~15 commands. Overlaps the `skep` plugin and `review`. **Cherry-pick** `venture-diligence`, `scientific-paper-review`, and `interview-case-study` into `caze`/`paper`; leave the rest — importing all of it duplicates skep. |

## Author tool — for *you* building this book, not a student suite

| File | Use |
|---|---|
| `education-tic-toc-v2.md` — *Tic TOC, Textbook Architecture Consultant* (2,267 lines; full `/i` intake → `/l` outcomes → `/c` chapters → `/m` market → `/p` proposal map) | The most valuable file here for the **Madison textbook itself**. Keep as an author-side tool (e.g. `tools/` or your book root), not a course suite. This is the thing that structures the book you're writing. |
| `education-ise.md` / `education-ise-complete.md` (ISE writing assistant, "Skepticism Edition") | Belongs with the `skep` project, not Madison. The `-complete` is the keeper; the other is an older cut. |

## Already covered — do **not** re-import (you'd fork the reconciled source)

These are prior/parallel versions of suites you already cleaned up and deduped:

- `brand-identity-strategy-and-style-guide-prompt-set.md` → **Nina** (`prompts/nina/`)
- `brand-communications-audit-and-strategic-memo.md` → **BRANDY** (`prompts/brandy/`)
- `branding-tool-pitch-master-prompt-set.md` + `history-branding-tool-pitch-framework.md` + `history-branding-tool-pitch-slide-prompts.md` → **Madison Pitch** (`prompts/madison-pitch/`). The `history-` pair are older drafts — title is literally the same. Diff if curious, don't merge.
- `design-hero-image-and-scientific-figure-prompts.md`, `design-scientific-figure-prompt-set-generator.md`, `high-assertion-zone-visualization-prompt-generator.md`, `magazine-hero-image-editorial-art-direction-prompt.md`, `media-magazine-hero.md` → **CAJAL** (`prompts/cajal/`) — the hero-image / scientific-figure family you already reconciled.
- `source-to-textbook-chapter-transformer.md`, `substack-writing-and-textbook-chapter-command-set.md`, `immersive-science-explanation-and-textbook-writing-assistant.md`, `technical-explanation-design-analysis-and-textbook-writing-assistant.md`, `science-immersive-mechanism-narrative.md`, `media-design-analysis-review.md`, `writing-mechanism-and-design-analysis-assistant.md` → the **textbook / chapter / essay** plugin skills (Fry + textbook). Already installed as skills.
- `substack-article-editorial-review-assistant.md`, `substack-markdown-to-html-converter.md` → **skep** plugin skills.
- `history-intimate-narrative-journalism.md` → **nart** plugin skill.

## Out of scope / niche — leave where they are

- `media-game-design-documentation-consultant.md` — different course (game design).
- `music-suno-portuguese-prompt.md` — niche one-off.
- `writing-award-nomination-letter-generator.md`, `writing-case-study-prompts.md`, `writing-voiceover-script-prompts.md` — small standalone utilities; pull a single command in only if a specific exercise needs it.
- `philosophy-guided-inquiry-prompt-evaluation.md` — a prompt-quality evaluator (Paul-Elder). Meta-useful for *grading student prompts*, but it's a grading aid, not course content. Park it.
- `prompt-template-pattern-image-generation-example.md` — a reference example, not a suite.

## The one risk to name

Several of these predate your reconciliation pass. If you import any "already covered" file thinking it's an upgrade, you'll silently fork Nina / BRANDY / Madison Pitch / CAJAL and lose the dedup work. Rule: **`madison/prompts/` is the source of truth.** Anything from `MD/prompts/` gets *diffed in*, never copied over.

## Recommended next move

Port `business-case-analysis` → `prompts/caze/` and `ai-project-to-scientific-paper` → `prompts/paper/` (each = body `.md` + `manifest.yml`, run through `build-prompts.mjs`), then cherry-pick the three commands from the evidence-based map into them. Keep `tic-toc` as your book-architecture tool. That's the whole useful yield — two new course suites and one author tool — out of 33 files.
