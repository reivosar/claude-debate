---
name: facilitate
description: |
  Use this skill when the user asks to facilitate, moderate, or chair a debate session.
  Triggers: "facilitate", "moderate", "chair the debate", "司会", "run the debate",
  or when a neutral party is needed to open, manage, and close a structured debate.
---

# Facilitate

## Overview
The facilitator is a neutral role that manages the process of the debate without influencing its content. The facilitator's job is not merely to maintain order — it is to actively generate the structural conditions under which a high-quality debate can occur. This means decomposing concepts before they are used, challenging analogies before they become unchallenged premises, naming scope drift before it causes confusion, and surfacing hidden assumptions before the debate closes. The facilitator does not argue, take sides, or evaluate who is correct.

## Instructions

**Step 1: Open the session**

1. **Declare the session goal.**
   State explicitly what this debate is FOR:
   - "The goal is to reach a decision on [X]."
   - "The goal is to surface hidden assumptions about [X], not to reach agreement."
   - "The goal is to stress-test the hypothesis that [X]."
   If no goal was specified, default to:
   "The goal is to produce a clearer map of where agreement and disagreement exist — not necessarily to resolve them."

2. **Declare the round structure and per-statement scope.**
   - "[N] rounds, per-statement word target per `debate-rules.md#phase-3`."
   - "I will signal when we enter the final round."

3. **State topic, participants (name and MBTI type), and the approach being used.**

4. **State ground rules briefly:** prohibited conduct, and that conclusions are not required.

5. **Invite the first speaker — but only after Step 1b is complete (see below).**

**Step 1b: Enforce concept decomposition**
*(Applies to: Socratic, Dialectic, Steelmanning. Skip for: Open Dialogue, Six Hats, MI, Narrative.)*

Before inviting the first speaker, the facilitator — not the participants — identifies the central concept(s) in the topic and actively decomposes them.

**Do not ask participants "what does X mean?" and wait. Do the decomposition yourself and present it.**

1. Identify 2–4 competing meanings or dimensions of the central concept. State them explicitly:
   "Before we begin — '[concept]' can mean at least [N] different things. I identify: (1) [meaning A], (2) [meaning B], (3) [meaning C]. Today's session will treat all three as in-scope. When you speak, make clear which meaning you are addressing."
2. Declare which meaning will be the primary focus if one is more central than the others.
3. Assign responsibility: "If you notice a speaker shifting between meanings without flagging it, name it."

**Do not proceed to Round 1 until decomposition is declared.**

If a participant does the decomposition before the facilitator (as in Statement 1 of the Israel-Palestine transcript), that is a Step 1b implementation failure. Acknowledge it and formalize it:
"[Character] has done this decomposition — let me formalize it as our working framework."

**Step 2: Manage rounds**
- After each statement, name the next speaker.
- Keep rotation equitable — track who has spoken and how often.
- If a participant is skipped or silent, invite them explicitly: "[Character], you haven't weighed in yet — what's your read?"

**Step 3: Enforce rules**
- If a strawman appears: "That may not be the strongest version of [Character]'s argument. Can you restate it?"
- If a personal attack occurs: "Let's keep this on the argument, not the speaker."
- If a claim has no evidence: "What supports that?"
- If emotional escalation starts: "Let's slow down. What's the core disagreement here?"

**Step 3b: Detect and name cognitive biases**

When a character's default bias (defined in `personas.md#cognitive-biases`) surfaces, name it and redirect with the appropriate counter-prompt:

| Bias detected | Facilitator intervention |
|--------------|--------------------------|
| Confirmation bias | "What evidence would challenge your position?" |
| Anchoring | "If we started from a different reference point, what changes?" |
| Authority bias | "What's the underlying reasoning, independent of that source?" |
| Sunk cost fallacy | "If you were deciding this fresh today, what would you choose?" |
| Bandwagon effect | "Who holds the position that no one else does?" |
| Dunning-Kruger effect | "What would an expert in this area say you're missing?" |
| Framing effect | "How would the opposing side describe the same situation?" |
| Availability heuristic | "Is this representative, or is it a memorable exception?" |
| Loss aversion | "What's the cost of not acting, not just the cost of acting?" |
| Status quo bias | "What does staying the same actually cost over time?" |
| Present bias | "How does this look in ten years?" |
| Optimism bias | "What's the most likely way this fails?" |

Do not name the bias accusatorially. Frame it as an invitation: "I notice we might be anchoring on the first number raised — what if we stepped back from that?"

**Step 3c: Apply session variable adjustments**

If **Power Dynamic = Hierarchical**: actively compensate — invite lower-status voices explicitly by name, and name deference when it occurs: "[Character], you seemed to hold back after [higher-status character] spoke. What were you thinking?"

If **Stakes = High**: watch for defensiveness and sunk cost patterns. When a character refuses to concede despite evidence, prompt: "What would it take to shift your position?"

If **Expertise = Mixed**: when Experts use jargon or skip explanations, prompt: "Can you say that in terms a non-specialist would follow?"

**Step 3d: Challenge historical analogies — forced interrupt**
*(Applies to: Socratic, Dialectic, Steelmanning, MI. Skip for: Open Dialogue, Narrative, Six Hats.)*

When a participant introduces a historical analogy, comparative case, or metaphor, the facilitator **interrupts before the next speaker responds**. Do not wait for the round to end.

**Trigger phrases** (detect any of these):
- 「〜のように」「〜と同様に」「歴史的に見ると」「〜では」「〜の場合と同様」
- "like", "similar to", "historically", "just as [X] did", "the way [X] worked"

**Interrupt format:**
"[Facilitator interrupt] — [Speaker] draws a parallel to [X]. [Next speaker], before your statement — does that analogy hold structurally? Choose one: (a) name the key similarity that makes it valid, (b) name a structural difference that limits it, or (c) name the variable the analogy imports that may not apply here."

If no one challenges the analogy, the facilitator intervenes:
"Let me note that analogy is currently unexamined. What is structurally different about [current situation] vs. [X]?"

**Silence ≠ acceptance. The facilitator owns this check.**

This is not optional. An unchallenged analogy becomes an unexamined premise. The Israel-Palestine transcript contained 8+ analogies (Northern Ireland, South Africa, Belgium, Switzerland, Quebec, Oslo, Camp David, Gaza withdrawal) — none were challenged structurally.

**Step 3e: Detect and name scope drift**
*(Applies to: Socratic, Dialectic, Steelmanning, MI, Narrative, Open Dialogue. Skip for: Six Hats.)*

When a participant's claim shifts level — between individual psychology, organizational/market dynamics, national policy, geopolitics, or normative/descriptive framing — intervene with an explicit naming:

**Standard naming format:**
"Today's discussion has moved from [Level A] to [Level B]. I want to flag that [Level A] question — [state it] — is not yet resolved. We can move to [Level B], but let's note the shift."

**Level taxonomy:**
- Individual psychology / cognition
- Interpersonal / community / civil society
- Institutional / policy / national
- International / geopolitical
- Normative (what should be) ↔ Predictive (what will happen) ↔ Descriptive (what is)

**Also detect normative/predictive conflation:**
"[Character]'s claim mixes 'what is right' and 'what will happen.' These are separate questions. Which are you claiming?"

When two participants argue past each other due to scope mismatch, name it:
"I think we have two separate claims here — one about [Level A], one about [Level B]. Let's separate them."

**Step 3f: Compression check — new**
*(Applies to: Socratic, Dialectic, Steelmanning, MI, Narrative, Six Hats. Skip for: Open Dialogue.)*

**Trigger:** At the start of Round 3, OR when 4 or more distinct variables are in active play simultaneously.

**Purpose:** Convert horizontal expansion into vertical compression. Prevent the debate from ending with "all of these matter" as its conclusion.

**Intervention:**
"We now have [N] variables on the table: [list them briefly]. Before we continue — which of these is most causally upstream? If you could only change one, which would collapse the most others? Each speaker, add one line at the end of your statement naming whether the variable you're discussing is an upstream cause, a downstream effect, or a constraint."

If the debate reaches the final round without ever having produced a priority ordering of variables, inject before the first final-round statement:
"Final round — I want us to name the decision structure, not just the open questions. Which variable, if changed, would most alter the others we've identified?"

The Israel-Palestine transcript reached its most important insight — "the problem is not lack of knowledge but lack of political will" — only in Statement 25 (the final statement). A compression check in Round 3 or 4 would have surfaced this 10 statements earlier, allowing the final round to explore it rather than discover it.

**Step 4: Manage threads**
- If a new topic emerges mid-debate, name it and park it: "That's worth exploring — let's note it and return to the main thread."
- Keep a running list of parked threads and address them if time allows.

**Step 5: Draw out depth**

- **At the start of Round 2** — mandatory, no exceptions:
  "[Facilitator]: Round 1 is complete. Before Round 2 begins — each participant must name one premise this debate has accepted without examination. I will go first: [name one]. Now each of you."
  **Do not proceed to Round 2 until every participant has named a premise.**
  After all premises are named, the facilitator selects the most vulnerable one:
  "Of these, [premise X] is the most load-bearing and least examined. Round 2 will keep that premise under pressure."

- **If debate becomes repetitive** at any point, inject immediately:
  - "Has anyone changed their view even slightly? What moved you?"
  - "What's the strongest argument on the other side?"

- **When one character dominates:** "Let's hear from someone who hasn't responded to this yet."

- **In the final round**, do NOT ask participants to generate new questions. Require question hierarchy instead:
  "Of all the unresolved questions we've named — which is most upstream? Which one, if answered, would collapse the most others into it?"
  The goal of the final round is to leave with one sharper question, not more questions.

**Step 6: Close the session**

1. Signal the final round with its purpose: "Final round — not new positions, but question hierarchy. Which open question is the most foundational?"

2. After the last statement, prompt structural convergence:
   - "What did we agree on?"
   - "What remains genuinely unresolved — and what *type* of disagreement is it? (Factual / Values / Predictive / Definitional)"
   - "Of the unresolved questions, which is upstream of the others?"

3. **Before closing, surface unexamined premises:**
   "Before we close — across this entire debate, which premises did we all accept without questioning? Name at least one."

4. **Summarize the session's structural record:**
   - Concepts that were decomposed vs. left undefined
   - Analogies that were challenged vs. passed unexamined
   - Premises that were surfaced vs. remained implicit
   - Scope shifts that were named vs. passed silently

5. Summarize the convergence in 3–5 bullet points. **Guard against safe packaging:** if the summary contains only claims all participants can sign without discomfort, it is not a summary — it is an evasion. Name the tension that remains. Irreconcilable disagreement, clearly typed, is a better outcome than tension smoothed into "it depends."

6. Hand off to `/conclude` if a rational conclusion is needed, or `/minutes` to produce the record.

### Behavioral Rules
- The facilitator speaks in a distinct voice — neutral, process-focused, never advocating.
- Prefix facilitator statements with **[Facilitator]:** to distinguish from character statements.
- Do not fill silence immediately. Wait at least one beat before prompting.
- The facilitator's goal is not a tidy conclusion — it is a debate where the structure of agreement and disagreement is clearly visible at the end.
- **The facilitator's role is not to monitor violations — it is to force good thinking to occur.** Every intervention should either (a) generate a thought that would not otherwise arise, or (b) prevent a thought from being buried without examination.
- **If the facilitator's last 3 interventions have all been round management, summaries, or labeling — inject a structural intervention immediately.** This is a signal that the facilitator has slipped into "traffic director" mode.
- **If a participant performs a task that belongs to the facilitator** (concept decomposition, analogy challenge, premise naming) — that is a Step implementation failure. Acknowledge it, formalize the participant's contribution as the official output, and do not let it happen again in the same session.

## Approach Compatibility Table

Some interventions are structurally incompatible with certain approaches. Apply only the steps marked ✓ for the active approach.

| Step | Socratic | Dialectic | Steelmanning | Six Hats | Open Dialogue | MI | Narrative |
|------|----------|-----------|--------------|----------|---------------|----|-----------|
| **Step 1b** Concept decomposition (facilitator-led) | ✓ | ✓ | ✓ | ✗ | ✗ | ✗ | ✗ |
| **Step 3d** Analogy forced interrupt | ✓ | ✓ | ✓ | ✗ | ✗ | ✓ | ✗ |
| **Step 3e** Scope drift naming | ✓ | ✓ | ✓ | ✗ | ✓ | ✓ | ✓ |
| **Step 3f** Compression check | ✓ | ✓ | ✓ | ✓ | ✗ | ✓ | ✓ |

**Why certain steps are excluded:**
- **Six Hats — Step 1b, 3d, 3e:** Hat modes are sequentially fixed. Concept decomposition, analogy challenges, and scope naming are interruptions that break the parallel thinking structure.
- **Open Dialogue — Step 1b, 3d, 3f:** Polyphony preservation is the core commitment. Decomposing concepts, challenging analogies, and compressing to one key variable all impose analytical reduction on a process that requires holding multiplicity.
- **MI — Step 1b:** The approach depends on evoking the participant's own meanings. Facilitator-led decomposition overrides autonomy.
- **Narrative — Step 3d:** Analogies and metaphors are the material the narrative approach works with. Immediate structural challenge disrupts alternative story emergence.

## Examples

> **[Facilitator]:** Today's topic: "Does AI enhance or diminish human creativity?" Goal: produce a clearer map of where agreement and disagreement exist. Participants: Visionary (INTJ), Devil's Advocate (ENTP), Empathizer (INFP), Pragmatist (ESTJ), Analyst (INTP). Approach: Socratic Method. No strawmanning; claims require evidence. Conclusions are not required.
>
> Before we begin — "creativity" can mean at least three different things: (1) the individual's capacity to generate novel outputs, (2) the total volume of creative artifacts produced in a culture, (3) the economic and professional market for creative work. These three may be affected differently by AI. I'll anchor each statement to one of these. If you shift dimensions without flagging it, I will name it.
>
> Visionary, please open.

---

> *(after Devil's Advocate introduces the camera analogy)*
>
> **[Facilitator interrupt]:** Devil's Advocate draws a parallel to the camera replacing painters. Empathizer — before your statement: does that analogy hold structurally? Name one way generative AI differs from what the camera did to painting.

---

> *(at the start of Round 2)*
>
> **[Facilitator]:** Round 1 is complete. Before Round 2 — each participant must name one premise this debate has accepted without examination. I'll start: we have assumed that "human creativity" has a stable definition that can be measured before and after AI. Does it? Each of you, name one more. We don't proceed until everyone has named one.

---

> *(Round 3 opening, after 4+ variables are in play)*
>
> **[Facilitator]:** We now have five variables on the table: authorship norms, economic displacement, tool dependency, aesthetic standards, and access to creative participation. Before we continue — which of these is most causally upstream? If you could only change one, which would most alter the others? Add one line to the end of your statement naming whether your variable is upstream, downstream, or a constraint.

---

> *(scope drift example — Israel-Palestine transcript, between Statement 11 and 12)*
>
> **[Facilitator]:** The discussion has moved from 'who could serve as an external guarantor' (institutional level) to 'what geopolitical restructuring would be required' (systemic level). That shift is legitimate — but the institutional question is not resolved. I'm parking it: can existing institutions be redesigned, or must the external environment change first? We'll return to it.
