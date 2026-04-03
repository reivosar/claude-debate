# Session Variables

Variables set per session to modulate how participants behave. These are applied on top of the base MBTI persona and modify intensity, tone, and decision-making patterns. Set at the start of `/debate` or pass explicitly to `/facilitate`.

---

## (expertise-level) Expertise Level

How much each participant knows about the debate topic.

| Level | Description | Effect on debate |
|-------|-------------|-----------------|
| **Expert** | Deep domain knowledge. Can cite specifics, mechanisms, and edge cases. | Technical depth increases; risk of jargon, blind spots to lay perspectives, and overconfidence |
| **Informed** | General understanding. Familiar with the main arguments but not the details. *(default)* | Balanced. Accessible language, moderate depth |
| **Novice** | Little prior knowledge. Relies on intuition and first principles. | Naive but often generative questions; challenges assumptions experts take for granted; lower technical credibility |

**Mixed expertise** is the most productive configuration: at least one Expert and one Novice forces translation between levels and often surfaces hidden assumptions.

---

## (stakes) Stakes

How directly the debate outcome affects each participant.

| Level | Description | Effect on debate |
|-------|-------------|-----------------|
| **High** | The outcome directly affects the participant's work, livelihood, or values. | Increased defensiveness and emotional investment; more motivated argumentation; harder to concede |
| **Medium** | Indirect or partial personal relevance. | Moderate engagement |
| **Low** | Third-party or academic interest only. *(default)* | Objective but lower energy; may underweight practical consequences |

Stakes can be set uniformly (all participants at the same level) or asymmetrically (some participants have high stakes, others low). Asymmetric stakes surface power and empathy dynamics.

---

## (power-dynamic) Power Dynamic

The social hierarchy among participants.

| Setting | Description | Effect on debate |
|---------|-------------|-----------------|
| **Flat** | All participants are peers with equal standing. *(default)* | Full freedom of speech; challenges are expected and accepted |
| **Hierarchical** | Explicit status differences exist (e.g., senior/junior, expert/layperson, employer/employee). | Lower-status participants self-censor, hedge, or defer; higher-status participants may dominate without noticing |
| **Reversed** | A participant who would normally be lower-status is granted authority for the session. | Surfaces suppressed perspectives; challenges dominant narratives |

When Hierarchical is set, the facilitator actively compensates: direct invitations to lower-status voices, and naming of deference when it occurs.

---

## (enneagram-override) Enneagram Override

Assign a specific Enneagram type to a character to override the default affinity. This adds a motivational layer on top of MBTI.

Format: `[Character name]: Enneagram [N]`

Example:
```
Visionary (INTJ): Enneagram 1
Pragmatist (ESTJ): Enneagram 6
```

See `personas.md#enneagram` for type definitions.

---

## (big-five-override) Big Five Override

Adjust individual Big Five traits to shift a character's behavior within their MBTI type. Use when a more specific personality profile is needed.

Format: `[Character name]: [Trait]-[Level]`

Example:
```
Analyst (INTP): N-High   ← makes them more reactive to criticism than the default
Commander (ENTJ): A-Mid  ← softens their dismissiveness toward minority views
```

Only specify traits you are changing. Unspecified traits revert to the defaults in `personas.md#character-roster`.

---

## (recommended-configurations) Recommended Configurations by Goal

| Goal | Expertise | Stakes | Power Dynamic |
|------|-----------|--------|---------------|
| Surface hidden assumptions | Mixed (Expert + Novice) | Low | Flat |
| Stress-test a proposal | Expert | High | Flat |
| Explore ethical dimensions | Informed | High (asymmetric) | Flat |
| Simulate real organizational decision | Informed | High | Hierarchical |
| Generate creative alternatives | Novice + Informed | Low | Flat |
| Challenge dominant narrative | Mixed | High | Reversed |

---

## (how-to-apply) How to Apply Variables

Variables are declared in the session header and applied throughout:

1. **Expertise**: Adjust the depth and specificity of each character's claims. Novice characters ask "why" more; Expert characters cite specifics and may use jargon.
2. **Stakes**: High-stakes characters defend positions longer, show more emotion, and are less willing to concede. Low-stakes characters are more exploratory.
3. **Power Dynamic (Hierarchical)**: Higher-status characters speak with more authority and interrupt more; lower-status characters hedge ("I might be wrong, but..."), wait to be called on, and avoid direct contradiction of higher-status speakers.
4. **Enneagram/Big Five overrides**: Apply the motivation or trait shift to every statement the character makes.
