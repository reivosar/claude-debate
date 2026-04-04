# claude-debate

A framework for running structured debate sessions inside Claude Code, using psychological and philosophical dialogue techniques as skills. Designed to compare which approach produces the most efficient, deep, and valuable debate on a given topic.

## Concept

Each debate approach (Socratic, Dialectic, Six Thinking Hats, etc.) is implemented as a Claude Code skill. Participant personas are defined by MBTI type, Big Five traits, Enneagram affinity, and cognitive biases. The same topic can be run through multiple configurations and evaluated on consistent dimensions, enabling controlled comparison.

## Requirements

- [Claude Code](https://claude.ai/code) CLI

## Usage

### Single session

```
/debate "Does remote work improve productivity?"
```

Confirms parameters, spawns an isolated `debate-runner` agent, and reports results when done. The agent writes each statement to disk as it generates it, keeping the main session context clean. Saves to `outputs/`.

### Controlled experiment

```
/experiment A "Does AI threaten democracy?"
```

Runs all variants in a series (e.g., Series A = all 7 approaches) on the same topic via isolated agents, then produces a comparison table.

```
/experiment A B "Should capital punishment be abolished?"
/experiment all "Is climate action an individual responsibility?"
/experiment A-3 "Will AI eliminate more jobs than it creates?"
```

## Debate Approaches

| Command | Approach |
|---------|----------|
| `/socratic` | Socratic Method — deepen thinking through probing questions |
| `/dialectic` | Dialectic Method — thesis / antithesis / synthesis |
| `/six-hats` | Six Thinking Hats — parallel thinking by perspective |
| `/steelmanning` | Steelmanning — argue the strongest version of the opposing view |
| `/open-dialogue` | Open Dialogue — polyphonic, non-hierarchical exchange |
| `/motivational-interviewing` | Motivational Interviewing — surface ambivalence and intrinsic motivation |
| `/narrative` | Narrative Approach — explore through story and lived experience |

## Session Management

| Command | Role |
|---------|------|
| `/debate` | Run a full single session end-to-end |
| `/experiment` | Run a controlled experiment series via agents |
| `/facilitate` | Moderate and chair a session |
| `/conclude` | Synthesize a rational conclusion from the debate |
| `/minutes` | Produce a structured Japanese record of the session |

## Participant Presets

| Preset | Participants |
|--------|-------------|
| Standard (5) | Visionary (INTJ), Devil's Advocate (ENTP), Empathizer (INFP), Pragmatist (ESTJ), Analyst (INTP) |
| Critical Scrutiny (3) | Analyst (INTP), Commander (ENTJ), Defender (ISFJ) |
| Creative Divergence (5) | Activist (ENFP), Devil's Advocate (ENTP), Mediator (INFJ), Detective (ISTP), Entertainer (ESFP) |
| Ethics and Social Issues (4) | Mediator (INFJ), Commander (ENTJ), Adventurer (ISFP), Pragmatist (ESTJ) |

Custom configurations (any combination of the 16 MBTI types) are also supported. See `.claude/rules/personas.md`.

## Session Variables

Each session can be tuned with the following variables:

| Variable | Options |
|----------|---------|
| Expertise Level | Expert / Informed (default) / Novice / Mixed |
| Stakes | High / Medium / Low (default) / Asymmetric |
| Power Dynamic | Flat (default) / Hierarchical / Reversed |
| Enneagram override | Assign a specific Enneagram type to a character |
| Big Five override | Adjust individual traits (e.g., `Commander (ENTJ): A-Mid`) |

## Experiment Series

Controlled experiments change one variable at a time against a fixed baseline.

| Series | Variable |
|--------|----------|
| A | Approach (all 7 skills) |
| B | Expertise Level |
| C | Stakes |
| D | Power Dynamic |
| E | Enneagram override |
| F | Big Five override |

Baseline: `/socratic`, Standard 5, Informed, Low stakes, Flat power dynamic.

## Evaluation Dimensions

Each session is scored 1–5 on six dimensions:

| Dimension | Description |
|-----------|-------------|
| Depth | Did the debate reach fundamental assumptions? |
| Efficiency | How much insight per turn? |
| Novelty | Did genuinely new perspectives emerge? |
| Convergence | Did participants reach shared understanding? |
| Balance | Did all participants contribute equally? |
| Psychological Safety | Could all participants speak freely? |

## Project Structure

```
.claude/
  agents/
    debate-runner/    # Isolated single-run debate agent
    series-runner/    # Orchestrates full experiment series
  rules/
    debate-rules.md   # Structure, prohibited conduct, evaluation criteria
    experiments.md    # Experiment series definitions and baseline
    personas.md       # Character roster, presets, Big Five/Enneagram reference
    variables.md      # Session variable definitions and effects
  skills/             # One directory per skill/command
  templates/
    minutes.md        # Minutes template
outputs/              # Generated debate records (not tracked in git)
```

## Output

Each session produces its own folder under `outputs/`:

```
outputs/
  YYYY-MM-DD-<topic-slug>/           ← /debate sessions
    transcript.md
    minutes.md
  YYYY-MM-DD-<series>-<id>/          ← /experiment runs
    transcript.md
    minutes.md
  YYYY-MM-DD-series-<series>-comparison/
    comparison.md
```

Minutes are written in Japanese. Character names and MBTI types remain in English. The `outputs/` directory is excluded from version control.
