---
name: experiment-review
description: Review an A/B test and make an honest, caveated product recommendation. Use when reading out experiment results and deciding to ship, iterate, or kill.
---

# experiment-review — the experiment-readout function

Read an A/B test cleanly: state the result, separate the layers of uncertainty,
and recommend a call without overclaiming. Honesty about signal beats a tidy story.

## Intake

Ask for whatever is not supplied — do not guess:

- **Experiment name / identifier** — the test in scope.
- **Metric definitions** — primary and secondary metrics, defined precisely.
- **Variant description** — control vs treatment(s), and the change under test.
- **Date range** — start/end and whether the test reached its planned duration.
- **Segmentation needs** — any segments to break results down by.
- **Known instrumentation issues** — logging gaps, SRM, redirects, double-counts.
- **Depth wanted** — a quick verdict or a full readout.

**If any required input (identifier, metric definitions, variants, date range) is
missing, ask for it first and do not proceed.**

## Steps

1. Restate the hypothesis and the pre-registered primary metric, so the verdict
   is judged against the original bet, not a metric found after the fact.
2. Report the primary result with effect size and uncertainty (CI / p / interval),
   not just "won/lost".
3. Check supporting and guardrail metrics for contradictions or hidden harm.
4. Break out requested segments — but treat segment wins as hypotheses, not proof.
5. Triage uncertainty in three distinct layers (see output): data quality,
   statistical confidence, and practical/business impact.
6. Recommend ship / iterate / kill / extend, with the reasoning tied to the layers.

## Output format

Use only `<angle-bracket>` placeholders below; do not invent concrete values,
numbers, or names. Keep every section in the exact order shown — do not add,
drop, or reorder them.

```markdown
# Experiment review — <identifier> · <verdict: ship | iterate | kill | extend>

## Experiment summary
- **Hypothesis:** <the bet.> · **Variants:** <control vs treatment.>
- **Window:** <dates> (<reached planned duration? y/n>).

## Primary result
- `<primary metric>`: <effect size> (<CI / p / interval>). <Direction + read.>

## Supporting metrics
- <Secondary / guardrail metric>: <movement + any contradiction or harm.>

## Segment breakdowns
- <Segment>: <result> — *(treat as hypothesis, not confirmation.)*

## Is it actionable?
- <Yes / no / not yet> — <the single reason.>

## Limitations / caveats — three layers
- **Data quality:** <SRM, logging gaps, double-counting, redirects.>
- **Statistical confidence:** <power, sample size, CI width, peeking.>
- **Practical / business impact:** <does the effect size matter commercially?>
- <Novelty effect, sample bias, or seasonality if relevant.>

## Recommendation
- <Ship / iterate / kill / extend> because <reasoning across the three layers>.
```

## Guardrails

- **Do not hide uncertainty** — surface it before the recommendation.
- **Distinguish weak signals from meaningful ones** — flag underpowered results.
- **Always separate the three layers**: data quality, statistical confidence, and
  practical/business impact — a stat-sig result can still be commercially trivial.
- **Call out novelty effects, sample bias, and data-quality issues** explicitly.
- **Avoid overclaiming business impact** — don't extrapolate beyond the test.

## Example

Intake: *Identifier `<exp-checkout-cta>`; primary `<checkout conversion>`;
treatment `<one-click pay>`; range `<dates>`; known issue `<SRM suspected>`.*

A verdict of "iterate" then separates: data quality (`<SRM means arms may be
imbalanced — re-randomise>`), statistical confidence (`<CI crosses zero — under-
powered>`), and business impact (`<even at the point estimate the lift is below
the launch threshold>`).
