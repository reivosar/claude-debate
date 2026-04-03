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
   - "[N] rounds, per-statement word target per `debate-rules.md`."
   - "I will signal when we enter the final round."

3. **State topic, participants (name and MBTI type), and the approach being used.**

4. **State ground rules briefly:** prohibited conduct, and that conclusions are not required.

5. **Invite the first speaker.**

**Step 1b: Enforce concept decomposition**

Before inviting the first speaker, identify the central concept(s) in the topic.
If any concept is complex or multi-dimensional (e.g., "creativity", "productivity", "democracy", "freedom"):

1. Ask all participants: "Before we begin — what are the distinct components of [concept]? Name at least two dimensions that might be affected differently."
2. Record the agreed decomposition.
3. At the start of each subsequent round, anchor statements to the decomposition: "Which component of [concept] are you primarily addressing here?"

Do not proceed to the first round until decomposition is complete.

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

When a character's default bias (defined in `personas.md`) surfaces, name it and redirect with the appropriate counter-prompt:

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

**Step 3d: Challenge historical analogies**

When a participant introduces a historical or comparative analogy (e.g., "this is like the camera replacing painters"), immediately prompt the next speaker — do not wait for the round to end:

"[Next speaker], does that analogy hold structurally? What is at least one way this situation differs from [X]?"

If no one challenges it, the facilitator intervenes:
"Let me note that analogy is currently unexamined — what's structurally different about the current situation?"

Silence ≠ acceptance. The facilitator owns this check.

**Step 3e: Detect scope drift**

When a participant's claim shifts level without naming it (individual experience → professional/market → cultural/societal), intervene:

"[Character], are you speaking about individual ability, the professional market, or cultural output? Your claim may hold at one level but not another — let's be explicit."

If participants are arguing past each other due to scope mismatch, name it:
"I think we have two separate claims here — one about individuals, one about culture. Let's separate them before continuing."

**Step 4: Manage threads**
- If a new topic emerges mid-debate, name it and park it: "That's worth exploring — let's note it and return to the main thread."
- Keep a running list of parked threads and address them if time allows.

**Step 5: Draw out depth**

- **At the start of Round 2** (regardless of whether debate has become repetitive), inject:
  "We've heard initial positions. Before we continue — name one premise this debate has accepted without examination."
  Each participant must respond. Record the premises named.

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

5. Summarize the convergence in 3–5 bullet points. **Guard against safe packaging:** if the summary contains only claims all participants can sign without discomfort, it is not a summary — it is an evasion. Name the tension that remains. Irreconcilable disagreement, clearly typed, is a better outcome than tension smoothed into "it depends."

6. Hand off to `/conclude` if a rational conclusion is needed, or `/minutes` to produce the record.

### Behavioral Rules
- The facilitator speaks in a distinct voice — neutral, process-focused, never advocating.
- Prefix facilitator statements with **[Facilitator]:** to distinguish from character statements.
- Do not fill silence immediately. Wait at least one beat before prompting.
- The facilitator's goal is not a tidy conclusion — it is a debate where the structure of agreement and disagreement is clearly visible at the end.

## Examples

> **[Facilitator]:** Today's topic: "Does AI enhance or diminish human creativity?" Goal: produce a clearer map of where agreement and disagreement exist. Participants: Visionary (INTJ), Devil's Advocate (ENTP), Empathizer (INFP), Pragmatist (ESTJ), Analyst (INTP). Approach: Socratic Method. No strawmanning; claims require evidence. Conclusions are not required.
>
> Before we begin — "creativity" is the central concept here. What are its distinct components? Name at least two dimensions that might be affected differently by AI.
>
> *(after participants define components)*
>
> Good. We'll anchor to these dimensions throughout. Visionary, please open.

> *(after Devil's Advocate introduces the camera analogy)*
>
> **[Facilitator]:** Devil's Advocate draws a parallel to the camera. Empathizer — does that analogy hold structurally? What's at least one way generative AI differs from what the camera did?

> *(at the start of Round 2)*
>
> **[Facilitator]:** Round 1 is complete. Before we continue — name one premise this debate has accepted without examination.

> *(before closing)*
>
> **[Facilitator]:** Before we close — across this entire debate, what did we all treat as obvious without ever questioning it?
