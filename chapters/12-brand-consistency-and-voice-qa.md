# Chapter 12 — Brand Consistency and Voice QA
*The difference between a brand that sounds consistent and one that sounds the same.*

The website was confident and technical. The email was warm and conversational. The ad was urgent and punchy. The deck was formal and structured. Run a quick AI pass to unify them — tighten the vocabulary, align the sentence rhythms, smooth the tone variation — and you get something consistent. You also get something worse.

What happened to the website is that its technical confidence, the thing that made it credible to a reader who had arrived with a specific problem and was evaluating whether the product could solve it, got softened toward the middle register of the other touchpoints. What happened to the email is that the warmth that made recipients feel like a person had written it got replaced with something that sounds like a brand. What happened to the ad is that the urgency that drove clicks got rounded down to the tone level of the deck. The deck alone, being the most formal artifact, came out relatively intact.

Consistency improved. Brand judgment got worse. And the practitioner who ran the pass now owns a set of assets that are more similar and collectively less effective than what they started with.

The problem here is a category error: treating consistency as uniformity. A brand is not one voice saying one thing in one register forever. A brand is a recognizable identity that adapts — deliberately, with accountability — to channel, audience, and purpose. The website talks to a buyer evaluating a purchase. The email talks to a customer who already chose. The ad intercepts someone who was not looking. The deck lives in a room with a client who is deciding whether to trust you with something important. Those contexts require different registers, and the differences are not failures of brand discipline. They are evidence of it.

---

What the QA audit is trying to find is not difference. It is the difference between *intentional adaptation* and *drift*.

Drift is what happens when no one is accountable for how a touchpoint sounds. The email was written by a junior writer on a deadline who defaulted to casual because it felt right. The deck was assembled by the account lead who copied boilerplate from a previous engagement and did not notice that the boilerplate was from a brand with a different positioning. The ad was written by an agency that never received the voice guide and is working from the brand guidelines PDF that the client sent, which is three years old and does not reflect the voice evolution since the rebrand. These are not intentional adaptations. They are accidents that accumulate into incoherence.

Intentional adaptation is something different. The email is warm because the brand strategy team decided that post-purchase communication should sound human, that a customer who has already bought deserves a different register than a prospect being converted. That decision is documented. The voice guide says so. The difference from the website is not a defect — it is a policy.

The QA matrix exists to make that distinction explicit and auditable. Every difference it finds gets classified: is this a rule violation, or is this a documented adaptation? If it is a rule violation, it needs a severity rating, a recommendation, and an owner. If it is a documented adaptation, it gets noted as such and passes. If it is ambiguous — if the variation looks intentional but no one can point to a rule that permits it — that is the most important finding in the matrix, because it reveals a gap in the brand documentation rather than a gap in execution.

| Touchpoint | Rule Reference | Issue Description | Evidence (specific line or element) | Severity | Recommendation | Owner | Decision |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Homepage hero | Claims policy §2.1 (no unqualified superlatives) | Unsupported superlative claim | "the most trusted platform in the industry" | Critical | Rewrite to a warranted claim or supply third-party proof | T. Okafor | Held — pending proof |
| Welcome email | Voice guide §3.4 (12–16 words, email) | Sentence length exceeds channel norm | Opening sentence runs 27 words | Major | Split into two sentences in next revision before send | R. Devi | Revise before launch |
| Product page | Voice guide §3.2 (active voice primary) | Passive construction cluster | "results are delivered," "decisions are supported" | Minor | Convert to active voice in next cycle | L. Park | Logged for next cycle |
| Loyalty email | Voice guide §1.1 (warm post-purchase register) | Tone slightly warmer than website | Casual greeting, first-name address | Note | No action — documented adaptation | A. Chen | Pass — intentional |

*The rule reference column is not optional. An issue without a rule citation is an opinion. The matrix trades in evidence, not taste.*

![Schematic of one QA matrix row as eight aligned cells — touchpoint, rule reference, issue, evidence, severity, recommendation, owner, decision — with the rule-reference cell weighted as load-bearing and a four-state severity indicator.](../images/12-brand-consistency-and-voice-qa-fig-01.png)
*Figure 12.1 — The QA matrix structure*

---

The recipe for this chapter requires inputs that are often partly missing in practice, and it is worth being direct about what happens when they are missing.

Inputs: brand rules, voice guide, sample touchpoints, a claims/proof map, accessibility requirements, and review criteria. Steps: inspect each touchpoint against those inputs — rule alignment, claim support, tone, jargon, accessibility, contradictions, and channel fit — assign severity, recommend action, capture the human decision. Gate: severe issues block launch until an owner has made and documented a decision. Log: touchpoint, issue, severity, recommendation, decision.

The missing-inputs problem is common. A brand rules document that predates the last rebrand. A voice guide that describes aspirational voice rather than operational guidance — that says the brand is "approachable but authoritative" without specifying what that means for sentence length, vocabulary level, or how claims should be sequenced. Accessibility requirements that no one has formally adopted for this account. When the inputs are thin, the QA matrix produces findings that are harder to defend — not because the findings are wrong, but because they cannot be tied to a documented standard. The practitioner has to choose between writing findings to a standard they are constructing in the moment, which is legitimate but should be labeled as such, or noting that the finding reflects professional judgment in the absence of documented rules.

![Systems diagram of QA inputs: brand rules and voice guide feed review criteria the agent applies to touchpoints, with an accessibility check running in parallel and the claims/proof map supplying the evidentiary layer; all findings converge in the QA matrix and close at a human decision.](../images/12-brand-consistency-and-voice-qa-fig-02.png)
*Figure 12.2 — The recipe input chain*

<!-- → [DIAGRAM: The recipe input chain — brand rules and voice guide feed the review criteria, which the agent applies to the touchpoints; accessibility requirements run as a parallel check; the claims/proof map provides the evidentiary layer for claim-related findings; all findings flow into the QA matrix; human decisions close each row. Caption: Missing inputs do not stop the process — they change the epistemic status of the findings. Label gaps honestly.] -->

The agent's role in this workflow is comparison at scale and consistency checks. Give it the voice guide and a set of touchpoints and ask it to identify vocabulary that falls outside the documented register, sentence structures that do not match the established patterns, jargon that the guide flags for avoidance — it does that efficiently and without the fatigue that makes human reviewers miss the fifteenth instance of a problem they have already seen fourteen times. It can run an accessibility check against WCAG contrast requirements, flag missing alt text, identify reading-level mismatches between a stated audience and the copy's actual complexity.

What it cannot do is decide whether the warmth in the email is a defect or a feature. That decision requires a human who knows the brand's strategy, who can evaluate the specific context of that touchpoint, and who is willing to be accountable for the judgment. The agent surfaces the difference. The practitioner names what kind of difference it is.

---

Severity is the part of the matrix that most junior practitioners underuse, and it matters because not all findings are equal and treating them equally creates noise that obscures the things that actually need attention.

Critical severity means the issue blocks launch. A claim that contradicts a legal restriction. A contrast ratio below the accessible minimum on a primary CTA. A brand positioning statement that directly contradicts an approved statement in a live campaign. These do not need nuance — they need resolution before anything ships.

Major severity means the issue should be addressed before launch if at all possible, and if it cannot be addressed, the decision to ship anyway needs to be documented by a named owner. An off-brand tone in a high-traffic touchpoint. An unsupported performance claim in a context where it will receive scrutiny. A voice register that drifts significantly from the established standard without a documented rationale.

Minor severity means the issue is worth noting and should be addressed in the next revision cycle, but it does not block the current launch. A vocabulary choice that is marginal — not wrong, just not the strongest option by brand standards. A structural pattern that slightly diverges from the established template.

A note is an observation that may be useful context but does not constitute a finding. A slight tone warmth variation that probably reflects the author's natural register. A word that is on the borderline of the jargon list.

| Severity | Definition | Triggering Condition | Example (brand/copy QA) | Action Required |
| --- | --- | --- | --- | --- |
| Critical | Blocks launch | Issue creates legal, accessibility, or brand-integrity risk if shipped | CTA contrast ratio below WCAG 4.5:1; claim contradicts a legal restriction | Resolve before anything ships |
| Major | Should be fixed before launch | Off-brand or unsupported in a high-visibility context | Off-brand tone in a high-traffic touchpoint; unsupported performance claim | Address before launch, or a named owner documents the decision to ship |
| Minor | Worth noting, non-blocking | Marginal deviation from brand standard | Sub-optimal vocabulary choice; slight template divergence | Address in the next revision cycle |
| Note | Observation, not a finding | Variation likely reflects natural register, not a defect | Slight tone warmth in author's voice; borderline jargon word | No action required; recorded as context |

*Severity exists to prioritize, not to signal alarm. A matrix full of critical findings is not a rigorous audit — it is an audit that has lost the ability to communicate.*

![Four severity tiers ordered from critical to note, each paired with the action it requires, with a gating glyph distinguishing the launch-decision weight of critical and major from the revision-cycle weight of minor and note.](../images/12-brand-consistency-and-voice-qa-fig-03.png)
*Figure 12.3 — Severity levels*

The distribution of severity across a real QA matrix is information. A set of three touchpoints with one critical finding, three major findings, and twelve minor findings is a different situation from a set with eight critical findings. The critical finding needs immediate owner attention. The twelve minor findings need a revision cycle. Running them together in the same conversation, at the same urgency level, is how QA matrices become noise generators that practitioners learn to ignore.

---

Voice is the hardest part of the matrix to write defensibly, and the most important to get right, because it is the dimension most likely to be contested.

A voice comment that says "this doesn't sound like the brand" is not a finding. It is an opinion, and it invites an argument the QA process is not designed to have. A voice comment that says "this paragraph uses passive construction in four consecutive sentences; the voice guide specifies active voice as a primary standard (Section 3.2); specific lines: 'results are delivered,' 'decisions are supported,' 'teams are empowered'" is a finding. It cites the rule, quotes the specific evidence, and makes the issue falsifiable — either the guide says that or it does not, and either those sentences use passive construction or they do not.

The discipline is to write every voice finding to a rule and a specific line. Not "the tone feels off" but "the email opens with a self-deprecating joke; the voice guide characterizes the brand as 'confident without arrogance' and specifically flags self-deprecation as inconsistent with the brand character (Section 4.1, Tone Boundaries)." Not "this is too formal" but "average sentence length in this section is 24 words; the voice guide recommends 12–16 words for email copy (Section 3.4, Channel Norms)."

When there is no rule to cite, the finding cannot be written as a rule violation. It can be written as a recommendation: "consider revising — this register may not serve the audience context, though no documented standard currently governs email tone. Flagging for review." That note is honest about its own epistemic status. It is useful. And it implicitly surfaces the gap in the documentation, which is information the brand team needs.

![Side-by-side comparison: a weak, opinion-based voice finding shown as a lone isolated node, against a strong, rule-cited finding built as a connected chain of rule reference, quoted evidence, finding statement, severity, recommendation, and owner.](../images/12-brand-consistency-and-voice-qa-fig-04.png)
*Figure 12.4 — Voice finding anatomy*

<!-- → [DIAGRAM: Voice finding anatomy — a single finding unpacked into its components: rule reference (with section number), specific evidence (quoted lines), finding statement, severity, recommendation, owner. Show a weak version (opinion-based) and a strong version (rule-cited) of the same finding side by side. Caption: The test for a voice finding: can someone disagree with it by pointing to the rule? If not, it's an opinion. Write it differently.] -->

---

The accessibility check runs parallel to the voice and consistency check, and it deserves more attention than it typically receives in brand QA workflows because it is both the most objectively verifiable dimension and the one most often treated as a technical afterthought.

Contrast ratios are computable. If your body text is rendered in a color that falls below the WCAG 4.5:1 minimum contrast ratio against its background, that is not an opinion — it is a finding with a specific numeric value, a documented standard it violates, and a specific remediation (change the foreground color to reach the minimum). The `contrast-check` script handles this; the agent can run it against the touchpoint's color values. The finding writes itself.

Alt text is either present or absent. Reading level is measurable. These are the easy parts of accessibility QA, and they should appear in every matrix as a matter of professional standard, not as optional additions when accessibility happens to be top of mind.

The harder part is judgment about whether the accessible version is also the effective version — whether the contrast-compliant color still works in the design, whether the simplified language still carries the brand voice, whether the alt text description serves both screen reader users and SEO simultaneously. Those are human judgment calls that the matrix surfaces but cannot resolve. They get severity ratings and owners, the same as everything else.

---

The running project task is an audit of three touchpoints: the matrix populated with every column, human decisions recorded in the decision column, and a brief revised guidance note identifying any gap in the brand documentation that the audit revealed. That last element — the gap note — is often the most valuable output of a QA process and the one most consistently omitted. Every time a practitioner has to write "finding reflects professional judgment in the absence of a documented standard," they are generating evidence that the documentation needs updating. The gap note captures that evidence before it disappears back into the workflow.

The verification checklist runs: brand rules are cited; voice comments point to specific lines; accessibility issues are included; the matrix distinguishes contradiction from useful variation; human decisions are recorded. Machine conformance is what the agent checks — are all columns populated, do rule citations resolve to existing documents, are severity levels within the defined range. Human adequacy is what the practitioner checks — is the distinction between defect and adaptation being made correctly, are severity ratings proportionate to actual risk, are the right people named as owners for the right findings.

The goal is a set of touchpoints that sounds like one brand thinking carefully about context, not one brand saying the same thing everywhere. Uniformity is easy and fragile. Coherent variation is hard and durable. The matrix is how you tell the difference between them, document the difference, and hold the right people accountable for the decisions that make the difference intentional.

---

## LLM Exercises

**Exercise 1 — Audit three touchpoints**

Select three brand touchpoints from the same organization — a website page, an email, and either an ad or a deck section. Using the QA matrix structure, audit each one against the brand rules and voice guide. For each finding, write the rule reference, the specific evidence, the severity, a recommendation, and an owner. Classify each finding as rule violation, undocumented adaptation, or documentation gap. When the matrix is complete, write a one-paragraph gap note identifying any rules or standards that your findings revealed to be absent or ambiguous.

Prompt suggestion: *"I'm going to give you three brand touchpoints and a voice guide. For each touchpoint, identify every place where the copy deviates from the documented brand rules. For each finding: cite the specific rule, quote the specific line, rate severity as critical/major/minor/note, and recommend an action. Classify each finding as rule violation, intentional adaptation (if supported by documentation), or documentation gap."*

**Exercise 2 — Voice finding discipline**

Take five voice-related observations about a piece of copy — observations in the form of opinions ("this doesn't sound right," "the tone feels off," "this is too formal") — and rewrite each one as a defensible finding. Each rewrite must cite a rule, quote specific evidence, and be falsifiable: someone should be able to disagree by pointing to the rule or the evidence. For any observation that cannot be rewritten as a defensible finding because no rule covers it, write the recommendation in its appropriate form and add the documentation gap note.

Prompt suggestion: *"Here are five voice observations about a piece of copy, written as opinions. Help me rewrite each one as a defensible QA finding with a rule citation, specific evidence, and a severity rating. For any observation that cannot be grounded in a documented rule, help me write it as a recommendation with a documentation gap note."*

**Exercise 3 — Defect versus adaptation**

Review a QA matrix with ten findings and classify each as: rule violation requiring remediation, intentional adaptation that should be documented in the voice guide, or unclear — could be either. For the rule violations, confirm the severity and owner. For the intentional adaptations, write the documentation addition that would make them officially sanctioned. For the unclear findings, write the question you would ask the brand team to resolve the ambiguity, and describe what the answer would need to contain to close the finding in either direction.

Prompt suggestion: *"Here is a QA matrix with ten findings. Help me classify each as rule violation, intentional adaptation, or unclear. For violations, confirm severity and owner. For adaptations, draft the voice guide addition that would document them. For unclear findings, write the clarifying question for the brand team and describe what answer would resolve the finding."*

---

## Prompts

### Figure 12.1 — The QA matrix structure
**Files:** ../images/12-brand-consistency-and-voice-qa-fig-01.svg
**Prompt:** Structural schematic of one QA matrix row as eight aligned cells on white — touchpoint, rule reference, issue, evidence, severity, recommendation, owner, decision — with the rule-reference cell drawn at a heavier stroke to mark it as load-bearing and a four-state severity indicator inside the severity cell. Brutalist palette only, JetBrains Mono numerals, no baked example text.

### Figure 12.2 — The recipe input chain
**Files:** ../images/12-brand-consistency-and-voice-qa-fig-02.svg · ../d3/12-brand-consistency-and-voice-qa-fig-02.html
**Prompt:** Systems diagram on white: brand rules and voice guide feed review criteria applied by the agent to touchpoints, with an accessibility check running as a parallel ochre dashed stream and the claims/proof map supplying the evidentiary layer, all converging in the QA matrix and closing at a red human-decision node. Single-headed arrows, EB Garamond title, Inter labels.

### Figure 12.3 — Severity levels
**Files:** ../images/12-brand-consistency-and-voice-qa-fig-03.svg
**Prompt:** Four-tier comparison panel ordered critical to note, each row paired with the action it requires, using a graduated ink-to-secondary treatment so descending consequence reads at a glance and a small gating glyph separates launch-decision weight (critical, major) from revision-cycle weight (minor, note). White canvas, no alarm iconography, brutalist palette only.

### Figure 12.4 — Voice finding anatomy
**Files:** ../images/12-brand-consistency-and-voice-qa-fig-04.svg · ../d3/12-brand-consistency-and-voice-qa-fig-04.html
**Prompt:** Side-by-side comparison on white: a weak opinion-based finding as a single faint dashed node on the left, against a strong rule-cited finding on the right built as a connected chain — rule reference (red anchor node), quoted evidence, finding statement, severity, recommendation, owner — joined by single-headed arrows. EB Garamond title, Inter labels, brutalist palette only.
