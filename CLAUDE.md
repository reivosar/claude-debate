# claude-debate

A project for implementing psychological approaches as Claude Code skills and comparing which method produces the most efficient and valuable debate.

## Rules

- Participant personas: `.claude/rules/personas.md`
- Debate best practices and evaluation criteria: `.claude/rules/debate-rules.md`

## Skills

### Debate Approaches
| Command | Approach |
|---------|----------|
| `/socratic` | Socratic Method |
| `/dialectic` | Dialectic Method |
| `/six-hats` | Six Thinking Hats |
| `/steelmanning` | Steelmanning |
| `/open-dialogue` | Open Dialogue |
| `/motivational-interviewing` | Motivational Interviewing |
| `/narrative` | Narrative Approach |

### Session Management
| Command | Role |
|---------|------|
| `/debate` | Run a full debate session end-to-end (single session) |
| `/experiment` | **Run controlled experiment series via agents** (recommended for comparison) |
| `/facilitate` | Moderate and chair the debate session |
| `/conclude` | Synthesize the debate into a rational conclusion |
| `/minutes` | Record the debate using the minutes template |

## Agent Architecture

```
/experiment
  └── series-runner agent  (1 per series, parallel across series)
        └── debate-runner agent  (1 per run, sequential within series)
              → saves outputs/YYYY-MM-DD-<series>-<id>.md
```

- `debate-runner`: clean context per run — no cross-session contamination
- `series-runner`: collects scores, generates comparison table
- Agents defined in `.claude/agents/`

## Workflow

**Single session:**
```
/debate "Does remote work improve productivity?"
```

**Controlled experiment:**
```
/experiment A "Does remote work improve productivity?"
/experiment A B "Does AI threaten democracy?"
/experiment all "Should capital punishment be abolished?"
/experiment A-3 "Is climate action an individual responsibility?"
```

```
/experiment <series> "<topic>"
    └── series-runner agent
          └── debate-runner agent × runs
                → outputs/YYYY-MM-DD-<series>-<id>.md
          → outputs/YYYY-MM-DD-series-<series>-comparison.md
```

## Templates

- Minutes template: `.claude/templates/minutes.md`
- Completed minutes: `outputs/YYYY-MM-DD-<topic-slug>/minutes.md`

## Experiment Design

- Controlled experiments: `.claude/rules/experiments.md`
- Change **one variable at a time** against the fixed baseline
- Series A (approach) → B (expertise) → C (stakes) → D (power) → E (enneagram) → F (big five)
- Minutes naming: `outputs/YYYY-MM-DD-<series>-<id>.md`

## Principles

- Skills define behavior only — no configuration or evaluation criteria inside skill files.
- Participant settings and evaluation criteria are managed in rule files.
- Run multiple approaches on the same topic to enable direct comparison.

## Section Reference Convention

All rule file headings carry an inline ID in the form `(id)`. When referencing a specific section, use `filename.md#id` — do not load an entire file when only a section is needed.

| Reference | Section |
|-----------|---------|
| `personas.md#preset-standard` | Standard participant preset |
| `personas.md#intj` | Visionary (INTJ) character |
| `personas.md#cognitive-biases` | Cognitive biases reference |
| `experiments.md#baseline` | Experiment baseline configuration |
| `experiments.md#series-a` | Series A experiment definitions |
| `debate-rules.md#evaluation-criteria` | Evaluation scoring dimensions |
| `debate-rules.md#phase-3` | Round rules and statement targets |
| `variables.md#expertise-level` | Expertise level definitions |
| `variables.md#power-dynamic` | Power dynamic settings |

## Output Rules

- **Never output debate transcripts, statements, or minutes inline in the chat.** Write all content directly to files only.
- After completing a session, report only: output file path(s) and evaluation score summary.
- This applies to all skills: `/debate`, `/facilitate`, `/conclude`, `/minutes`, and all approach skills.
