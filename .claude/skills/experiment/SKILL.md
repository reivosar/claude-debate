---
name: experiment
description: |
  Use this skill to run one or more experiment series from the controlled experiment design.
  Triggers: "run experiment", "実験を走らせて", "series A を実行", "全シリーズ実行",
  or when the user wants to compare debate approaches or variable effects using the controlled design in experiments.md.
argument-hint: <series> "<topic>"
---

# Experiment

## Overview

Entry point for the experiment system. Reads the experiment definition from `.claude/rules/experiments.md`, spawns a `series-runner` agent for each requested series, and collects results. Each series runs all its variants through isolated `debate-runner` agents, ensuring clean context per run.

```
/experiment
    └── series-runner (Series A)
    │     ├── debate-runner: A-0  → outputs/YYYY-MM-DD-A-0.md
    │     ├── debate-runner: A-1  → outputs/YYYY-MM-DD-A-1.md
    │     └── → outputs/YYYY-MM-DD-series-A-comparison.md
    └── series-runner (Series B)          ← parallel if multiple series requested
          ├── debate-runner: B-0
          └── ...
```

## Instructions

**Step 1: Parse the request**

Arguments are passed as: `/experiment <series> "<topic>"`

Parse `$ARGUMENTS` to extract:

1. **Series** — first token(s): `A`, `B`, `A B`, `all`, or a specific run like `A-3`
   - If not provided, ask once: "Which series do you want to run? (A–F, or all)"

2. **Topic** — everything after the series identifier, quoted or unquoted
   - If not provided, ask once: "Enter the debate topic (e.g. 'Should AI development be internationally regulated?')"
   - The topic is applied to all runs in the session as the fixed debate subject.

Examples:
```
/experiment A "Does remote work improve productivity?"
/experiment A B "Does AI threaten democracy?"
/experiment all "Should capital punishment be abolished?"
/experiment A-3 "Is climate action an individual responsibility?"
```

**Step 2: Read experiment definitions**

Read `.claude/rules/experiments.md` and extract the full run configuration for each requested series. Replace the hardcoded baseline topic with the user-provided topic for all runs.

**Step 3: Spawn series-runner agents**

- If one series: spawn one `series-runner` agent (foreground).
- If multiple series: spawn all `series-runner` agents in parallel (each series is independent).

Pass to each `series-runner`:
- `series_id`
- `series_name`
- `variable` (what is being changed)
- `runs` (full list of run parameter sets from `experiments.md`)
- `date` (today's date: YYYY-MM-DD)

**Step 4: Collect and report results**

After all series-runner agents complete, output a summary:

```
Experiment Run Complete
=======================
Date: YYYY-MM-DD
Topic: <topic>

Series A — Approach Comparison
  Runs completed: 7
  Highest score: A-3 / steelmanning (26/30)
  Lowest score: A-5 / motivational-interviewing (18/30)
  Comparison file: outputs/YYYY-MM-DD-series-A-comparison.md

Series B — Expertise Level
  ...
```

### Behavioral Rules

- Series-runner agents within a series run variants sequentially (context isolation requires one debate at a time).
- Multiple series can run in parallel with each other.
- Do not interpret results here — interpretation is in each series comparison file.
- All output files are saved under `outputs/<date>-<id>/`. Never overwrite existing files — use the date+experiment_id naming to ensure uniqueness.
- If the user requests a single run (e.g. "A-1だけ走らせて"), spawn one `series-runner` with a single-run list.

## Examples

**Run all approach variants:**
```
/experiment A "Does remote work improve productivity?"
```
→ Spawns one series-runner for Series A, which runs A-0 through A-6 sequentially via debate-runner agents.

**Run two series in parallel:**
```
/experiment A B "Does remote work improve productivity?"
```
→ Spawns series-runner for A and series-runner for B simultaneously, both on the same topic.

**Run a single experiment:**
```
/experiment A-3 "Does remote work improve productivity?"
```
→ Spawns one series-runner configured for the single run A-3 (steelmanning).
