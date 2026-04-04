---
name: debate
description: |
  Use this skill to run a complete debate session end-to-end.
  Triggers: "run a debate", "start a debate session", "debate this topic", "ディベートして", "議論して",
  or when the user provides a topic and wants the full workflow: facilitation → debate → conclusion → minutes.
---

# Debate Session (Full Workflow)

## Overview

Orchestrates a complete debate session by spawning a `debate-runner` agent. The agent runs in an isolated context, writes each statement immediately to disk, and returns evaluation scores when done. The main session only confirms parameters and reports results.

**Do not run the debate inline.** Inline execution accumulates all statements in the main context (~10,000 words) before writing, causing slow responses. The agent approach writes each statement as it is generated and keeps the main context clean.

For controlled experiments across multiple runs, use `/experiment` instead.

## Instructions

**Step 1: Confirm session parameters**

Ask for the topic if not provided. For all other parameters, use whatever the user specifies. Apply rule-file baselines for anything left unspecified — do not prompt for them.

Determine:
- `topic`: the debate topic (exact string)
- `approach`: skill name (default: `socratic`)
- `participants`: character list (default: Standard 5 from `personas.md#preset-standard`)
- `rounds`: number of rounds (default: 5)
- `expertise_level`: Informed / Expert / Novice / Mixed (default: Informed)
- `stakes`: Low / Medium / High / Asymmetric (default: Low)
- `power_dynamic`: Flat / Hierarchical / Reversed (default: Flat)
- `enneagram_overrides`: character-specific overrides or None
- `big_five_overrides`: character-specific overrides or None
- `date`: today's date (YYYY-MM-DD)
- `topic_slug`: lowercase, hyphen-separated topic (e.g. `ai-job-displacement`)
- `output_dir`: `outputs/<date>-<topic-slug>/`

State the confirmed parameters to the user, then proceed.

**Step 2: Spawn the debate-runner agent**

Spawn the `debate-runner` agent with all parameters confirmed in Step 1. The agent will:
1. Open the session (facilitator intro, ground rules, concept decomposition per `facilitate/SKILL.md`)
2. Run all rounds (approach skill + facilitation)
3. Close and converge
4. Draw the conclusion
5. Write minutes in Japanese
6. Return evaluation scores as JSON

Pass the full parameter set. Do not pass partial parameters — the agent uses baselines only for parameters not provided.

**Step 3: Report results**

When the agent completes, report to the user:
- Output files: `outputs/<date>-<topic-slug>/transcript.md` and `outputs/<date>-<topic-slug>/minutes.md`
- Evaluation scores (Depth / Efficiency / Novelty / Convergence / Balance / Psychological Safety / Total)

### Behavioral Rules
- Never run debate steps inline. Always delegate to the debate-runner agent.
- Do not ask for confirmation between steps — confirm parameters once, spawn agent, report results.
- If the topic is not provided, ask once and then proceed.
- All minutes output is in Japanese. Character names and MBTI types remain in English.

## Examples

**User:** "AIは人間の仕事を奪うかについて弁証法でディベートして"

> Session parameters confirmed:
> - Topic: Will AI eliminate more jobs than it creates?
> - Approach: `dialectic`
> - Participants: Standard 5 (Visionary, Devil's Advocate, Empathizer, Pragmatist, Analyst)
> - Rounds: 5 / Expertise: Informed / Stakes: Low / Power: Flat
> - Output: outputs/2026-04-04-ai-job-displacement/
>
> Spawning debate-runner agent…

*(agent runs in isolation, writes transcript.md and minutes.md)*

> Complete.
> - outputs/2026-04-04-ai-job-displacement/transcript.md
> - outputs/2026-04-04-ai-job-displacement/minutes.md
>
> Scores: Depth 4 / Efficiency 3 / Novelty 4 / Convergence 5 / Balance 5 / Safety 4 — Total 25/30
