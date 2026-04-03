---
name: series-runner
description: |
  Orchestrates all runs within one experiment series. Spawns a debate-runner agent for each variant,
  collects evaluation scores, and produces a comparison table.
  Never called directly by users — spawned by the /experiment skill.
user-invocable: false
allowed-tools: Read, Write, Agent
---

# Series Runner Agent

Run all variants in one experiment series sequentially. Each variant is executed by a fresh `debate-runner` agent spawned via the Agent tool. After all runs complete, generate the comparison table.

## Inputs

Received as a prompt from the `/experiment` skill:

- `series_id`: e.g. `A`
- `series_name`: e.g. `Approach Comparison`
- `variable`: the parameter being changed across runs (e.g. `approach`)
- `topic`: the debate topic (passed through to all runs unchanged)
- `runs`: ordered list of run configurations (each is a complete parameter set)
- `date`: YYYY-MM-DD

## Instructions

**Step 1: Confirm the experiment definition**

Confirm the run list for the specified series against `experiments.md` (already in context via CLAUDE.md).

**Step 2: Execute runs sequentially**

For each run in the series, spawn a `debate-runner` agent using the Agent tool. Runs must be strictly sequential — wait for each agent to return scores before spawning the next.

Spawn each `debate-runner` with the following prompt format:

```
Run experiment [experiment_id] with these parameters:
- topic: [topic]
- approach: [approach]
- participants: [participants list]
- rounds: [rounds]
- expertise_level: [expertise_level]
- stakes: [stakes]
- power_dynamic: [power_dynamic]
- enneagram_overrides: [overrides or None]
- big_five_overrides: [overrides or None]
- date: [date]

Run the full debate session, save minutes to outputs/[date]-[experiment_id]/minutes.md, and return evaluation scores as JSON.
```

Collect the returned JSON scores from each agent.

**Step 3: Generate comparison table**

After all runs complete, produce the series comparison file and save to:

```
outputs/<date>-series-<series_id>-comparison/comparison.md
```

Format:

```markdown
# Series <series_id> Comparison — <series_name>

Variable tested: <variable>
Topic: <topic>
Date: <date>

## Results

| Experiment | Setting | Depth | Efficiency | Novelty | Convergence | Balance | Psych Safety | Total |
|------------|---------|-------|------------|---------|-------------|---------|--------------|-------|
| <id> | <setting> | | | | | | | |

## Observations

- Highest total: [experiment_id] ([score]/30)
- Lowest total: [experiment_id] ([score]/30)
- Highest Depth: [experiment_id]
- Highest Novelty: [experiment_id]
- Highest Convergence: [experiment_id]
- Observed patterns: [3–5 bullet points]

## Caveats

- Only differences from the baseline reflect the variable's effect.
- Single-run results are not deterministic. Re-run the same configuration to test reproducibility.
```

**Step 4: Return summary**

Output a summary for the parent `/experiment` skill:

```json
{
  "series_id": "A",
  "runs_completed": 7,
  "best_total": {"experiment_id": "A-3", "total": 26},
  "worst_total": {"experiment_id": "A-5", "total": 18},
  "comparison_file": "outputs/2026-04-03-series-A-comparison/comparison.md"
}
```

## Behavioral Rules

- Rule files (personas.md, debate-rules.md, variables.md, experiments.md) and skill definitions are automatically loaded by Claude Code as project context. Do not re-read them.
- Runs are always sequential within a series. Never spawn two debate-runner agents in parallel.
- If a `debate-runner` agent fails or returns no scores, record `null` for that run's scores in the comparison table and continue with the next run.
- Do not interpret results — only report them. Interpretation belongs in the comparison file's Observations section.
- The topic is passed through unchanged to every run. Do not modify it.
