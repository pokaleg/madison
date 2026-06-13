# Exercise Nine — Brand Storytelling, Told True

**Course:** INFO 7375 Branding & AI · backs **Assignment 9** (Brand Storytelling & Content Strategy)
**What you'll build:** the narrative layer of your brand — three 100-word story arcs, one 300-word expanded About-page story, and one 500-word published article with a custom graphic — by **conducting Ogilvy and Nina** to structure and sharpen, while **you supply the true details, the voice, and the meaning.**
**Time:** one session to draft the arcs and expand the strongest; the publish + promote is the homework after.
**You need:** your **`brand/resume.json`** (Exercise 1 — your verified raw material), your **`brand.yml`** + archetype (A6/A7), the `ogilvy` and `nina` skills, a publishing platform (LinkedIn Articles / Medium / your site), and a graphic tool (Canva / the `cajal` skill).

The principle this exercise runs on: **the brand story is where the fluency trap is most tempting and most dangerous.** A8's warning says it plainly — *sound like a human being, not a LinkedIn post generator; write in your own voice, not the voice you think a brand should have.* The generated-brand-voice ("passionate, results-driven, innovative thought leader on a mission to disrupt…") is the fluency trap in its purest form: polished, frictionless, and indistinguishable from ten thousand others. Worse, a story is the one asset people **remember and repeat** — so a story that's embellished or untrue isn't a small fib, it's the untrustworthy artifact with the longest half-life. The discipline that closes it is the one the whole course has been building: **every story is true, specific, and yours — it traces to a real moment in your attested `brand/`, and it sounds like you because the details are real.**

The division of labor is the whole lesson, and A9 states it outright: *use AI to sharpen and structure; the specific details, the authentic voice, and the decision about what's actually true and meaningful — that's yours.* **Ogilvy and Nina do the Tier-1 work** — the framework scaffold, the hook, the pacing, the cut to 100 words. **You do the irreducible work** — choosing the true moment, supplying the concrete detail only you know, and judging whether it sounds like a person or a press release. Don't ask the tools for a story. Bring them a true thing that happened and ask them to give it shape.

---

## Command → deliverable map

| A9 deliverable (points) | Madison tool | What it gives you |
|---|---|---|
| **Voice + who it's for** (the anti-generic gate) | Nina `/n6 voice` (IS / IS NOT) + `/n3 personas` | the voice rules that keep the stories *yours*, and the reader who must "recognize something of themselves" |
| ↳ which framework fits | Nina `/n2 archetype` | your archetype suggests the natural arc (a Hero/Outlaw tells a different story than a Sage/Caregiver) |
| **Three 100-word arcs (35)** | Ogilvy `/hook` → `/emotion` → `/edit` | structure each true bullet-set into a named framework, check it lands, cut to exactly 100 words |
| **Expanded 300-word story (25)** | Ogilvy `/byline` (full) or `/blurb web` | the five-point arc (Setup · Rising · Turning · Resolution · Takeaway) — your About page |
| **500-word published article (25)** | Ogilvy `/linkedin` + `/cta`, interactive | the article with the arc as backbone, the tool woven in, a clear close; published live |
| **Custom graphic (8)** | `cajal` (`/scan`/`/show`) **or** Nina `/n7`+`/n9` | a process diagram / before-after as colorblind-safe SVG, or the brand-image generation prompt |
| **Publish + promote (7)** | Ogilvy `/linkedin` (caption) | the 2–3 sentence promotion caption that earns the click |
| **The raw material (all of it)** | **`brand/resume.json`** (Exercise 1) | the *verified, true* moments your stories are built from |

**The honest caveat — what the tools do *not* do:** they do not know what's true, and they do not have your voice. Ogilvy will happily structure a Hero's Journey out of anything you give it — including an exaggeration. The truth and the voice are the parts only you can supply, and they're the parts that are graded. Bring real material; the tools give it shape.

---

## Move 0 — Mine your true raw material

Pick your path (A: personal brand · B: the Madison tool startup), then open **`brand/resume.json`** and pull the real moments that match A9's story angles — the pivotal career turn, the failure that shaped you, the origin of the tool, the user whose pain you saw. These are your attested facts; the stories are built from them, not from a blank page.

> Render it readable first: `node scripts/to-markdown.mjs brand/resume.json`. The true, specific details — the ones that make a story sound like a person — are already in there. Use them.

If the raw material is thin, that's the signal — not to invent, but to add a real entry to `resume.json` first.

## Move 1 — Lock voice, archetype, audience (the anti-generic gate)

Open `nina` and feed it your `brand.yml`:

```
/n6      # voice: the IS / IS NOT list — this is what keeps the stories from sounding generated
/n2      # archetype: which arc is natural for you (the Outlaw and the Sage tell different stories)
/n3      # personas: who is reading, and what must they recognize of themselves?
```

Keep the `/n6` IS-NOT list beside you for the whole exercise. Every line you write gets checked against it. *"Never corporate, never breathless"* is a gate, not a preference.

## Move 2 — Three 100-word arcs (Part 1, 35 pts)

Choose **three different frameworks** (Hero's Journey · Quest · Overcoming the Monster · Rags to Riches · Mentor). For each, bring Ogilvy your **true bullets** and the framework name:

```
/hook        # the opening line that stops the scroll — from a real detail, not a slogan
/emotion     # does it land? what transformation does the reader feel?
/edit        # cut to exactly 100 words, kill every generic phrase
```

A worked prompt (paste your real material):
> *Help me structure these true bullet points into a Hero's Journey, ~100 words, sounding like a real person, not a press release: [paste from your resume.json].*

**Your gate — the trace + voice double-check:** each story (a) names its framework at the top, (b) traces to a real moment in your `brand/`, and (c) passes the read-aloud test against Nina's IS-NOT list. A story you can't trace to a true moment is the one to cut. A story that sounds like the IS-NOT column is the fluency trap — rewrite it with a more specific true detail.

## Move 3 — The expanded 300-word story (Part 1, 25 pts)

Take your **strongest** arc and expand it on the five-point structure — **Setup · Rising Action · Turning Point · Resolution · Takeaway**:

```
/byline      # (full paragraph mode) or /blurb web — structure the five beats
/emotion     # the Turning Point must carry the weight; check it does
/edit        # to 300 words, in your voice
```

This is your **About page**. It should feel earned, specific, and true — the Takeaway turns it from *your* story into something *the reader* can use. Don't open with your name (Ogilvy's rule); open with the moment.

## Move 4 — The 500-word published article (Part 2, 25 pts)

Drive Ogilvy interactively with your strongest arc as the backbone:

```
/linkedin    # lead with insight, not announcement; the arc gives it structure
/cta         # Path A: position yourself as worth following · Path B: a clear next step
/credibility # add proof — but every stat is [VERIFY — human]; only real numbers
/edit        # 500+ words, scannable: headline, subheads, short paragraphs
```

Weave the Madison tool in **as a natural extension** (Path A) or **build toward the value proposition** (Path B). Then **publish it live** — LinkedIn Articles / Medium / your site — and keep the URL. A PDF in Canvas is not "published."

## Move 5 — The custom graphic (Part 2, 8 pts)

One custom visual that **enhances the message** and carries your A7 brand system — a process diagram, a before/after, a branded image, or a tool screenshot:

- **Process / before-after diagram** → the `cajal` skill (`/scan` the article, `/show` to render a colorblind-safe SVG in your palette).
- **Branded image** → Nina `/n7` (the visual world) + `/n9` (the generation prompt) → run in Canva/Firefly.

No stock-photo orphans. The graphic traces to the story the same way every visual choice has traced since A7.

## Move 6 — Promote it (Part 2, 7 pts)

```
/linkedin    # the 2-3 sentence promotion caption that earns the click — not a summary, a hook
```

Post the caption with the link. Screenshot the promotion post (you'll need it for the PDF).

## Move 7 — Assemble + log

Build the single Canvas PDF (`LastName_FirstName_Assignment9.pdf`): the three 100-word stories with **frameworks labeled** + word counts, the 300-word expanded story, the **clickable article URL**, the LinkedIn promotion screenshot, and the custom graphic. Then one `logs/RUN_LOG.md` entry: your path, the three frameworks, which arc you expanded, your live URL, and the one story detail you can trace most cleanly to a line in `brand/resume.json`.

---

## Grading — 100 points

| Criteria | Pts | Exceptional |
|---|---|---|
| **Three story arcs** | 35 | all three distinct, specific, publication-ready, authentic voice |
| **Expanded story** | 25 | vivid, structured, emotionally resonant, five-point arc clear |
| **Article quality** | 25 | compelling 500+ words, professional voice, arc integrated |
| **Visual content** | 8 | professional, branded, enhances the message |
| **Publication & promotion** | 7 | published, well-formatted, promoted with an engaging caption |
| | **100** | |

The quality tiers all turn on the same axis the course has taught all term: *specific and authentic* beats *polished and generic*. The exceptional column is the anti-fluency-trap column.

---

## What can go wrong

| Symptom | What it means | Fix |
|---|---|---|
| It sounds like a LinkedIn post generator | the fluency trap — generated brand voice | read it aloud against Nina's `/n6` IS-NOT list; replace abstractions with one true, specific detail |
| The transformation feels invented | you reached past the true material | every arc traces to a real moment in `resume.json` — if it isn't there and isn't true, cut it |
| All three stories feel the same | one arc wearing three framework hats | different frameworks must produce different *movements* — Rags-to-Riches and Mentor can't have the same shape |
| The framework isn't visible in the article | structure didn't survive drafting | the five beats / the arc must be legible to a stranger — name them to yourself, then check each is on the page |
| "Published" is a PDF in Canvas | it isn't published | live URL on LinkedIn/Medium/your site, or you lose the 7 publication points |
| The graphic is a stock photo | visual orphan, no trace | a diagram/before-after/branded image in your A7 palette, or it doesn't count |

## Before you submit — check it

```bash
node scripts/to-markdown.mjs brand/resume.json   # your truth source — every story detail should trace back to a real entry here
```

Then, by hand: **count the words** (three at 100, one at 300, one at 500+) · run the **truth audit** — point each story to the real moment it's built from · run the **voice test** — read every piece aloud against Nina's IS-NOT list (if it sounds like the IS-NOT column, it's the generic one to fix) · confirm the **framework is visible** in each piece · confirm the **article URL resolves**. The machine can't check whether a story is true or whether it sounds like you — those are the human gates, and on a brand story they're the entire grade. Full guide: `docs/exercises/HOW-TO-CHECK.md`.

**Lifecycle note:** A6 named the brand, A7 made it visible, A8 shipped it live — and A9 makes it **memorable**. The narrative layer is the last one because it's the one that needs all the others to be true first: you can only tell the story of a brand that actually exists. Ogilvy and Nina are the through-line tools — Nina's voice keeps it yours, Ogilvy's craft gives it shape — and `brand/resume.json`, the artifact you attested back in **Exercise 1**, is one more time the source of what's true. AI structured the arc. You supplied the true detail, the voice, and the meaning. The trace is what makes the story trustworthy — and the reason a stranger will remember it is the same reason it's yours: it actually happened.
