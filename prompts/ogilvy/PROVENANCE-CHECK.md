# Ogilvy suite — provenance check (your gate)

The `/medhavy` and `/causal` builders embed factual claims about **your own companies**. The suite is wired to treat each as `[VERIFY — human]` and never assert it unconfirmed — but here is the full list so you can confirm, correct, or strike each one before any script ships. This is the P3 gate (provenance or it isn't evidence) applied to your own brand copy: a persuasive line built on an unverified number is exactly the fluent-but-untrustworthy thing the course teaches students to catch.

This file is **not** bundled into the skill (it's not in the manifest's `knowledge_files`) — it's your working checklist.

## `/causal` — Living Models

| # | Claim as written | Where | What confirms it | Status |
|---|---|---|---|---|
| 1 | **FinCARE benchmark: F1 improvement from 0.163 → 0.759** | `/credibility` integration note (now inline-flagged `[VERIFY — human]`) | the source paper / benchmark run that produced these exact numbers | ☐ |
| 2 | **J.C. Penney 2012 pricing collapse** as the canonical "data correct, inference wrong" case | Layer 1 hook example | public event (Ron Johnson era) is real; the *causal framing* is interpretation — confirm you want to attach your argument to it | ☐ |
| 3 | **Knowledge Acquisition Tool builds a first-draft DAG in ~45 minutes** (4 phases: ~10 / 20 / 10 / 5 min) | Layer 3 + production notes | that the tool actually does this in that time with a prepared expert | ☐ |
| 4 | **Methods named as shipped:** CPDAG resolution, do-calculus, NOTEARS, DML estimation, Expected Value of Intervention | Layers 2–4 | that these are actually implemented in the product, not aspirational | ☐ |
| 5 | **Tagline + URLs:** "Causal intelligence for the decisions that actually matter" · livingmodels.org · Substack hypothetical.ai | attribution block (every output) | the URLs resolve and the tagline is the one you want on record | ☐ |

## `/medhavy` — Medhavy LLC

| # | Claim as written | Where | What confirms it | Status |
|---|---|---|---|---|
| 6 | **2–3 week deployment window** | Layer 2 | actual typical deployment time | ☐ |
| 7 | **Plugin names: CRITIQ, Popper, Nina** | `/medhavy plugin` variant | that these are real, current Medhavy plugins (names/spelling) | ☐ |
| 8 | **Feature set stated as fact:** five teaching approaches, textbook-only rule, white-label deployment, persona system, the AI-experiment layer | frame + Layer 1–3 | each feature exists and works as described | ☐ |
| 9 | **Attribution line:** "Medhavy LLC · in collaboration with Bear Brown LLC · Humanitarians AI" | close of every output | the legal/collab framing is correct and current | ☐ |

## How the suite handles these at runtime
The framing note at the top of `ogilvy.md` instructs the persona: **do not assert any specific statistic, benchmark, or named result as fact unless you've supplied or confirmed it.** When a script wants a number you haven't cleared, it writes a `[VERIFY — human]` placeholder and names what would confirm it — the same move `/credibility` already makes ("statistics to source"). So you can run `/medhavy` and `/causal` safely today; the unverified numbers come out as gated placeholders, not claims. Clear the rows above and you can let the real figures in.
