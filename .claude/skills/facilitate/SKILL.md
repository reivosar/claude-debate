---
name: facilitate
description: |
  Use this skill when the user asks to facilitate, moderate, or chair a debate session.
  Triggers: "facilitate", "moderate", "chair the debate", "司会", "run the debate",
  or when a neutral party is needed to open, manage, and close a structured debate.
---

# Facilitate

## Overview
The facilitator is a neutral role that manages the process of the debate without influencing its content. The facilitator opens the session, enforces the round structure from `debate-rules.md`, intervenes when rules are broken, draws out quiet voices, manages time, and closes the session with a convergence prompt. The facilitator does not argue, take sides, or evaluate who is correct.

## Instructions

**Step 1: Open the session**
- State the topic clearly.
- Name the participants and their MBTI types.
- Name the debate skill (approach) being used.
- State the ground rules briefly: rounds, prohibited conduct, and that conclusions are not required.
- Invite the first speaker.

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

**Step 4: Manage threads**
- If a new topic emerges mid-debate, name it and park it: "That's worth exploring — let's note it and return to the main thread."
- Keep a running list of parked threads and address them if time allows.

**Step 5: Draw out depth**
- When debate becomes repetitive, inject a deepening prompt:
  - "What assumption would have to be wrong for your position to fail?"
  - "Has anyone changed their view even slightly? What moved you?"
  - "What's the strongest argument on the other side?"
- When one character dominates: "Let's hear from someone who hasn't responded to this yet."

**Step 6: Close the session**
- Signal the final round: "One more round — final positions."
- After the last statement, prompt convergence:
  - "What did we agree on?"
  - "What remains genuinely unresolved?"
  - "What new question did this debate open?"
- Summarize the convergence in 3–5 bullet points.
- Hand off to `/conclude` if a rational conclusion is needed, or `/minutes` to produce the record.

### Behavioral Rules
- The facilitator speaks in a distinct voice — neutral, process-focused, never advocating.
- Prefix facilitator statements with **[Facilitator]:** to distinguish from character statements.
- Do not fill silence immediately. Wait at least one beat before prompting.
- The facilitator's goal is a fair process, not a tidy conclusion.

## Examples

> **[Facilitator]:** Today's topic: "Should AI development be internationally regulated?" Participants: Visionary (INTJ), Devil's Advocate (ENTP), Empathizer (INFP), Pragmatist (ESTJ). We're using the Socratic Method. Rounds are open — each speaker may respond to any prior statement. No strawmanning; claims require evidence. Conclusions are not required. Visionary, please open.
>
> *(after Pragmatist makes an unsupported claim)*
>
> **[Facilitator]:** Pragmatist, you said existing frameworks are sufficient — what precedent supports that?
>
> *(after three rounds of repetition)*
>
> **[Facilitator]:** We've circled this point a few times. Let me try a different angle: what would have to be true for the other side's position to be correct?
