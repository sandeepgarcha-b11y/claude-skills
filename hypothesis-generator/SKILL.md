---
name: hypothesis-generator
description: Generate strong, ranked, testable product hypotheses from a problem statement. Use when turning a problem or opportunity into discovery or experiment hypotheses worth investing in.
---

# hypothesis-generator — the discovery function

Turn a problem statement into a ranked set of measurable hypotheses — each tied
to a user problem, an expected metric move, and a first test. No vague brainstorm.

## Intake

Ask for whatever is not supplied — do not guess:

- **Product area** — the surface or flow in scope (e.g. activation, checkout, auth).
- **User problem / opportunity** — who hurts, when, and the evidence for it.
- **Business goal** — the outcome this serves (e.g. lift conversion, cut churn).
- **Constraints** — tech, legal, brand, timeline, or resourcing limits.
- **Target metric** — the primary measure a hypothesis must move.
- **Type wanted** — discovery hypotheses, experiment hypotheses, or both.

**If any required input (product area, user problem, business goal, target
metric) is missing, ask for it first and do not proceed.**

## Steps

1. Restate the user problem in one sentence so every hypothesis traces back to it.
2. Generate candidates, then convert each into a true hypothesis: *We believe
   `<change>` will cause `<metric>` to `<move>` for `<user>` because `<reason>`.*
3. Discard anything not measurable or not falsifiable — a hypothesis must be able
   to be wrong.
4. Score each on expected impact, confidence, and effort; rank by impact ÷ effort
   weighted by confidence.
5. For every hypothesis, write at least one counter-argument / failure mode and
   the cheapest first test.
6. Separate true hypotheses from bare **solution ideas** (a feature with no causal
   claim) — list the latter apart so they aren't mistaken for testable bets.

## Output format

Use only `<angle-bracket>` placeholders below; do not invent concrete values,
numbers, or names. Keep every section in the exact order shown — do not add,
drop, or reorder them.

```markdown
# Hypotheses — <product area> · goal: <business goal>

**User problem:** <one-sentence restatement.>

## Ranked hypotheses
### 1. <Hypothesis title>
- **Statement:** We believe `<change>` will cause `<target metric>` to `<move>`
  for `<user>` because `<reason>`.
- **User problem behind it:** <the underlying need.>
- **Why it might work:** <mechanism / evidence.>
- **Expected metric movement:** `<metric>` <direction + rough magnitude band>.
- **Confidence:** <high | medium | low> — <why>.
- **Effort:** <low | medium | high>.
- **Key risk / failure mode:** <the strongest reason it won't work.>
- **Suggested first test:** <cheapest way to learn — fake door, prototype, A/B…>

### 2. <…>

## Solution ideas (not yet hypotheses)
- <Idea> — needs a causal claim + metric before it can be tested.
```

## Guardrails

- **No vague brainstorm ideas** — every entry is a falsifiable statement.
- **Every hypothesis must be measurable** against the target metric.
- **Include at least one counter-argument or risk** per hypothesis.
- **Separate solution ideas from true hypotheses** — never blur the two.
- If evidence for the underlying problem is weak, say so before ranking.

## Example

Intake: *Area `<activation>`; problem `<new users don't reach first value>`;
goal lift day-7 activation; metric `<activation rate>`; type both.*

A ranked entry's statement: `We believe `<a guided first-run checklist>` will
cause `<activation rate>` to `<rise>` for `<first-time users>` because `<it
removes ambiguity about the first valuable action>`.` — risk: `<checklist
fatigue could depress completion>`; first test: `<concierge / Wizard-of-Oz run>`.
