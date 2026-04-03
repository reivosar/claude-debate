---
name: debate
description: |
  Use this skill to run a complete debate session end-to-end.
  Triggers: "run a debate", "start a debate session", "debate this topic", "ディベートして", "議論して",
  or when the user provides a topic and wants the full workflow: facilitation → debate → conclusion → minutes.
---

# Debate Session (Full Workflow)

## Overview

**This skill is for single interactive sessions only.** For controlled experiments across multiple runs, use `/experiment` instead — it spawns isolated `debate-runner` agents that eliminate cross-session context contamination.

Orchestrates a complete debate session from open to close. Reads and applies each skill file in sequence:
1. **Setup** — confirm topic, approach, and participant configuration
2. **Facilitation** — apply `facilitate/SKILL.md` to open and manage the session
3. **Debate** — apply the chosen approach skill (e.g. `socratic/SKILL.md`)
4. **Conclusion** — apply `conclude/SKILL.md` to synthesize a rational conclusion
5. **Minutes** — apply `minutes/SKILL.md` to produce the full Japanese record

## Instructions

**Step 1: Confirm session parameters**

Before starting, confirm the following. If not specified by the user, apply the defaults:

| Parameter | Default |
|-----------|---------|
| Topic | *(required — ask if not provided)* |
| Approach skill | `/socratic` |
| Participant configuration | *(see `personas.md` for presets — default: Standard)* |
| Number of rounds | *(see `experiments.md` for baseline)* |
| Facilitator | Enabled |
| Expertise Level | Informed |
| Stakes | Low |
| Power Dynamic | Flat |
| Enneagram override | None (use defaults from `personas.md`) |
| Big Five override | None (use defaults from `personas.md`) |

Session variables (Expertise, Stakes, Power Dynamic, Enneagram, Big Five) are applied to all characters throughout the session. See `variables.md` for definitions and effects.

State the confirmed parameters and proceed without further prompting unless the user objects.

**Step 2: Open the session (`/facilitate` — Open)**

Apply the Facilitate skill: open the session, introduce participants, state the topic and ground rules, and invite the first speaker.

**Step 3: Run the debate**

Apply the chosen approach skill for the agreed number of rounds. The facilitator manages turn order and enforces rules throughout. Run all rounds before proceeding.

After generating each statement or facilitator intervention, immediately append it to `outputs/YYYY-MM-DD-<topic-slug>/transcript.md`. Do not accumulate statements in context before writing.

Append format per entry:
```
---
Statement N — [Speaker] ([MBTI]) — [Type] [FLAG]

[Full statement text]
```

**Step 4: Close facilitation (`/facilitate` — Close)**

Apply the Facilitate skill: signal the final round, prompt the convergence questions, and summarize convergence in 3–5 bullet points. Append to `transcript.md`.

**Step 5: Draw the conclusion (`/conclude`)**

Apply the Conclude skill immediately after convergence. Produce the three-part conclusion: Established / Conditional / Open. Append to `transcript.md`.

**Step 6: Produce minutes (`/minutes`)**

Read `transcript.md` in full, then apply the Minutes skill to produce the full Japanese record:
- Executive Summary
- Full Transcript (copied from `transcript.md` — do not regenerate from memory)
- Statement Index
- Key Moments
- Convergence
- Evaluation scores
- Conclusion

Save to `outputs/YYYY-MM-DD-<topic-slug>/minutes.md`.

### Behavioral Rules
- Do not skip any stage. If a stage is skipped, state why explicitly.
- Do not ask for confirmation between stages — run the full workflow uninterrupted unless the user intervenes.
- If the user specifies an approach skill, use it. If not, default to `/socratic`.
- All minutes output is in Japanese. All character names and MBTI types remain in English.
- If the topic is not provided, ask once and then proceed.

## Examples

**User:** "AIは人間の仕事を奪うかについて弁証法でディベートして"

> Session parameters confirmed:
> - Topic: Will AI eliminate more jobs than it creates?
> - Approach: `/dialectic`
> - Participants: Standard 4 (Visionary INTJ, Devil's Advocate ENTP, Empathizer INFP, Pragmatist ESTJ)
> - Rounds: 3
> - Facilitator: Enabled
>
> Proceeding with full workflow.
>
> ---
> **[Facilitator]:** Today's topic: "Will AI eliminate more jobs than it creates?" ...
