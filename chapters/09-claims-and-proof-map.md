# Chapter 9 — Claims and Proof Map
*Copy review is a risk and evidence practice, not a polish pass.*

Here is a landing page headline that is not obviously wrong: *Trusted by modern teams. Faster workflows, more intuitive design, built for the way you work today.* Read it quickly and it holds together. The rhythm is reasonable. The vocabulary is current. Nothing jumps out as false.

Read it slowly, with the question *what kind of claim is this and what would prove it*, and four completely different problems appear in the same sentence.

"Trusted" is a credential claim — it implies a record of verified reliability, the kind of thing that wants a testimonial count, a case study, a third-party review score. "Faster" is a comparative performance claim — faster than what, measured how, under what conditions — the kind of claim that can attract regulatory attention if it cannot be substantiated with a methodology. "More intuitive" is a subjective audience claim dressed as an objective one — intuitive for whom, measured against what baseline — the kind of claim that is almost never supported and almost always present in software copy. "Built for the way you work today" is puffery — a rhetorical gesture with no claim content, legally safe but strategically empty.

Four claims. Four different proof requirements. Four different risk profiles. One smooth paragraph that makes them all invisible to a quick reader, including the quick reader who approved the copy.

The problem is not that the copy is dishonest. Most brand copy is not written to deceive — it is written to persuade, under time pressure, by people who are not thinking about the difference between "this sounds right" and "this can be defended." The problem is that copy that cannot be defended creates exposure: legal exposure if a performance claim is challenged, reputational exposure if an audience claim turns out not to match the actual audience, strategic exposure if a credential claim falls apart in due diligence. Junior practitioners who can make that exposure visible before the copy ships create enormous value. That is what the claims and proof map is for.

---

The map starts with a discipline that sounds simple and is harder than it looks: extracting claims one at a time, in isolation.

Copy is written to flow. One sentence builds on the next; claims embed themselves in syntax; the paragraph-level argument carries readers past individual assertions before they have time to evaluate them separately. That is partly what makes copy persuasive, and it is exactly what makes copy difficult to audit. The extraction step breaks the flow deliberately. You are not reading the copy as a reader — you are reading it as an analyst, pulling each claim out of its context and setting it down in a row by itself where it can be examined.

A claim, for purposes of this exercise, is any assertion about the product, brand, service, or category that a reader might take as a reason to believe, act, or choose. Not every sentence is a claim. "Discover what's possible" is not a claim — it is a navigation instruction dressed as inspiration. "Reduce onboarding time by 40%" is a claim. "The industry's most trusted compliance platform" is a claim. "We're on a mission to make work feel human again" sits in between — it is a claim about intent, which has a different risk profile than a claim about outcomes.

| Claim type | Definition | Example | Typical proof requirement | Typical risk |
|---|---|---|---|---|
| Factual | A verifiable statement of fact | "Available in 14 languages" | A source or record | Low–medium |
| Comparative | An assertion relative to a named alternative | "Faster than the leading tool" | Methodology + named comparison point | High |
| Credential | An implied record of reliability or status | "Trusted by modern teams" | Documentation of the credential | Medium–high |
| Performance | A quantified outcome claim | "Reduce onboarding time 40%" | Numbers with defined conditions | High |
| Audience | A claim about who it is for or how they feel | "Built for skeptical buyers" | Audience data | Medium |
| Puffery | Rhetorical gesture with no claim content | "The way you work today" | None — asserts nothing | Low |
| Opinion | A subjective view held by a speaker | "We think it's the cleanest UI" | Attribution to the holder | Low |

*The taxonomy exists to make proof requirements visible, not to eliminate claims. Some puffery is fine. Unsupported performance claims are not.*

![The seven claim categories arranged as equal-weight nodes ordered by the proof burden they demand — performance and comparative at the high-burden end, puffery at the no-proof end — with puffery marked as the structural outlier.](../images/09-claims-and-proof-map-fig-01.png)
*Figure 9.1 — Claim type taxonomy*

Once the claims are extracted and sitting in rows, the next step is classification. Madison uses seven categories: factual claim, comparative claim, credential claim, performance claim, audience claim, puffery, and opinion. The categories are not about judgment — a credential claim is not better or worse than an opinion — they are about proof requirements. A factual claim needs a source. A comparative claim needs a methodology and a named comparison point. A credential claim needs documentation of the credential. A performance claim needs numbers with defined conditions. An audience claim needs audience data. Puffery needs nothing because it asserts nothing. An opinion needs attribution to a speaker who holds it.

The classification step is where the agent adds real value. Give it the extracted claims and ask it to classify each one and note what proof requirement the classification implies — it does that consistently and at a speed that would take a human practitioner significantly longer. What the agent cannot do is assess whether the proof you have is adequate for the risk context you are operating in. That assessment depends on factors the agent does not have: the regulatory environment for the category, the client's history with claims-related challenges, the channel where the copy will run, and the practitioner's judgment about how aggressively to challenge the draft.

---

The proof column in the matrix is where the discipline becomes practical. For each claim, you attach whatever supporting evidence exists: a source document, a metric, a testimonial, a screenshot, an approved boilerplate statement, a client-provided data point. Or you write "none" — which is itself information, and the most important information the matrix can produce.

A performance claim with no proof attached is not ready to ship. That is not a stylistic judgment; it is a professional standard. The matrix makes the gap visible in a way that the original copy did not. Where the landing page said "faster workflows" fluently and confidently, the matrix says: *original claim — "faster workflows"; type — comparative performance; proof — none; risk — high; status — needs source or rewrite.*

| Original claim | Type | Proof | Risk | Rewrite | Approval owner | Status |
|---|---|---|---|---|---|---|
| "Trusted by modern teams" | Credential | 4,000 paying teams; no review score | Medium | "Used by 4,000 teams" | Brand lead | Approved with proof |
| "Faster workflows" | Comparative performance | none | High | "Cuts setup from 2 days to 4 hours (Q3 customer data, teams <50)" — pending verification | Legal | Flagged for approval owner |
| "More intuitive design" | Audience | none | Medium | "Most reviewers reached first value without docs (n=120 usability test)" | UX research | Flagged for approval owner |
| "Built for the way you work today" | Puffery | n/a | Low | keep as is | — | Approved as written |
| "Cuts reporting time 40%" | Performance | internal benchmark, 12 accounts | High | "Cuts reporting time ~40% across 12 pilot accounts" with methodology note | Legal | Approved with proof |

*The matrix is not a grading rubric. It is a production tool. "High risk, no proof" is a work item, not a verdict.*

![One row of the claims-and-proof matrix as a horizontal pipeline of linked cells — original claim, type, proof, risk, rewrite, approval owner, status — with the proof and status cells weighted as the load-bearing decision points and four colored end-states at the status terminus.](../images/09-claims-and-proof-map-fig-02.png)
*Figure 9.2 — The claims/proof matrix anatomy*

The risk assessment attaches to each claim independently, and it is a function of three factors: the claim type (comparative and performance claims carry higher inherent risk than puffery or opinion), the proof status (no proof is higher risk than supported proof), and the channel and context (a claim that runs in a regulated category, or in a jurisdiction with active advertising standards enforcement, carries more exposure than the same claim in a lower-stakes context). The matrix does not resolve the risk assessment — that is human judgment — but it gives the practitioner the inputs to make the judgment explicitly rather than implicitly.

---

I want to pause on the rewrite column because it is the most misused part of this workflow.

The rewrite is not an opportunity to make the copy timid. A rewrite that eliminates the claim rather than grounding it has not solved the problem — it has abandoned the strategic intent of the original. If the product genuinely does reduce onboarding time, the goal is not to remove "faster" from the copy; the goal is to get the number, verify the conditions, and write "reduces onboarding time by 40% in teams under 50 people, based on customer data from Q3 2024." That rewrite is more specific, more defensible, and more persuasive than the original, because specificity reads as credibility.

The verification checklist for this chapter includes a line that is easy to skip: *the cleaned copy is still useful, not merely timid.* It is there because the failure mode in the opposite direction from unsupported claims is copy that has been audited into uselessness — every claim softened to an opinion, every performance assertion hedged into a gesture, every credential buried in a qualifier. That copy is defensible and worthless.

The rewrite step should preserve the strategic intent of the claim while grounding it in available proof. If no proof is available and the claim cannot be grounded, the rewrite options are: qualify it explicitly as an opinion or user experience, replace it with a claim that can be supported, or flag it for the approval owner as a strategic choice that requires human sign-off. What it should not do is disappear the claim silently and let the copy ship with a gap where a selling point used to be.

![A decision tree from a claim with no proof: if proof can be found, attach, verify, and rewrite with specifics; if not, either qualify it as opinion with attribution or flag it for the approval owner to remove or hold.](../images/09-claims-and-proof-map-fig-03.png)
*Figure 9.3 — The rewrite decision tree*

<!-- → [DIAGRAM: The rewrite decision tree — starting from "claim with no proof attached," branching into: proof can be found (→ attach and verify → rewrite with specifics), proof cannot be found (→ can claim be qualified as opinion/UX? → yes: rewrite with attribution; no: flag for approval owner → remove or hold). Caption: The tree is a decision aid, not a policy. The approval owner can decide to ship a claim that the tree would flag, with documented reasoning.] -->

---

The approval owner column is where the matrix connects to organizational accountability, and it is the column most likely to be left blank in a first draft.

Every high-risk claim — every unsupported performance claim, every comparative claim, every credential claim that has not been independently verified — needs a named human who is accountable for the decision to include it. Not "legal" or "compliance" as a category, but a specific person who will review the evidence, assess the risk, and document that they approved the claim to move forward. The log entry for that decision is what makes the artifact defensible after the fact: if the claim is challenged, there is a record of what evidence was available, who reviewed it, and what judgment was made.

This is the phase gate in direct form. The agent can extract the claim, classify it, identify the proof gap, and suggest a rewrite. It cannot take responsibility for the consequences of the claim appearing in public. That responsibility attaches to the accountable practitioner who reviews the matrix and approves each line. The gate is not a formality — it is the professional moment that separates copy review from mere proofreading.

| Layer | What it contains | Who is accountable |
|---|---|---|
| Verified | Source documents, metrics, testimonials, screenshots, approved boilerplate | The evidence record |
| Model judgment | Claim classification and rewrite suggestions | The agent — prepared, not approved |
| Human judgment | Risk tolerance, brand fit, final copy approval | The accountable practitioner |

*The model prepares the matrix. The human signs the claim.*

![Three zones — verified evidence, model judgment, and human judgment — with a heavier divider marking the phase gate between what the model prepares and what the human signs.](../images/09-claims-and-proof-map-fig-04.png)
*Figure 9.4 — Evidence boundary*

---

The running project task is a full audit of one page or deck section: a claims/proof table with every column populated, and a cleaned draft of the copy that reflects the decisions the table records. The discipline is in the status column — each claim ends in one of four states: approved with proof, approved as qualified opinion, flagged for approval owner, or removed.

The common mistake is treating the matrix as an editing checklist and moving through it too quickly to think carefully about the approval owner column. A matrix where every approval owner line says "copy team" or is left blank is a matrix that has not yet done its most important work. The value of the exercise is not the classification — that is structural, and the agent handles it — but the explicit chain of accountability from claim to proof to named human decision.

Audit the copy the way a careful reader who does not know your client would read it: assuming nothing, questioning everything, asking for every credential and every number. That reader exists. In the worst cases, they work for a competitor, a regulator, or a journalist. The matrix is the practice of being that reader before the copy ships.

---

## LLM Exercises

**Exercise 1 — Extract and classify**

Take a page of brand or marketing copy — a landing page, a deck section, an email, an ad — and extract every claim into a row of the matrix. For each claim, assign a type (factual, comparative, credential, performance, audience, puffery, or opinion), attach whatever proof you can find or note "none," and assess the risk level as low, medium, or high. Do not rewrite yet. When the extraction is complete, identify the three highest-risk claims and write a one-paragraph note on what evidence would be needed to reduce the risk of each one.

Prompt suggestion: *"I'm going to give you a piece of copy. Extract every claim into a row: original claim, type, available proof, and risk level. Label each claim type using these categories: factual, comparative, credential, performance, audience, puffery, opinion. For proof, note what the claim would need to be substantiated. For risk, rate low/medium/high and explain why."*

**Exercise 2 — The rewrite column**

Take three high-risk claims from Exercise 1 — ideally one comparative, one performance, and one credential — and write two rewrites for each. The first: the rewrite that grounds the claim in the available proof, preserves the strategic intent, and is more specific and credible than the original. The second: the rewrite that hedges the claim into defensibility but loses the persuasive force. Evaluate which rewrite better serves the copy's strategic purpose. For the claims where no proof is available, write the flag note you would give the approval owner, naming the decision they need to make.

Prompt suggestion: *"Here are three high-risk claims from my copy audit. For each one, write two rewrites: one that grounds the claim in the available proof while preserving strategic intent, and one that hedges to defensibility but loses persuasive force. Then write a brief note comparing which serves the copy better. For claims with no proof, write the flag note for the approval owner."*

**Exercise 3 — The accountability audit**

Review a completed claims/proof matrix and populate the approval owner column for every claim rated medium or high risk. For each one, name the specific role or person who should review it, describe what information they need to make the approval decision, and write the log entry that would document their decision once made. If any high-risk claim has no obvious approval owner — no one in the organization whose job includes this kind of accountability — write a note on what that gap reveals about the workflow and what would need to change for the claim to be safely shipped.

Prompt suggestion: *"Here is a claims/proof matrix. Help me populate the approval owner column for every medium and high-risk claim. For each one, suggest who should review it and what information they need. Then help me write the log entry template that would document the approval decision, including what fields should be required."*

---

## Prompts

### Figure 9.1 — Claim type taxonomy
**Files:** ../images/09-claims-and-proof-map-fig-01.svg · ../d3/09-claims-and-proof-map-fig-01.html
**Prompt:** Brutalist taxonomy of the seven claim categories as equal-weight nodes ordered by proof burden, high to low — performance and comparative at the top, puffery at the bottom. Mark puffery as the outlier with an ochre accent. One red; ink and gray otherwise; EB Garamond / Inter / JetBrains Mono.

### Figure 9.2 — The claims/proof matrix anatomy
**Files:** ../images/09-claims-and-proof-map-fig-02.svg · ../d3/09-claims-and-proof-map-fig-02.html
**Prompt:** Brutalist structural schematic of one matrix row as a left-to-right pipeline of seven cells (original claim, type, proof, risk, rewrite, approval owner, status). Weight the proof and status cells heavier; show four colored end-states at the status terminus, with removed in red.

### Figure 9.3 — The rewrite decision tree
**Files:** ../images/09-claims-and-proof-map-fig-03.svg · ../d3/09-claims-and-proof-map-fig-03.html
**Prompt:** Brutalist top-down decision tree from "claim with no proof." Diamonds for decisions, rounded rectangles for actions; single-headed ink arrows. The grounding path and the remove/hold terminus carry red accents; ≤8 nodes.

### Figure 9.4 — Evidence boundary
**Files:** ../images/09-claims-and-proof-map-fig-04.svg · ../d3/09-claims-and-proof-map-fig-04.html
**Prompt:** Brutalist three-zone comparison — verified evidence, model judgment, human judgment — stacked, with a heavier ochre divider marking the phase gate between what the model prepares and what the human signs. Human-judgment zone in red.
