---
name: minutes
description: |
  Use this skill when the user asks to take minutes, record the debate, or produce a meeting record.
  Triggers: "take minutes", "record this debate", "write up the discussion", "議事録",
  or when a structured record of the debate is needed during or after a session.
---

# Minutes

## Overview
Produce a complete, structured record of the debate using the template at `.claude/templates/minutes.md`. The record has three layers: (1) an executive summary for quick orientation, (2) a full transcript preserving every statement in full, and (3) an index for navigation. The record must be accurate and complete enough to reconstruct the debate from scratch without having attended it.

## Instructions

**Step 1: Load the transcript**
- Read `outputs/<session-id>/transcript.md` — this is the raw record of every statement written during the session.
- All subsequent steps are compiled from this file. Do not reconstruct content from memory.

**Step 2: Initialize the record**
- Fill in the header: date, topic, approach skill, whether a facilitator was present, number of rounds.
- List all participants with MBTI type and their stated initial position.

**Step 3: Write the Full Transcript**
- Copy every statement from `transcript.md` verbatim. Do not compress.
- Format each statement as its own named section: `### Statement N — [Speaker] ([MBTI]) — [Type]`
- Place the full statement text in a blockquote.
- Apply flags inline in the section heading where applicable: `[PIVOT]`, `[TURN]`, `[OPEN]`, `[AMBIGUOUS]`.
- Do not editorialize. Record what was said, not whether it was correct.

**Step 4: Build the Statement Index**
- After the full transcript, produce the index table.
- One row per statement: number, speaker, type, flag (if any), one-line summary.
- The index is for navigation only — it does not replace the transcript.

**Step 5: Flag Key Moments**
- Identify the 3–5 most significant statements or exchanges in the Key Moments section.
- For each, explain in one sentence why it mattered — what it changed, opened, or resolved.

**Step 6: Write the Executive Summary**
- After completing the transcript and index, write a 150–250 word narrative of the debate.
- Cover: how the debate opened, what the main tensions were, which moments shifted the conversation, and where it landed.
- Write for a reader who did not attend. No jargon; no unexplained references.

**Step 7: Convergence**
- List points of genuine agreement.
- List unresolved disagreements and classify each by type: Factual / Values / Predictive / Definitional.
- List new questions the debate opened that were not present at the start.

**Step 8: Evaluation**
- Score the session 1–5 on each dimension from `debate-rules.md#evaluation-criteria`: Depth / Efficiency / Novelty / Convergence / Balance / Psychological Safety.
- Write one justification sentence per dimension.
- Scoring is performed by `/minutes`, not the facilitator.
- Convergence: score based on how clearly the map of agreement and disagreement was drawn — NOT on how much agreement was reached. A debate that names three irreconcilable value-based disagreements scores higher than one that manufactured vague consensus.

**Step 9: Output**
- Produce the completed minutes using the full template structure.
- Save to `outputs/YYYY-MM-DD-<topic-slug>/minutes.md`.

### Behavioral Rules
- The full transcript is the primary record. The index and summary are secondary.
- Record all voices equally — do not give more space to dominant speakers.
- Preserve disagreement and tension in the record. Do not smooth it over.
- If a statement was ambiguous, record it as stated and flag `[AMBIGUOUS]`. Do not interpret.
- Minutes are always written in Japanese, regardless of the language the debate was conducted in.

## Examples

```markdown
### Statement 1 — Visionary (INTJ) — Claim

> AI regulation is necessary. Without legally binding international standards, market incentives will consistently prioritize capability development over safety. The EU AI Act demonstrates that comprehensive regulation is achievable; the question is whether it scales globally.

### Statement 2 — Devil's Advocate (ENTP) — Rebuttal [PIVOT]

> That assumes regulators can understand what they're regulating — which is historically false in fast-moving technology sectors. GDPR took effect years after the practices it targeted were already entrenched. By the time international AI regulation is agreed upon and enforced, the technology it governs will have moved on entirely.

### Statement 3 — Analyst (INTP) — Question [TURN]

> Before we go further: what do we mean by "regulation"? Ex ante rules that constrain development? Ex post liability frameworks? Mandatory disclosure? These are substantially different interventions with different feasibility profiles. We may be talking past each other.
```

```markdown
## Statement Index

| # | Speaker | Type | Flag | One-line summary |
|---|---------|------|------|-----------------|
| 1 | Visionary (INTJ) | Claim | | Binding international standards are necessary; EU AI Act as proof of concept. |
| 2 | Devil's Advocate (ENTP) | Rebuttal | [PIVOT] | Regulators historically can't keep pace with fast-moving technology. |
| 3 | Analyst (INTP) | Question | [TURN] | "Regulation" is undefined — ex ante rules vs. ex post liability are different things. |
```
