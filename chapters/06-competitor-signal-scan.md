# Chapter 6 — Competitor Signal Scan
*What public messaging reveals, and what it doesn't.*

The first draft came back describing the competitor's brand as "premium, youthful, disruptive, and trustworthy." The account team nodded. The strategist frowned. Because those four words describe approximately every brand operating in the category, and they describe none of them in particular, and they cannot support a single creative decision. You cannot look at "youthful" and figure out what color palette to avoid or what claim structure to counter. You cannot brief a copywriter with "disruptive." The words sound like competitive intelligence. They are actually the absence of it.

What happened? AI was used to scan public-facing materials, and the AI did what language models do well: it found the dominant vocabulary and returned it in the register of a professional summary. The problem is that "premium" is not a signal. It is a category convention, the background noise every brand in that space emits by default. Returning it as an insight is like reporting that the competitors all have websites.

The failure is not that AI was used. The failure is that the artifact crossed a professional boundary — from extracted observation to strategic implication — without evidence, without sourcing, and without the human judgment that the boundary requires.

---

What the competitor scan is actually supposed to produce is something much more specific and much more humble: a matrix of observed signals, each one traceable to a source, each one dated, each one labeled for what it is rather than what it might mean.

Here is what a signal actually looks like. A competitor's homepage headline on a specific date. A CTA button that says "Get the proof" rather than "Learn more." An ad that leads with a customer testimonial and buries the product name. A campaign that ran on LinkedIn but not Instagram. A press release that makes a quantified performance claim. These are facts. They are observable. They have sources. They can be compared across competitors and across time. And if the comparison reveals something — if every competitor in the category is leading with social proof while your client is leading with product specs — that is a pattern worth bringing to a human strategist, labeled carefully as a pattern, with the sources attached.

<!-- → [TABLE: Competitor matrix structure — columns: competitor name, source URL, capture date, headline/primary claim, proof offered, CTA, audience signal, tone label, channel, contradiction flag, human-review note. Caption: The matrix is an observation layer, not a strategy layer. Implications go in a separate labeled section.] -->

The recipe for this chapter is built around that matrix. Inputs: the competitor set, the category terms you are using to bound the comparison, a source list, a date range, and the brand question you are trying to answer. Steps: capture the sources directly — screenshots, URLs with timestamps, downloaded ads — and then extract from each source the specific observable features: positioning language, claims, proof offered, CTA, audience signals, channel choices, tone. Flag contradictions when you find them. Compare patterns across the set. Write human-review notes for every inference that goes beyond the observation. Outputs: the matrix, a source appendix, and a short implication memo that is labeled as interpretation rather than observation. Gate: strategy recommendations stay separate from observations, and the separation is explicit, not implicit. Log: competitor names, URLs or file paths, capture timestamps, and extraction notes.

The date matters more than it seems. A competitive landscape from eighteen months ago may not describe the current market. A campaign that ran during a product launch may not represent the brand's current positioning. When you are reading the matrix, you need to know when each signal was captured, not just what it said.

---

I want to spend some time on the question of what the agent can actually do here, because this is one of the assignments where the capability is highest and the failure mode is most seductive.

The agent is genuinely useful for extraction at scale. Give it a set of captured pages and ask it to identify the primary claim on each one, the proof structure, the CTA, the visible audience signals — it does that efficiently and consistently in a way that a human reviewer skimming quickly would not. It can normalize vocabulary across competitors so that you can compare them: identifying that three out of five competitors are using some form of social proof, even when each one has phrased it differently. It can detect when a competitor's messaging on one channel contradicts its messaging on another, which is a real and useful signal about strategic coherence or inconsistency.

What it cannot do is decide which competitors belong in the set. That decision depends on strategy, market context, and business stakes in ways that are not visible in the public-facing materials themselves. A direct category competitor is an obvious inclusion. But what about the brand that is not technically competing with your client today but is moving in the same direction and will be competing in eighteen months? What about the brand from an adjacent category that is capturing the same audience attention? Those inclusion decisions require someone who understands the client's actual strategic situation, not just the public landscape.

<!-- → [DIAGRAM: The agent-human division in a competitor scan — two columns. Agent column: gather public signals, extract observable features, normalize vocabulary, flag contradictions, identify patterns. Human column: define the competitor set, assess category relevance, interpret strategic meaning, decide implications. Caption: The columns meet at the gate. The agent's outputs become the human's inputs, not the human's conclusions.] -->

The agentic supervision questions apply directly here. Scope: the agent is scanning publicly available signals within a bounded competitor set and date range — it is not inferring private strategy or predicting future moves. Approval: a human brand practitioner reviews the matrix before it moves to a client or a brief. Verification: every observation in the matrix has a source URL or file path and a capture timestamp, so the claim can be checked against the original.

---

The contradiction flag deserves its own attention because it is one of the more valuable things the matrix can surface and one of the things most likely to get smoothed away.

Contradictions in competitor messaging are informative. A brand that positions itself as trustworthy and transparent in its long-form content but uses urgency-pressure tactics in its ads is telling you something about the distance between its brand aspiration and its performance marketing. A brand that leads with sustainability claims on its website but runs no visible advocacy or third-party verification is telling you something about the depth of that commitment. A brand that targets professionals in its copy but uses creative that reads as consumer-facing is telling you something about an internal misalignment or a strategic pivot in progress.

None of those inferences should appear in the matrix as conclusions. They should appear as observations with a contradiction flag and a human-review note that says something like: *homepage positions as transparent, ads use countdown-timer scarcity mechanics — review note: possible misalignment between brand and performance teams, or deliberate bifurcation by audience segment. Human interpretation required.* The note names what was observed, names the possible interpretation, and explicitly holds that interpretation as a candidate rather than a finding.

<!-- → [CHART: Contradiction frequency across a hypothetical competitor set — a simple bar showing how many contradiction flags appear per competitor, with a note distinguishing substantive contradictions (strategy vs. execution) from surface contradictions (tone variation by channel). Caption: Not all contradictions are problems. Some are strategic. The matrix surfaces them; the practitioner decides which kind they are.] -->

The temptation to average contradictions away — to find the central tendency and report it — is strong because it makes the deliverable cleaner. Resist it. The contradiction is often the most strategically useful thing in the matrix. A competitor that is internally inconsistent is potentially vulnerable. A competitor that is consistently consistent across every channel is telling you they have solved a coordination problem your client has not. The matrix should preserve the texture of what was actually observed, not smooth it into a neater picture.

---

There is a second temptation that runs in the opposite direction, and it is the one that produced the first draft I described at the opening: the temptation to turn the observed patterns directly into strategic implications.

The pattern is real. Three out of five competitors are leading with social proof. That is an observation. What does it mean? Maybe the category has matured to the point where functional claims are no longer differentiating and social proof is the new minimum. Maybe one competitor started it and the others followed without thinking carefully. Maybe your client's audience is at a stage in the decision journey where proof matters more than awareness and the competitors have figured that out. Maybe the pattern reflects a shared consultancy that has been advising the whole category in the same direction.

All of those interpretations are possible from the same observation. The matrix cannot tell you which one is right. The strategist, working with the full context of the client's situation, competitive history, and target audience, has to make that judgment. The matrix's job is to give the strategist accurate observations to work from, not to do the strategy.

The implication memo exists for exactly this reason: to give the strategist a first pass at interpretation, clearly labeled as interpretation, that they can evaluate and revise with their fuller knowledge. It is a thinking aid, not a conclusion. The difference between "competitors are leading with social proof" (observation) and "your client should lead with social proof" (recommendation) is the gate, and the gate is the human judgment about whether this pattern is relevant, actionable, and right for this client's particular situation.

<!-- → [TABLE: Evidence boundary — rows: Verified (captured public pages, screenshots, ads, dated source notes), Model judgment (tone labels, message clusters, inferred audience), Human judgment (category relevance, strategic interpretation, priority). Caption: The labels are not hierarchical. Verified evidence is not more important than human judgment — they belong to different categories that serve different functions.] -->

---

The running project task for this chapter is the competitor matrix itself: three to five competitors, columns for source, date, claim, proof offered, CTA, audience signal, tone label, contradiction flag, and human-review note. The discipline is in the human-review note column — every inference that goes beyond the observable gets flagged there, labeled as inference, and held as a candidate rather than a finding.

If the evidence is thin — if a competitor has minimal public-facing materials, or if the capture date is too old to be reliable — write that directly in the matrix. The note that says *competitor website sparse, last substantive update uncertain, observations have low confidence* is more useful than a confident characterization built on weak inputs. The matrix should tell the truth about its own evidence, not just about the competitors it is describing.

There is a test for whether the matrix is working correctly: can you trace any single entry back to a source? If someone at the client meeting asks where the claim that a competitor uses countdown-timer scarcity mechanics came from, can you show them? If the answer is yes — here is the URL, here is the capture date, here is a screenshot — the entry is doing its job. If the answer requires reconstructing something from memory or explaining that the AI identified the pattern, the entry is not yet defensible and should not be presented as observation.

---

The verification checklist for this chapter runs: the competitor set is explicit; every observation has a source and a date; tone and audience inferences are labeled; the matrix separates observation from implication; contradictions are preserved rather than averaged away.

Machine conformance is what the agent checks: are all required columns present, are all source fields populated, does the log contain the expected entries. Human adequacy is what the practitioner checks: is this competitor set the right one for this strategic question, is this evidence sufficient to bring to a brief, are the inferences I am drawing from this matrix ones I can defend?

The difference between those two checks is the whole architecture. The agent handles the first because it is a structural question about completeness. The human handles the second because it is a judgment question about whether the work is good enough for what it needs to do.

A competitor scan built this way — specific observations, traceable sources, dated captures, labeled inferences, preserved contradictions — is a professional artifact. It can support a brief, a strategy presentation, a creative direction. The one built the other way, the one that came back with "premium, youthful, disruptive, trustworthy," is noise that sounds like signal. And in the meeting, when the client asks which competitor led with social proof and when, only one of those artifacts has an answer.

---

## LLM Exercises

**Exercise 1 — Build the matrix**

Select three competitors from a category you have access to or can research through public sources. Capture at least two public-facing touchpoints per competitor (homepage, a current ad, a social post, a press release). For each capture, complete the full matrix row: source URL, capture date, primary claim, proof offered, CTA, audience signal, tone label, channel, contradiction flag (if applicable), and a human-review note for every inference that goes beyond the observable. When the exercise is complete, identify which entries you are most and least confident in, and write a one-paragraph note on what would increase confidence in the weakest entries.

Prompt suggestion: *"I'm going to give you a set of captured brand materials from three competitors. For each one, help me extract: the primary claim, what proof is offered, the CTA, the visible audience signals, the tone, and the channel. Label any inferences separately from observable facts. Flag any contradictions between what you find in different materials from the same competitor."*

**Exercise 2 — Separate observation from implication**

Take a completed competitor matrix — yours from Exercise 1 or a provided sample — and write two documents from it. The first: a one-page observation summary that contains only what was directly observed, sourced, and dated. No strategy, no recommendations, no implications. The second: a one-page implication memo that draws on the observation summary to suggest strategic meaning, labeled explicitly as interpretation. Compare the two documents. Identify three specific places where the implication memo makes a jump that cannot be fully supported by the observation summary. Write a note on what additional evidence would be needed to close each gap.

Prompt suggestion: *"Here is my competitor matrix. Help me write two documents from it: a pure observation summary with no strategy, and a separate implication memo labeled as interpretation. Then help me identify the three places where the implication memo makes the biggest inferential leaps, and describe what additional evidence would be needed to support each one."*

**Exercise 3 — The contradiction audit**

Review a competitor matrix (yours or a provided sample) specifically for contradictions: places where a competitor's messaging on one channel, at one point in time, or for one audience seems inconsistent with its messaging elsewhere. For each contradiction you find, write a human-review note that names what was observed, lists at least two possible explanations for the inconsistency, and explicitly marks which explanation you consider most likely and why. Then identify which contradictions, if true, would have the most significant implications for your client's strategic choices.

Prompt suggestion: *"Here is a competitor matrix with several contradiction flags. For each flagged contradiction, help me develop at least two possible explanations for what the inconsistency might mean strategically. Then help me assess which contradictions are most likely to be strategically significant versus which are likely to be noise or minor execution variation."*
