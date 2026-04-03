# Experiment Configurations

Changing multiple variables simultaneously makes it impossible to attribute differences in debate quality to any specific factor. All experiments follow a controlled design: one variable changes at a time; everything else is held at the baseline.

---

## Baseline (Control)

All experiments are compared against this baseline. Do not modify the baseline between experiments.

| Parameter | Baseline value |
|-----------|---------------|
| Topic | *(set by user at runtime via `/experiment <series> "<topic>"`)* |
| Approach | `/socratic` |
| Participants | Standard 5: Visionary (INTJ), Devil's Advocate (ENTP), Empathizer (INFP), Pragmatist (ESTJ), Analyst (INTP) |
| Rounds | 3 |
| Facilitator | Enabled |
| Expertise Level | Informed |
| Stakes | Low |
| Power Dynamic | Flat |
| Enneagram override | None |
| Big Five override | None |

---

## Experiment Series

Each series isolates one variable. Run the baseline first, then each variant. Record evaluation scores for every run in `outputs/`.

---

### Series A — Approach (Psychological Approach Comparison)

**Variable:** Approach skill  
**All other parameters:** Baseline

| Experiment | Approach |
|------------|----------|
| A-0 (baseline) | `/socratic` |
| A-1 | `/dialectic` |
| A-2 | `/six-hats` |
| A-3 | `/steelmanning` |
| A-4 | `/open-dialogue` |
| A-5 | `/motivational-interviewing` |
| A-6 | `/narrative` |

**What to measure:** Which approach produces the highest scores on Depth, Novelty, and Convergence for this topic?

---

### Series B — Expertise Level (Effect of Domain Knowledge)

**Variable:** Expertise Level  
**All other parameters:** Baseline (approach = `/socratic`)

| Experiment | Expertise Level |
|------------|----------------|
| B-0 (baseline) | Informed |
| B-1 | Expert |
| B-2 | Novice |
| B-3 | Mixed (Visionary=Expert, Empathizer=Novice, others=Informed) |

**What to measure:** Does expertise level affect Depth and Efficiency? Does mixed expertise produce more Novelty?

---

### Series C — Stakes (Effect of Personal Investment)

**Variable:** Stakes  
**All other parameters:** Baseline (approach = `/socratic`)

| Experiment | Stakes |
|------------|--------|
| C-0 (baseline) | Low |
| C-1 | High (all participants) |
| C-2 | Asymmetric (Visionary=High, others=Low) |

**What to measure:** Does high stakes increase Depth and reduce Balance? Does asymmetric stakes surface power and empathy dynamics?

---

### Series D — Power Dynamic (Effect of Hierarchy)

**Variable:** Power Dynamic  
**All other parameters:** Baseline (approach = `/socratic`)

| Experiment | Power Dynamic | Status assignment |
|------------|--------------|-------------------|
| D-0 (baseline) | Flat | — |
| D-1 | Hierarchical | Commander (ENTJ) = senior; others = junior |
| D-2 | Reversed | Empathizer (INFP) = authority; others = deferential |

**What to measure:** Does Hierarchical power reduce Psychological Safety and Balance? Does Reversed power surface new perspectives (Novelty)?

---

### Series E — Enneagram Override (Effect of Motivational Type)

**Variable:** Enneagram type assigned to one character  
**All other parameters:** Baseline (approach = `/socratic`)  
**Target character:** Visionary (INTJ) — default affinity is 5 (Investigator)

| Experiment | Visionary's Enneagram |
|------------|----------------------|
| E-0 (baseline) | 5 (Investigator) — default |
| E-1 | 1 (Perfectionist) |
| E-2 | 8 (Challenger) |
| E-3 | 9 (Peacemaker) |

**What to measure:** Does the Enneagram type of one character measurably shift Depth, Balance, or Convergence scores?

---

### Series F — Big Five Override (Effect of Personality Trait Adjustment)

**Variable:** One Big Five trait on one character  
**All other parameters:** Baseline (approach = `/socratic`)  
**Target character:** Commander (ENTJ) — default A (Agreeableness) = Low

| Experiment | Commander's Agreeableness |
|------------|--------------------------|
| F-0 (baseline) | A-Low (default) |
| F-1 | A-Mid |
| F-2 | A-High |

**What to measure:** Does raising Agreeableness in a dominant character improve Balance and Psychological Safety without reducing Depth?

---

## Recording Results

After each experiment run, record the evaluation scores in the minutes file using the naming convention:

```
outputs/YYYY-MM-DD-<series>-<experiment-id>/minutes.md
```

Examples:
```
outputs/2026-04-03-A-0-baseline/minutes.md
outputs/2026-04-03-A-1-dialectic/minutes.md
outputs/2026-04-03-B-3-mixed-expertise/minutes.md
```

---

## Comparison Table

After completing a series, populate this table:

| Experiment | Depth | Efficiency | Novelty | Convergence | Balance | Psych Safety | Total |
|------------|-------|------------|---------|-------------|---------|--------------|-------|
| A-0 (baseline) | | | | | | | |
| A-1 | | | | | | | |
| A-2 | | | | | | | |

**Rule:** Do not interpret results until an entire series is complete. Single-run comparisons are not meaningful.

---

## Confound Checklist

Before running any experiment, confirm:
- [ ] Only one variable differs from the baseline
- [ ] The topic is identical to the baseline
- [ ] The participant configuration is identical to the baseline
- [ ] The number of rounds is identical to the baseline
- [ ] The facilitator is enabled (same as baseline)
- [ ] Results are recorded immediately after the run
