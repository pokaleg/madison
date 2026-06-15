# Chapter 3 — The Verified Brand Data Contract
*Where the chain breaks is where the trouble lives.*

There is a particular kind of meeting that brand practitioners dread more than any other. Not the meeting where the client hates the creative. Not the meeting where the budget gets cut. The meeting where someone at the table — usually the quiet one, usually the one with the most seniority — asks a simple question about the report you just presented.

*Where did that come from?*

The report said the audience is anxious about pricing. It said the category is shifting toward trust messaging. It said the brand should lead with proof. All of that sounds credible, the way things sound credible when they are formatted with confidence and presented without hesitation. But the question is not about whether the claims are plausible. The question is about whether they are traceable. And if you cannot answer it — if you have to flip back through the deck looking for a footnote that was not included, or explain that the AI surfaced the insight from several sources you did not specifically retain — the meeting has just become a different meeting entirely.

The failure in that room is not that AI was used. AI is useful; that is not in dispute. The failure is that an artifact crossed a professional boundary — from working material to decision-support — without evidence, without ownership, and without a gate. Someone trusted the output because it looked finished, and finished things have a way of demanding trust they have not earned.

![A two-column comparison — the left column "what a finished-looking report conveys" holds confidence, authority, and recommendation; the right column "what the report requires to be defensible" holds a source chain, a transformation log, and a human adequacy judgment — separated by a thin vertical boundary representing the professional line that polished formatting tends to obscure](../images/03-the-verified-brand-data-contract-fig-04.png)
*Figure 3.1 — Looks done vs is defensible*

<!-- → [DIAGRAM: The gap between "looks done" and "is defensible" — a simple two-column illustration showing what a polished report conveys (confidence, authority, recommendation) vs. what it requires to be professionally defensible (source chain, transformation log, human adequacy judgment). Caption: The professional boundary that finished formatting tends to obscure.] -->

The question this chapter is trying to answer is: how do you close that gap before the meeting happens?

---

The concept Madison introduces for this is called the verified brand data contract, and the name is worth unpacking before going further. It is a contract in the sense that it makes obligations explicit. You are obligating yourself — and your workflow — to a particular discipline: every claim in a report must be traceable back to a source, every transformation of that source must be logged, and every judgment call about whether the source is adequate must be made by a human before the output moves forward. That is the contract. It has no legal force. It has professional force, which in practice matters more.

The word "data" in the name does not mean only numbers. It means all the raw material you work with: source files, screenshots, analytics exports, client comments, URLs, approval records, draft copy inherited from a previous engagement. All of it is data in the relevant sense, which means all of it needs to be handled with the same discipline.

And "verified" does not mean the data has been proven correct in some absolute sense. It means the chain between the original source and the claim you are making from it is visible. Verifiable, not verified. The distinction matters because the goal is inspectability, not certainty. You are building something that a teammate, a client, or a future version of yourself can audit — not building a proof.

| Label | Definition | What can be cited from it | What cannot |
|---|---|---|---|
| Raw data | Original source material as collected (files, exports, URLs, screenshots). | Its literal contents, with a path. | Any interpretation not present in the source. |
| Verified data | Raw data a human has checked for date, method, and relevance. | The checked facts, as adequate for the decision. | Facts outside what was actually checked. |
| Generated artifact | Model output: summaries, drafts, suggested relationships. | Nothing as evidence by default — it is a candidate. | Any claim presented as observed fact. |
| Approval record | A logged human decision authorizing something to move. | That the decision was made, by whom, when. | The correctness of the thing approved. |
| Report | The finished deliverable assembled from the above. | Claims whose chain back to verified data is visible. | Claims with a broken or missing chain. |

*Table 3.1 — Labels are not judgments about quality. They are categories of epistemic status.*

![A taxonomy of five equal parallel boxes stacked from raw to finished — raw data, verified data, generated artifact, approval record, and report — each with a reserved definition slot; colour marks epistemic status rather than quality, with the generated artifact flagged as not-evidence-by-default and the report as the terminal product](../images/03-the-verified-brand-data-contract-fig-01.png)
*Figure 3.4 — The five epistemic-status labels*

---

I want to be precise about what the agent can do in this workflow and what it cannot, because the confusion between those two things is where most of the trouble originates.

The agent is very good at extraction. Give it a folder of files and ask it which files are present, what paths they live at, and what their contents look like at a summary level — it handles that efficiently. Give it a prompt and a set of inputs and ask it to produce a formatted output — it does that too. It can detect when something is missing from a set that should be complete. It can surface relationships between pieces of content that a human reviewer skimming quickly might not notice. It can check whether an output conforms to a template, whether all required sections are present, whether the log entries are structurally valid.

What it cannot do is confer legitimacy on a source by summarizing it. This is the hard boundary, and it is worth stating directly because the agent's summaries can be so fluent and so confident that they create the impression of authority they do not possess. A summary of a source is not evidence that the source is adequate for the claim being made. That judgment — adequacy for the decision at hand — requires a human who understands the decision and can evaluate whether the evidence is sufficient to support it.

![A triangular systems diagram with three corner nodes — Scope, Approval, Verification — each pointing toward a central Accountable Output node; the three questions are concurrent, not sequential, and should all have answers before the workflow begins](../images/02-the-reallocation-principle-fig-03.png)
*Figure 3.2 — The agentic supervision scaffold (shared with Chapter 2)*

<!-- → [DIAGRAM: Agentic supervision three-question scaffold — Scope (what is the agent allowed to do?), Approval (who decides whether the output moves forward?), Verification (what evidence would make the output defensible?). A triangular arrangement, with each question pointing toward the human decision in the center. Caption: The three questions are not sequential. They should all have answers before the workflow begins.] -->

The practical structure for holding this boundary is what Madison calls the recipe: a small, explicit, auditable workflow description. Inputs, steps, outputs, gate, log. The recipe does not need to be long. It needs to be specific enough that someone who did not run it can tell what happened, and complete enough that the gaps it produces are named rather than smoothed over.

Here is what a recipe for this kind of work looks like in its minimal useful form. Inputs: source files, URLs, screenshots, analytics exports, prompts, logs, and report templates. Steps: label each input by its epistemic status; connect outputs back to sources; record every transformation; flag every gap where the chain is broken or thin; write a provenance note. Outputs: a source map, a missing-evidence list, and a short paragraph suitable for inclusion in the report that describes the provenance of its claims. Gate: no strategic recommendation moves forward unless the source chain behind it is visible. Log: store source paths, run IDs, and every gap that was not resolved.

![A process flowchart of the minimal recipe structure — Inputs, Steps, Outputs, a prominently emphasized Gate, and Log — connected by single forward arrows, with the agent preparing the ground at Inputs and Steps and the human crossing at the emphasized Gate, whose decision is recorded into the Log](../images/03-the-verified-brand-data-contract-fig-03.png)
*Figure 3.5 — The recipe structure*

The gate is the professional moment. The AI prepares the ground on one side of it. The accountable practitioner crosses it.

---

What makes this concrete is tracing an actual claim. Take a statement like: *the category is shifting toward trust messaging*. That is the kind of statement that tends to appear in brand strategy reports without much ceremony, as though it were simply known. But it is not simply known. It came from somewhere. The question is: where?

Follow it backward. It appeared in a report. The report was generated from a template populated by a recipe run. The recipe drew on a summarization of several source documents — analytics exports, a client-provided competitive landscape, a prompt that asked the model to identify directional trends. The model identified the trend toward trust messaging as a pattern across those sources. The sources themselves were a mix of the client's own data and several public-domain category analyses that a junior practitioner pulled and included in the working folder.

Now the question becomes specific: is that chain adequate for the claim? The sources are real. The transformation is logged. But the public-domain analyses — were they checked for date, for methodology, for whether they actually cover the category in question? The model surfaced the pattern; was that pattern also visible on direct inspection of the sources by a human reviewer? The client's data — does it support the claim independently, or only in combination with the external analyses?

These are not gotcha questions. They are the ordinary questions of professional adequacy, and they have determinate answers. Either the chain supports the claim or it does not. If it does not, the provenance note says so directly, and the claim either gets qualified or gets cut.

![A provenance-chain diagram tracing one strategic claim backward — the claim at the top descends through intermediate artifacts (a report, a template, a recipe run, a model summarization) down to a row of source documents; one descending link carries a visible break labelled "source not checked for date/methodology," and one lower node is flagged as a generated artifact, not evidence by default](../images/03-the-verified-brand-data-contract-fig-02.png)
*Figure 3.3 — The broken provenance chain*

<!-- → [CHART: A broken chain visualization — a claim at the top, with lines tracing back through intermediate artifacts to source documents. One line has a break labeled "source not checked for date/methodology." Another terminates in a generated artifact labeled "not evidence by default." Caption: The break does not invalidate the whole chain. It shows exactly where the human review needs to focus.] -->

The point of the contract is not to make the work perfect before it moves forward. The point is to make the imperfections visible so that the practitioner can make a defensible judgment about whether they matter for the decision at hand. Sometimes thin evidence is adequate because the decision is low-stakes. Sometimes apparently strong evidence is inadequate because the decision is irreversible. The contract does not make that call. It gives you the information to make it.

---

There is a particular temptation in this work that I want to name directly, because it operates below the level of conscious intention and causes most of the professional failures of the kind we started with.

Generated text is fluent. It is formatted. It sounds authoritative. And because it sounds authoritative, there is a constant pull toward treating it as evidence — toward letting the finished quality of the artifact do the work that should be done by the source chain behind it. A model summary of a competitive landscape sounds like a competitive analysis. A model-generated trend statement sounds like observed data. The output has the surface properties of the thing you need without necessarily having the epistemic properties of the thing you need.

Madison's posture on this is explicit: generated text is an artifact, not evidence by default. An artifact can become trustworthy — when its claims are traceable, when its inputs are logged, when a human has reviewed the chain and judged it adequate. But it does not arrive trustworthy. It arrives useful, which is a different thing.

The recipe structure operationalizes that posture. The label system — raw data, verified data, generated artifact, approval record, report — is not bureaucratic pedantry. It is a way of keeping track of which things in your working folder have epistemic status and which things are still candidates. You can work with candidates. You can build on them, transform them, format them. You cannot cite them in a strategic recommendation without first moving them from candidate to verified, and moving them requires the human review that the gate enforces.

| Boundary | What it covers |
|---|---|
| Verified | Local files, raw records, cited public pages, approval notes. |
| Model judgment | Summaries and suggested source relationships. |
| Human judgment | Adequacy of the evidence for a business decision. |
| Out of scope | Pretending generated text is original evidence. |

*Table 3.2 — The boundary exists to protect the practitioner, not to limit the agent.*

---

The running project task in this chapter is simple and serious: trace one brand claim from a report back to a log, a recipe, and a source. If the chain holds, write the provenance note that would appear in the report. If the chain breaks, write exactly where it breaks and what would repair it.

That second outcome is not a failure. It is the system working. A break you can see and describe is a break you can fix or qualify. A break you cannot see is the one that ends up in the meeting, stalling the decision, causing the quiet person with the seniority to ask the question.

The artifact you produce from this task has a name in Madison: the provenance note. It is short — short enough to be used in review, short enough that a client can read it in thirty seconds and understand where the supporting evidence came from. It is not a methods section. It is not a disclaimer. It is a plain-language account of the source chain for the claims in the report, including an honest statement of what the chain does not establish.

If the evidence is thin, you write that it is thin. Not in language designed to soften the thinness, but directly. The provenance note that says *the competitive landscape analysis draws on three public-domain sources from 2021-2022 and has not been independently corroborated by the client's own data; the trend characterization should be treated as directional rather than definitive* is a more useful document than the one that says *this analysis is supported by a comprehensive review of available category intelligence*. The first version tells the decision-maker what they need to know. The second version sounds like it is protecting the practitioner.

It is protecting the practitioner from the wrong thing.

---

The verification checklist that closes this chapter is not a box-ticking exercise. It is a list of the conditions that need to hold before an artifact can cross the professional boundary from working material to decision-support.

Raw inputs and generated artifacts are not confused. Every report claim points backward to evidence. Missing links are named, not smoothed over. Logs and human reports tell the same story. The provenance note is short enough to be used in review.

There are two kinds of checking implied by that list. Machine conformance is what the agent can do: verify that files exist at the expected paths, that logs contain the required fields, that the report template is fully populated. Human adequacy is what the accountable practitioner must do: verify that the work is good enough for the decision it is supposed to support. The agent can tell you the chain is structurally complete. Only the human can tell you whether it is good enough.

That distinction — conformance versus adequacy — is the whole architecture of Madison's posture. Not less AI. Better division of labor. Use the agent for the work it does efficiently and correctly. Reserve for the human the work that requires judgment, taste, accountability, and professional standing.

The meeting goes differently when those boundaries are held. The question still gets asked — *where did that come from?* — but now the answer is ready, and the answer is the chain. Here is the source. Here is the transformation. Here is the gap, and here is why I judged it acceptable for this decision. Here is the human who reviewed it and approved it to move forward.

That is what a verified brand data contract looks like in practice. Not a guarantee of correctness. A demonstration of professional accountability.

---

## LLM Exercises

**Exercise 1 — Trace a claim**

Take a strategic claim from a brand report you have access to (or construct a plausible one from the source material in this chapter). Using the recipe structure — inputs, steps, outputs, gate, log — trace the claim backward to its sources. At each step, label the material by its epistemic status: raw data, verified data, generated artifact, approval record, or report. Write the provenance note. If the chain breaks, identify exactly where and name what would repair it.

Prompt suggestion: *"I'm going to give you a brand claim and a set of source materials. Help me trace the claim back through each source, label the epistemic status of each link in the chain, identify any breaks, and draft a provenance note suitable for inclusion in the report."*

**Exercise 2 — Design a gate**

For a workflow you use or have observed, write a gate condition: the specific, testable criterion that must be met before an artifact can move from working material to decision-support. The gate should be concrete enough that two practitioners would agree on whether it has been passed. Describe what the agent checks (conformance) and what the human checks (adequacy). Identify what information the human needs in order to make the adequacy judgment.

Prompt suggestion: *"Here is a workflow description. Help me design a gate condition that separates the agent's conformance checks from the human's adequacy judgment. Give me the gate as a set of yes/no questions, with the last question requiring human judgment to answer."*

**Exercise 3 — Write the honest provenance note**

Take a piece of supporting evidence that you would characterize as thin — a source that is dated, narrow in scope, or not independently corroborated — and write the provenance note as if you were including it in a professional report. The note should accurately describe the chain, including the limitations, in language that a client can read in thirty seconds and use to calibrate how much weight to place on the claim it supports. Then write the version of the note that obscures those limitations. Compare them. What does the second version protect? What does it risk?

Prompt suggestion: *"I have a piece of supporting evidence that is thin — here are its limitations. Help me write two versions of a provenance note: one that describes the chain accurately including its gaps, and one that presents the same evidence in a way that obscures those gaps. Then help me articulate what each version is protecting and what each is risking."*

---

## Prompts

### Figure 3.1 — Looks done vs is defensible
**Files:** ../images/03-the-verified-brand-data-contract-fig-04.svg · ../d3/03-the-verified-brand-data-contract-fig-04.html
**Prompt:** Render a brutalist two-column comparison split by a central ink boundary — left column "what polish conveys" (confidence, authority, recommendation) in secondary grey, right column "what defensibility requires" (source chain, transformation log, human adequacy judgment) in red to carry the weight. Three empty rounded rows per column. Hardcoded palette (ink #2a1a0e, red #C8102E, secondary #545454, border #D4D4D4, fill #F5F5F5, white #FFFFFF), no arrows, no icons.

### Figure 3.2 — The agentic supervision scaffold (shared with Chapter 2)
**Files:** ../images/02-the-reallocation-principle-fig-03.svg · ../d3/02-the-reallocation-principle-fig-03.html
**Prompt:** Reuse the Chapter 2 supervision-frame figure — a brutalist triangle of Scope, Approval, Verification nodes around a central red Accountable Output, with each corner's guiding question beside it and no implied sequence. Same hardcoded palette and conventions as Figure 2.3.

### Figure 3.3 — The broken provenance chain
**Files:** ../images/03-the-verified-brand-data-contract-fig-02.svg · ../d3/03-the-verified-brand-data-contract-fig-02.html
**Prompt:** Render a brutalist top-down provenance trace — a red claim node at the top descending through a report and a dashed-outline generated model summary down to source nodes; draw single-headed downward arrows, and break exactly one descending link with a visible gap and a red JetBrains Mono note "source not checked for date/methodology." Keep intact links solid; only the one break is interrupted. Hardcoded palette (claim/break #C8102E, intact links #2a1a0e, generated artifact #C8860E, sources #545454, white #FFFFFF).

### Figure 3.4 — The five epistemic-status labels
**Files:** ../images/03-the-verified-brand-data-contract-fig-01.svg
**Prompt:** Render a brutalist taxonomy of five equal stacked boxes — raw data, verified data, generated artifact, approval record, report — each with a reserved definition slot. Colour encodes epistemic status not quality: neutral raw, supportive verified and approval record, cautionary generated artifact, dominant report. Hardcoded palette (ink #2a1a0e, red #C8102E for report, secondary #545454, ochre #C8860E for the generated-artifact caution band, border #D4D4D4, white #FFFFFF), no arrows, no ranking.

### Figure 3.5 — The recipe structure
**Files:** ../images/03-the-verified-brand-data-contract-fig-03.svg
**Prompt:** Render a brutalist five-stage flowchart — Inputs, Steps, Outputs, an emphasized Gate, Log — connected by single forward arrows, with the Gate as the strongest red element and a thin connector from Gate to Log. Annotate agent-prepares near Inputs/Steps and human-crosses at the Gate. Hardcoded palette (Inputs/Steps/Outputs secondary #545454, Gate red #C8102E, Log ochre #C8860E, arrows #2a1a0e, white #FFFFFF), no literal door or lock imagery.
