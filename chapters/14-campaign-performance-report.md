# Chapter 14 — Campaign Performance Report
*The charts were confident. The recommendation was not connected to them.*

The report lands in the client's inbox with twelve slides. There are bar charts, percentage changes, a summary paragraph, and a bold recommendation at the end. It looks complete. It looks authoritative. It looks like work was done.

The client reads the recommendation and asks: what was the baseline for that CTR comparison? The account manager does not know — the export did not include prior period data and nobody checked. The client asks: is the consideration lift you're attributing to the campaign actually from the campaign, or did the trade press story from week two drive it? Nobody thought to separate those. The client asks: what should I do differently next quarter based on this? The report does not say.

The report described what happened. It did not support a decision. The recommendation at the end was detached from the evidence in the middle, which was detached from the KPI map that should have governed what got measured in the first place.

This is metric theater — the production of a report that resembles decision support without actually providing it. It is the performance reporting equivalent of the twenty social variants from Chapter 2: the artifact is polished and the professional judgment is missing. The fix is not better charts. It is a different structure — one that makes the chain from raw export to recommendation visible and every link in it inspectable.

---

## The Three Layers of a Performance Report

A performance report does three distinct things, and most reports collapse them into one undifferentiated narrative. The collapse is where the problems live.

The first layer is description: what the metrics show. This is the factual layer. The click-through rate was 1.4%. The brand consideration score in the post-campaign survey was 34%. The share of voice in the monitored category increased 6 points. These are observations. They are true or false. They can be verified against the source files. AI is well-suited to this layer — it can extract, organize, and format metric values accurately and quickly, provided the source data is clean and the metric definitions are specified.

The second layer is interpretation: what the metric movement means. This is where description ends and analysis begins. A CTR of 1.4% means something different if the prior campaign averaged 0.9% than if the category benchmark is 2.1%. A 34% consideration score means something different if the pre-campaign baseline was 29% than if it was 37%. Interpretation requires context — specifically, the baseline and target from the KPI map — and it requires judgment about whether the movement observed is signal or noise. AI can assist with this layer by surfacing comparisons and flagging anomalies, but the interpretation itself requires a practitioner who understands what the metric is supposed to be measuring and what the business decision depends on.

The third layer is recommendation: what action follows. This is the decision layer. It answers the question the client is actually asking: given what we now know, what should we do next? Maintain current spend? Shift budget to a performing channel? Change the creative? Test a different audience segment? Run a follow-up study? The recommendation should follow from the interpretation. If the interpretation says "consideration moved significantly above target, driven by the 35-44 segment," the recommendation should name what that means for the next campaign decision, not just restate the finding.

![Vertical three-tier stack: description at the base (AI extracts and formats), interpretation in the middle (AI surfaces candidates, human decides meaning), and recommendation at the top (human accountable), with accountability shifting from machine-assisted to human-owned.](../images/14-campaign-performance-report-fig-01.png)
*Figure 14.1 — The three layers of a performance report*

<!-- → [DIAGRAM: Three-layer report structure — vertical stack with three labeled tiers: Description (bottom), Interpretation (middle), Recommendation (top) — each tier annotated with what it contains and what it requires — Description: metric values, source files, export dates / AI can extract and format / verified against KPI map; Interpretation: baseline comparisons, anomaly flags, signal vs. noise judgment / AI can surface candidates / human decides meaning; Recommendation: action, next test, decision owner / AI cannot supply / human accountable. Caption: Most reports present all three layers as the same kind of content. They are not. The distinction determines who is responsible for each claim.] -->

The structural discipline of a good performance report is keeping these three layers visually and rhetorically distinct. A sentence that reads "CTR increased 56% versus prior campaign, indicating the new creative is driving stronger audience activation, which suggests we should increase investment in this format next quarter" is doing all three things in a single sentence — and it is doing them without labeling which claims are factual, which are inferential, and which are recommendations. Pull them apart and you can assess each one. Collapse them and you cannot.

---

## The KPI Map as Report Spine

The performance report should not be designed from scratch when it is time to write it. It should be assembled against the KPI map that was built before the campaign ran. This is the connection between Chapter 8 and this one: the map defines the metrics, the definitions, the baselines, and the decision uses. The report asks, for each row in the map: what did we find, and what does that mean for the decision this metric was supposed to inform?

This discipline solves the most common performance reporting failure: the report answers questions nobody asked while omitting answers to questions that were agreed to matter. If the KPI map specified brand consideration as the primary outcome metric, the report should lead with brand consideration — not with impressions, which are easier to get and look more impressive, or with engagement rate, which moved in an interesting direction but was never the decision metric.

| KPI Map Field | Map Entry | → | Report Section Field | Report Entry |
| --- | --- | :-: | --- | --- |
| Objective | Increase consideration | → | Outcome reported | Brand consideration measured |
| Metric | Brand consideration (aided) | → | Result | 33% post-wave |
| Definition | % selecting brand after prompt | → | Definition used | % selecting brand after prompt |
| Baseline | 29% pre-wave | → | Comparison point | +4 pts vs. 29% baseline |
| Target | 34% by end of flight | → | Target status | 1 pt below target |
| Decision use | Determines whether to extend campaign | → | Decision supported | Recommendation: extend flight two weeks to close gap |
| Objective | Drive product page traffic | → | Outcome reported | CTR result |
| Metric | CTR | → | Result | 1.4% |
| Definition | Clicks / impressions | → | Definition used | Clicks / impressions |
| Baseline | 0.8% prior campaign | → | Comparison point | +0.6 pts vs. prior |
| Target | 1.2% | → | Target status | Above target |
| Decision use | Triggers creative review if < 0.6% | → | Decision supported | Recommendation: maintain current creative in next flight |

*The report is not a fresh document. It is a populated version of the KPI map.*

![Two aligned horizontal bands joined by per-field connectors: the upper KPI-map planning layer and the lower populated-report layer, with the target-status connector weighted to show an underperforming metric cannot be quietly dropped.](../images/14-campaign-performance-report-fig-02.png)
*Figure 14.2 — KPI map to report mapping*

A report built against the KPI map is also accountable in a specific way: it cannot quietly drop a metric that underperformed. If the map committed to measuring something and the report does not include it, that omission is visible. The metric was either not measured (a planning failure that should be noted) or the result was unfavorable (a finding that should be included). Selective reporting — including the metrics that look good and omitting the ones that do not — is harder when the report structure is determined by a prior agreement rather than by post-hoc selection.

---

## The Caveat Is Not a Weakness

Every performance report has limitations. The data has coverage gaps. The measurement design has confounds. The sample was smaller than planned. The timing created noise. These limitations are not embarrassing — they are the normal condition of brand measurement, which almost never occurs under controlled conditions. The question is not whether limitations exist but whether they are visible.

A caveat placed near the conclusion it qualifies is a professional act. It says: I saw this limitation, I am telling you it is there, and I am still making this recommendation because the evidence, with its limitations, is sufficient to support it. That is accountability. A report with no caveats is either working with unusually clean data or is not being honest about its evidence.

| Limitation Type | Example Caveat | Where to Place It |
| --- | --- | --- |
| Sample size | "Post-wave survey n=312; directional at segment level, not projectable to full population" | Immediately below the consideration metric result |
| Confound | "Week 3 saw significant earned media coverage; consideration lift may reflect both paid and organic effects" | In the interpretation section for the consideration finding |
| Source lag | "Social sentiment data has 48-hour processing lag; final week of flight not fully represented" | In the data sources section and flagged in the relevant metric row |
| Attribution | "Campaign ran without a holdout group; reported lift is correlated with campaign exposure, not attributable to it" | In the executive summary as a standing caveat on all outcome claims |
| Baseline | "Pre-campaign baseline estimated from Q4 tracker; different survey vendor than post-wave" | Below the baseline comparison anywhere it appears |

*Caveats are not footnotes to be buried. They are qualifications that belong adjacent to the claims they qualify.*

![Five limitation types — sample size, confound, source lag, attribution, baseline mismatch — each connected to a placement location within a faint report column, with the attribution caveat marked as a standing qualifier on all outcome claims.](../images/14-campaign-performance-report-fig-04.png)
*Figure 14.4 — Caveat placement guide*

The causal language discipline from Chapter 5 applies here with particular force. A performance report is exactly the context where "caused" and "drove" want to appear — the campaign ran, the metrics moved, it feels like the campaign caused the movement. But without a holdout group, a pre-post design with no competing explanations, or some form of causal control, the campaign and the metric movement are correlated in time, not causally linked. The warranted verb is "is associated with," "coincided with," or "occurred during a period of" — not "caused" or "drove." The distinction is not pedantic when the client is deciding how much to spend on the next campaign based on a causal claim that the evidence cannot support.

---

## The Next-Test Recommendation

A performance report that ends with findings and no forward direction has done half the job. The decision the report supports is not just "did this work?" It is "what should we do next, and what should we test to know if we are right?"

The next-test recommendation is a specific element: a proposed experimental variation for the next campaign that would produce evidence bearing on an open question from this one. If the current report shows that the 35-44 segment drove disproportionate consideration movement but the 25-34 segment did not respond, the next test is not "run the same campaign again." It is: run a variant in the 25-34 segment with modified creative to test whether the non-response was a targeting issue, a message issue, or a genuine lack of category interest in that segment.

![Three stacked three-node chains, each running from a finding to the open question it raises to a proposed test design, echoing the description-interpretation-recommendation color logic of the report.](../images/14-campaign-performance-report-fig-03.png)
*Figure 14.3 — Next-test recommendation structure*

<!-- → [DIAGRAM: Next-test recommendation structure — three-node flow: (1) Finding from current report → (2) Open question it raises → (3) Proposed test design — three example chains shown: "35-44 over-indexed on consideration" → "Is 25-34 non-response a message or targeting issue?" → "A/B test: same creative, tighter 25-34 targeting vs. modified creative for 25-34" | "CTR above target, consideration below target" → "Is high CTR driving unqualified traffic?" → "Add landing page conversion tracking and post-click survey next flight" | "Share of voice increased, competitor activity decreased" → "Is SOV gain campaign-driven or competitor-driven?" → "Monitor competitor activity week-by-week, isolate before attributing SOV movement to campaign." Caption: The next-test recommendation turns a report into the first step of a learning cycle rather than a period at the end of a campaign.] -->

The next-test recommendation is human work. An AI agent can suggest candidate tests based on the findings, and that is a useful input. But the decision about which test is worth running — given the budget available, the strategic priorities, the client relationship, and the timeline for the next campaign — is a judgment that requires contextual knowledge the agent does not have. The agent surfaces options; the practitioner decides.

---

## The Human-Review Field

The performance readout, like the KPI map, should have a sign-off field. The field records who reviewed the report, on what date, and what their accountability is. This is the point in the workflow where the agent's assembly work becomes a professional document.

The human-review field is not a formality. It is the boundary between an AI-assisted analysis and a professional recommendation. Before the sign-off, the document is a draft with numbers in it. After it, the document carries a practitioner's judgment about what the numbers mean and what the client should do. Those are different things, and the distinction should be visible.

The review itself has a checklist: Do the metrics in the report match the KPI map? Is every source named and dated? Are the caveats present and adjacent to the conclusions they qualify? Does the report contain any causal claims that the evidence does not support? Does the recommendation follow from the interpretation, or is it a separate assertion? Does the report end with a forward direction?

| Check | Status |
| --- | --- |
| Metrics match KPI map | ☐ Verified ☐ Discrepancy noted |
| Sources named and dated | ☐ All sourced ☐ Gaps flagged |
| Causal language audit | ☐ No unwarranted causal claims ☐ Claims rewritten |
| Caveats adjacent to conclusions | ☐ Placed correctly ☐ Moved |
| Recommendation follows from interpretation | ☐ Connected ☐ Disconnect noted |
| Forward direction included | ☐ Next test specified ☐ Missing — requires revision |
| Reviewer name and date | __________________________ |

*The checklist is not a quality rating. It is a record that a named person examined these specific elements before the report moved.*

A report that passes this checklist is not a perfect report — no report that depends on imperfect data can be perfect. It is a defensible report: one in which the claims are inspectable, the limitations are visible, and the recommendation is traceable to the evidence that supports it. That is the standard Madison sets for performance reporting, and it is a higher standard than most campaign reports currently meet.

---

## What Would Change My Mind

The argument against this level of reporting discipline is that clients do not want it. They want a clear story, a confident recommendation, and a number that went up. A report that leads with caveats and carefully labels its interpretations as interpretations rather than facts will lose in a competitive pitch to a report that leads with "your campaign delivered a 56% lift in CTR and drove significant consideration movement." If the market rewards confident metric theater, requiring practitioners to produce qualified, inspectable reports is asking them to compete at a disadvantage.

I think this is true in some client relationships and false in others — specifically, false in relationships where a practitioner has the standing to say "I am going to tell you what the evidence actually supports, and that is more valuable than a confident story that collapses under scrutiny." Building that standing is partly a skill and partly a track record. But the argument that the market structurally rewards overconfident reporting is one I take seriously. If you apply this framework and consistently find that clients respond worse to accurate, inspectable reports than to polished metric theater, that is evidence the problem is upstream of the report — in the client relationship, the brief, or the expectations set at the start of the engagement.

## Still Puzzling

The hardest question in performance reporting is also the most important one: what would it actually take to make a defensible causal claim? The held-out control group is the gold standard and is almost never available at the budgets and timelines of most brand campaigns. There are quasi-experimental approaches — difference-in-differences designs, synthetic controls, geographic holdouts — that can do better than pre-post comparison without a full RCT. I do not have a clean answer for when these approaches are practical for a mid-market brand team versus when "is associated with" is honestly the best we can do.

---

## LLM Exercises

**Exercise 1 — Layer Separation**
Take any performance report you have recently written or received. Paste the executive summary into the chat and ask the LLM to separate it into three layers: description (what the metrics show), interpretation (what the movement means), and recommendation (what action follows). Then review the output. Where did the original report collapse layers? Where was the interpretation presented as description, or the recommendation detached from the interpretation?

**Exercise 2 — Causal Language Audit**
Give the LLM five sentences from a performance report — choose ones that include words like "drove," "caused," "resulted in," "led to," or "delivered." Ask it to identify which ones are making causal claims and whether the evidence described in the sentence supports a causal interpretation. Then rewrite the ones it flags using warranted verbs.

**Exercise 3 — Next-Test Generation**
Give the LLM two or three key findings from a campaign report. Ask it to generate a next-test recommendation for each one using the three-node structure: finding → open question → proposed test. Review the output. Which proposed tests would you run? Which are impractical given timeline or budget? What the LLM cannot assess is whether the test is worth running given your specific context — that evaluation is yours.

---

## Exercises

**Warm-up**

1. *(Basic recall)* What are the three layers of a performance report, and what kind of claim does each one make? Give one example of a sentence that belongs in each layer. *What this tests: whether you can distinguish description, interpretation, and recommendation before applying the structure.*

2. *(Concept check)* Why should a performance report be built against the KPI map rather than assembled from whatever metrics are available at reporting time? What failure does the KPI map prevent? *What this tests: whether you understand the structural connection between planning and reporting.*

3. *(Definition)* What is metric theater, and what distinguishes a performance report that produces it from one that supports decisions? Give a specific structural difference. *What this tests: whether you can identify the report form that signals the problem, not just the general concept.*

**Application**

4. *(Moderate)* A performance report includes the following sentence: "The campaign drove a 12-point increase in brand consideration, demonstrating that the new messaging platform is resonating with the target audience." Identify every place where this sentence makes a claim stronger than warranted. Rewrite it in three separate sentences — one description, one interpretation, one recommendation — using warranted verbs throughout. *What this tests: whether you can apply layer separation and the causal language audit to a realistic example.*

5. *(Moderate)* You are reviewing a performance report before it goes to a client. The report includes strong consideration lift findings but no mention of the fact that a major news story about the brand ran in week two of the campaign flight. Write the caveat that should appear in the report, specify where it should be placed, and explain what decision it would affect if the client were using the consideration finding to justify increasing campaign spend. *What this tests: whether you can identify a confound, write a specific caveat, and connect it to a downstream decision.*

6. *(Moderate)* Using the KPI map structure from Chapter 8, create a two-row KPI map for a hypothetical brand awareness campaign. Then populate the corresponding report fields for each row, including a result, a baseline comparison, a target status, and a decision output. For one row, show a result that met the target; for the other, show a result that missed it. *What this tests: whether you can connect the planning and reporting frameworks end-to-end.*

**Synthesis**

7. *(Challenging)* A performance report shows that CTR was well above target (1.8% vs. 1.2% target) but brand consideration did not move (33% vs. 34% target, within margin of error). The client wants to know whether the campaign worked. Using the three-layer structure and the warranted-verb discipline, write a three-paragraph executive summary that answers the client's question accurately without either false confidence or evasion. Include a caveat and a next-test recommendation. *What this tests: whether you can produce a complete, honest performance narrative under the constraint of mixed results.*

8. *(Challenging)* The chapter argues that a report built against the KPI map cannot quietly drop a metric that underperformed. Describe a realistic scenario in which a practitioner would be tempted to drop a metric from a report — what the metric was, why it underperformed, and what the client context looks like. Then describe what the professionally accountable response is, including how to present a poor result without undermining the overall recommendation. *What this tests: whether you can apply the accountability framework to a situation with real professional stakes.*

**Challenge**

9. *(Open-ended)* "Still Puzzling" raises the question of when quasi-experimental approaches — difference-in-differences, geographic holdouts, synthetic controls — are practical for mid-market brand teams. Research or reason through one of these approaches: what does it require in terms of data, design, and timeline? Under what conditions would a typical brand team with a modest measurement budget be able to implement it? What would the resulting claim be able to say that a standard pre-post comparison cannot? What would it still not be able to say? *What this tests: whether you can engage with the causal inference problem as a practical design question rather than a theoretical one.*

---

## Prompts

### Figure 14.1 — The three layers of a performance report
**Files:** ../images/14-campaign-performance-report-fig-01.svg · ../d3/14-campaign-performance-report-fig-01.html
**Prompt:** Vertical three-tier stack on white, foundation to apex: description (AI extracts and formats, secondary accent), interpretation (AI surfaces candidates, human decides, ink accent), recommendation (human accountable, red accent), with a red dashed boundary between interpretation and recommendation marking the AI-to-human accountability shift. EB Garamond title, Inter labels, brutalist palette only.

### Figure 14.2 — KPI map to report mapping
**Files:** ../images/14-campaign-performance-report-fig-02.svg
**Prompt:** Structural schematic of two aligned horizontal bands on white joined by six single-headed per-field connectors — the upper KPI-map planning layer and the lower populated-report layer — with the target-status connector weighted to encode that an underperforming metric cannot be quietly dropped. JetBrains Mono numerals, no example values, brutalist palette only.

### Figure 14.3 — Next-test recommendation structure
**Files:** ../images/14-campaign-performance-report-fig-03.svg · ../d3/14-campaign-performance-report-fig-03.html
**Prompt:** Three stacked left-to-right chains on white, each running finding to open question to proposed test, joined by single-headed arrows, with node strokes echoing the report's three-layer logic (finding secondary, question ink, test red). EB Garamond title, Inter labels, brutalist palette only.

### Figure 14.4 — Caveat placement guide
**Files:** ../images/14-campaign-performance-report-fig-04.svg
**Prompt:** Mapping panel on white: five limitation-type markers on the left each connected by a single-headed arrow to a placement location within a faint right-side report column of stacked sections, with the attribution standing caveat drawn in red since it qualifies all outcome claims. Inter labels, no footnote symbols, brutalist palette only.
