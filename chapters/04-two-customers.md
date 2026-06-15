# Chapter 4 — Two Customers

Here are two workflows, both of which fail. The first one fails quietly. The second one fails loudly. Neither failure has anything to do with whether AI was used.

Workflow one produces a perfect JSON file. The schema is clean. The fields are populated. The logs are green. The brand team opens it, looks at the columns, and has no idea what any of it means or what they're supposed to do with it. The file sits in a folder. Nothing happens. Eventually someone asks for the memo that was supposed to come out of this process, and nobody can say where the memo went or whether the JSON was ever used to make a decision.

Workflow two produces a persuasive memo. It is beautifully written. The argument is structured and clear. The recommendations are specific. A senior brand manager reads it, agrees with it, and acts on it. Three months later, the same decision comes up again and someone asks to rerun the analysis. Nobody can. The memo has no inputs, no parameters, no logs. It is not a workflow at all — it is a document that happened once, under conditions that no longer exist, produced by a process that no longer exists.

Both workflows failed. For opposite reasons. The first one served its executing agent and forgot its human audience. The second one served its human audience and forgot that it needed to be reproducible. Madison is built around the observation that a recipe has two customers, and you have to serve both.

---

Let me describe what each customer actually needs, because the needs are genuinely different and partially in tension.

![A two-column comparison joined by a shared central spine — the left column is the executing agent and its needs (explicit inputs, a clear transformation, an output schema, graceful anomaly handling); the right column is the human maintainer and theirs (purpose, the decision supported, the review point and its meaning, context to judge, and the ability to modify the recipe) — signalling that a single recipe must satisfy both, partially in tension](../images/04-two-customers-fig-01.png)
*Figure 4.1 — The two customers of a recipe*

The executing agent — the AI system, the automated script, whatever is running the operational steps — needs structure. It needs explicit inputs: where the data comes from, what format it arrives in, what to do if it's missing. It needs a clear transformation: the sequence of steps, the parameters, the decision rules. It needs an output schema: what the result looks like, where it goes, what gets logged. The agent does not need to understand the purpose of the workflow. It does not need context about why this matters. It needs operational specificity. Ambiguity makes agents fail silently, which is often worse than failing loudly.

The human maintainer — the brand practitioner who received the workflow, runs it, reviews its output, and eventually inherits responsibility for it — needs something almost completely different. They need to understand what the workflow is for. They need to see the decision the workflow is designed to support, and what kind of decision it explicitly refuses to make. They need to know where the human review point is and what the reviewer is actually supposed to do there. They need enough context to judge whether the output is reasonable, to recognize when something has gone wrong in a way that the logs won't catch, and to explain the workflow to someone else who takes over when they leave.

The human maintainer also needs to be able to modify the workflow when the world changes. Brand contexts change. Audience data gets refreshed. Competitors do things. Platforms update their APIs. A recipe that is perfectly documented for its original context but opaque to modification is a liability, not an asset. Within a year or two, it will either be abandoned or will continue running on stale assumptions with no one watching.

---

Now I want to look carefully at what happens when a workflow underserves each customer, because the failure modes are different and worth distinguishing.

![Two side-by-side panels showing the opposite ways a workflow fails — the left panel is the quiet failure: a complete, tidy structured-data artifact (clean schema, populated fields, green logs) with a hollow, outlined-only human-interpretation area; the right panel is the loud failure: a complete, persuasive narrative memo with a hollow, outlined-only reproducibility and log area](../images/04-two-customers-fig-02.png)
*Figure 4.2 — Two failure modes*

When a workflow underserves the executing agent — when the recipe is too ambiguous, too narrative, too reliant on implied context — the agent makes guesses. Language models, in particular, are very good at making plausible guesses. This is not reassuring. A plausible guess that is wrong is harder to detect than a broken schema. If the input specification is vague and the model fills in what sounds reasonable, the output will look coherent. The logs will be clean. The error will be invisible until someone with domain knowledge looks at the substance and notices that the audience segment described does not match the customer data, or the competitive framing reflects a market position the brand abandoned eighteen months ago.

When a workflow underserves the human maintainer — when the recipe is structurally perfect but humanly opaque — the failure mode is different. The output arrives and the human cannot evaluate it. They cannot tell whether the schema was applied correctly, whether the input data was what they expected, or whether the result represents a meaningful signal or an artifact of the process. In this situation, the human has three choices. They can pass the output along anyway, in which case they have effectively abdicated review and made the phase gate fictional. They can spend a lot of time reverse-engineering what the workflow did, which is possible but expensive and often incomplete. Or they can ignore the output entirely, in which case the workflow produces nothing of value. All three outcomes are failures.

The underlying problem in both cases is the same. A recipe that is only legible to one of its customers is a recipe that breaks when that customer is absent, unavailable, or replaced.

---

There is a concept in maintenance engineering called *serviceability* — the degree to which a system can be maintained and repaired by the people who are responsible for it under real operating conditions. Not ideal conditions. Not the conditions that existed when the system was designed. The conditions that actually exist: time pressure, partial documentation, institutional memory gaps, personnel turnover.

A Madison recipe needs to be serviceable in this sense. Not just runnable. Maintainable.

The practical test for serviceability is simple and uncomfortable. Hand the recipe to a colleague who was not involved in building it. Give them a realistic amount of time — say, thirty minutes. Ask them: can you tell me what this recipe is for? Can you tell me what you're supposed to do when you review the output? Can you tell me what would change about this recipe if the underlying audience data were refreshed?

If they can answer those questions, the recipe is serving its human customer. If they can't, the gap is in the human layer, not the agent layer.

The parallel test for the agent layer is different: run the recipe on data with a deliberate anomaly — a missing field, an unexpected format, a value outside the expected range. Does the recipe fail gracefully, with a useful error? Or does it fail silently, producing output that looks plausible but reflects the anomaly without flagging it?

Both tests should be run. Most recipes, in practice, pass only one.

---

| Recipe Element | Agent Customer (what the agent needs here) | Human Customer (what the human needs here) | Which is underserved? |
|---|---|---|---|
| Input specification | Source, format, and what to do when a field is missing. | Where the data comes from and whether it is current. | Human — sources rarely dated. |
| Transformation steps | Ordered steps, parameters, decision rules. | What the workflow is for and what it refuses to decide. | Human — purpose left implicit. |
| Output schema | Exact result shape and destination. | Whether the output is reasonable for the decision. | Neither, if labeled. |
| Log format | Required fields, run IDs, timestamps. | A trail that lets the run be reproduced. | Agent often fine; human can't read it. |
| Human review fields | Where to stop. | What to look at, what question to answer. | Human — usually just "review required." |
| Decision gate | A halt point. | Criteria, named decision, owner, logged record. | Human — the latch-less gate. |
| Maintenance notes | None needed. | What changes if the world changes. | Human — usually absent. |

*Table 4.1 — Most recipes were written with one customer in mind and barely gesture toward the other. The annotation makes that asymmetry visible.*

The table structure for this work has four columns. Recipe element: the specific part of the recipe you're annotating — input specification, transformation steps, output schema, log format, human review fields, decision gates, maintenance notes. Agent customer: what the executing agent needs from this element to run reliably. Human customer: what the human maintainer needs from this element to review, judge, and maintain. Which is underserved: a direct assessment of which customer this element is failing, if either.

Running this annotation on an existing recipe is often uncomfortable. Most recipes were written with one customer in mind and barely gesture toward the other. The annotation makes that asymmetry visible. That is the point. The repair comes after the visibility.

---

There is a specific element of recipe design that almost always underserves the human customer, and it is worth naming directly: the decision gate.

A decision gate is the point in a workflow where a human must decide whether to proceed. Not review — decide. The distinction matters. Review can be cursory. A person can look at an output, feel that it looks reasonable, and sign off without engaging the substance. A decision gate is designed to make that impossible, or at least harder. It should specify what the reviewer is looking at, what question they are answering, and what happens if their answer is no.

Most recipes that have a decision gate name it without specifying it. They say something like: *human review required before output moves downstream.* That instruction serves the agent — the agent knows where to stop. It does not serve the human. The human has not been told what to look for, what risk they're accepting if they proceed, or what recourse exists if the output turns out to be wrong.

The version that serves both customers looks different. It specifies the review criteria: what would make this output acceptable, and what would make it unacceptable? It names the decision: is this output ready to be used as input to the next step, yes or no? It names the owner: whose judgment counts here? And it records the decision in a log that can be inspected later.

That is a real gate. A gate that just says *review required* is a gate with no latch.

![A comparison schematic contrasting a gate with no latch against a real decision gate — the weak gate is a single node carrying only an undifferentiated "review" instruction with an open pass-through that anything can cross; the real gate contains four components — review criteria, the named decision (yes or no), the named owner, and a logged record — that an output must satisfy before crossing](../images/04-two-customers-fig-03.png)
*Figure 4.3 — The latch-less gate vs the real gate*

---

I want to address the tension that makes this hard. Serving both customers simultaneously takes longer than serving one. A recipe with comprehensive human documentation is longer and slower to write than a recipe with only operational specifications. A recipe with a well-specified decision gate requires someone to think carefully about what reviewers should actually look for, which requires domain knowledge and judgment that is harder to produce than schema definitions.

This is the real cost of the two-customer requirement. Not complexity. Time. The time of a domain expert who knows what the output is supposed to mean, who understands the brand well enough to articulate what a bad result looks like, and who cares enough about the workflow's longevity to write it down for the people who come after them.

Madison does not pretend this cost is zero. What it argues is that the cost of not doing it is higher — and is paid later, under worse conditions, by people who were not involved in the original design and have no context for recovering from the failure.

The JSON file that nobody could interpret was not a failure of AI. It was a failure to spend the time required to make the output legible to the humans who needed to act on it. That time has to come from somewhere. Madison's position is that it comes from the recipe-building phase, not the incident-response phase.

---

The practical shape of this chapter's work is an annotation. Take one recipe you use or have inherited. Mark every element in two categories: what it provides to the executing agent, and what it provides to the human maintainer. Then identify the weakest element on the underserved side, and make the smallest change that would improve it.

One element. One change. The goal is not to rewrite the recipe. It is to build the habit of seeing both customers in every recipe you touch, so that over time the recipes you produce serve both without having to be reminded.

If an element is missing entirely — if there is no human review section, or no maintenance note, or no specification of what the reviewer is supposed to decide — write that directly in the annotation. Do not smooth it over. A recipe that acknowledges its gaps is more maintainable than a recipe that hides them inside confident-sounding prose.

---

A recipe that serves both customers can still overclaim. It can be runnable, legible, maintainable, and still produce output that asserts more certainty than the evidence supports. That is the problem the next chapter addresses: what a recipe is allowed to say about what it found, and where the honest boundary between analysis and assertion sits.

---

<!-- LLM EXERCISE -->
**Exercise for further inquiry.** Take a workflow or recipe you currently use — a prompt chain, a content brief process, a reporting routine, anything that runs repeatedly and produces an artifact that someone acts on. Annotate it in two columns: what each element provides to the executing system, and what each element provides to the human who reviews and maintains it. Then ask: if the person who built this recipe left tomorrow and a new teammate had to run it next week, which column would they find sufficient? Which would leave them guessing? Write one sentence describing the smallest addition that would close the largest gap on the weaker side.

## Prompts

### Figure 4.1 — The two customers of a recipe
**Files:** ../images/04-two-customers-fig-01.svg
**Prompt:** Render a brutalist two-column comparison joined by a shared central spine — left column "executing agent" (explicit inputs, clear transformation, output schema, graceful anomaly handling) in secondary grey; right column "human maintainer" (purpose, decision supported, review point and meaning, context to judge, modifiability) in ochre. Four to five empty rounded rows per column. Hardcoded palette (agent #545454, human #C8860E, spine #2a1a0e, border #D4D4D4, fill #F5F5F5, white #FFFFFF), no person or robot icons, no directional arrows.

### Figure 4.2 — Two failure modes
**Files:** ../images/04-two-customers-fig-02.svg
**Prompt:** Render a brutalist two-panel comparison — left panel quiet failure: a complete structured-data block (schema, fields, a green-accent log) with a hollow outlined-only human-output area; right panel loud failure: a complete narrative block with a hollow outlined-only reproducibility/log area. Hardcoded palette (structured artifact #545454, narrative artifact #C8860E, empty regions ink #2a1a0e outline only, green-log accent — substitute secondary grey, red #C8102E reserved for emphasis, white #FFFFFF), no rendered JSON or memo text, no checkmarks.

### Figure 4.3 — The latch-less gate vs the real gate
**Files:** ../images/04-two-customers-fig-03.svg
**Prompt:** Render a brutalist contrast of two gates — a weak gate: one node with an undifferentiated "review" instruction and an open unobstructed pass-through arrow; a real gate: one node holding four reserved component slots (review criteria, named decision yes/no, named owner, logged record) with a controlled crossing. Hardcoded palette (weak gate ochre #C8860E, real gate red #C8102E, pass-through arrows #2a1a0e, border #D4D4D4, fill #F5F5F5, white #FFFFFF), no literal door or lock imagery, no rendered criteria text.
