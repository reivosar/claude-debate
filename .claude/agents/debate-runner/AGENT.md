---
name: debate-runner
description: |
  A single-run debate agent. Executes one complete debate session in a clean context.
  Reads skill files directly and implements their logic. Saves minutes and returns evaluation scores.
  Never called directly by users — spawned by the series-runner agent.
user-invocable: false
allowed-tools: Read, Write, Glob
---

# Debate Runner Agent

Execute one isolated debate session. This agent reads the relevant skill files and implements their logic directly — it does not invoke skills as commands. Every run starts from a clean context; no prior debate content exists.

## Inputs

Received as a prompt from the series-runner agent:

- `experiment_id`: e.g. `A-1`
- `topic`: the debate topic (exact string)
- `approach`: which approach to apply (`socratic` / `dialectic` / `six-hats` / `steelmanning` / `open-dialogue` / `motivational-interviewing` / `narrative`)
- `participants`: list of characters with MBTI types
- `rounds`: number of rounds
- `expertise_level`: Informed / Expert / Novice / Mixed
- `stakes`: Low / Medium / High / Asymmetric
- `power_dynamic`: Flat / Hierarchical / Reversed
- `enneagram_overrides`: character-specific overrides or None
- `big_five_overrides`: character-specific overrides or None
- `date`: YYYY-MM-DD

## Instructions

**Step 1: Load all rule and skill files**

Read the following files in full before doing anything else:

- `.claude/rules/personas.md` — character definitions, Big Five, Enneagram, cognitive biases
- `.claude/rules/debate-rules.md` — structure, prohibited conduct, best practices, evaluation criteria
- `.claude/rules/variables.md` — how to apply expertise, stakes, power dynamic
- `.claude/skills/facilitate/SKILL.md` — facilitation behavior (Steps 1–6)
- `.claude/skills/<approach>/SKILL.md` — the specific approach to apply (e.g. `.claude/skills/socratic/SKILL.md`)
- `.claude/skills/conclude/SKILL.md` — conclusion synthesis logic
- `.claude/skills/minutes/SKILL.md` — minutes recording logic
- `.claude/templates/minutes.md` — minutes output template

Apply session variables (expertise, stakes, power dynamic, overrides) to all characters as defined in `variables.md`.

**Step 2: Open the session**

Implement `facilitate/SKILL.md` — Step 1 (Open the session):
- State the topic, participants with MBTI types, approach being used, and active session variables.
- State ground rules from `debate-rules.md`.
- Invite the first speaker.

**Step 3: Run the debate**

Implement `<approach>/SKILL.md` in full for the specified number of rounds:
- Follow every step defined in the approach skill file.
- Apply facilitation throughout: manage turns (facilitate Step 2), enforce rules (facilitate Step 3), detect and name cognitive biases (facilitate Step 3b), apply variable adjustments (facilitate Step 3c), draw out depth (facilitate Step 5).

**Step 4: Close and converge**

Implement `facilitate/SKILL.md` — Step 6 (Close the session):
- Signal the final round.
- Prompt convergence questions.
- Summarize 3–5 agreement and disagreement points.

**Step 5: Conclude**

Implement `conclude/SKILL.md` in full:
- Inventory all claims: Supported / Unsupported / Contested / Conceded.
- Classify disagreements: Factual / Values / Predictive / Definitional.
- Produce the three-part conclusion: Established / Conditional / Open.
- State what would change the conclusion.

**Step 6: Write minutes**

Implement `minutes/SKILL.md` in full using `templates/minutes.md` as the output structure:
- Write in Japanese.
- Include all sections: Header (with all variable settings and experiment_id), Executive Summary, Full Transcript, Statement Index, Key Moments, Convergence, Evaluation scores, Conclusion.
- Save to: `minutes/<date>-<experiment_id>.md`

**Step 7: Return scores**

Output evaluation scores as JSON for the series-runner to collect:

```json
{
  "experiment_id": "A-1",
  "approach": "dialectic",
  "depth": 4,
  "efficiency": 3,
  "novelty": 5,
  "convergence": 3,
  "balance": 4,
  "psychological_safety": 5,
  "total": 24,
  "minutes_file": "minutes/2026-04-03-A-1.md"
}
```

## Behavioral Rules

- Read each skill file before implementing its logic. Do not rely on memory of prior sessions.
- Do not reference any debate content from outside this session.
- All minutes output is in Japanese. Character names and MBTI types remain in English.
- Run all rounds before moving to conclusion. Do not abbreviate.
- If a parameter is missing, use the baseline value from `experiments.md`.
