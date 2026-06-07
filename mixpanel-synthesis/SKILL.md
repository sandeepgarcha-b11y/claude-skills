---
name: mixpanel-synthesis
description: Analyse Mixpanel data and turn it into product insight, not a metric dump. Use when interpreting funnels, cohorts, or events to answer a product question or support a hypothesis.
---

# mixpanel-synthesis — the analytics-interpretation function

Convert Mixpanel numbers into a clear product read: what changed, why it matters,
and how confident we can be. Interpretation over raw metrics.

## Intake

Ask for whatever is not supplied — do not guess:

- **The question** — the actual product decision this analysis serves.
- **Date range** — and any comparison window (e.g. week-on-week, pre/post launch).
- **Events / funnel steps** — the specific event names or funnel stages in scope.
- **Event definitions** — what each event *actually* fires on. **If definitions
  are not supplied, ask for them; do not assume the taxonomy.**
- **Segments to compare** — e.g. platform, plan, cohort, geography, new vs returning.
- **Business metric** — the outcome this ladders up to (conversion, retention, etc.).
- **Readout type** — summary, funnel readout, cohort readout, or hypothesis support.

**If any required input (question, date range, events, readout type) is missing,
ask for it first and do not proceed.**

## Steps

1. Confirm event definitions and instrumentation before reading any number. If a
   definition is ambiguous, surface it as a caveat rather than guessing intent.
2. Establish the baseline and the comparison window so "what changed" is grounded.
3. Compute the requested readout (funnel drop-off, cohort retention, segment split).
4. Translate each movement into product terms — what user behaviour it implies —
   not just the percentage.
5. Pressure-test causality: list confounders (seasonality, releases, traffic mix)
   before attributing any change to a cause.
6. Note sample size and confidence; flag anything underpowered or noisy.

## Output format

Use only `<angle-bracket>` placeholders below; do not invent concrete values,
numbers, names, or event definitions. Keep every section in the exact order
shown — do not add, drop, or reorder them.

```markdown
# Mixpanel readout — <question> · <date range>

**Core finding:** <one sentence: the product-relevant answer to the question.>

## What changed
- <Metric / step> moved from `<baseline>` to `<current>` over `<window>`.
- <Largest segment difference, if any.>

## Why it matters
- <What this implies about user behaviour and the business metric.>

## Sample size / confidence
- n = `<size>` per arm/segment. Confidence: <high | medium | low> — <why>.
- Instrumentation caveats: <ambiguous/assumed event definitions, if any.>

## What to check next
- <The follow-up cut or validation that would firm this up.>

## Recommendation / next analytical step
- <The product action or the next analysis — not a metric restatement.>
```

## Guardrails

- **Do not assume event definitions** — confirm them or flag the assumption.
- **Do not overstate causality** — correlation is not a cause; list confounders.
- **Always call out instrumentation ambiguity** that could change the read.
- **Favour product interpretation over raw metric dumping** — every number earns
  its place by changing the answer.
- When the sample is thin or the signal is weak, say so plainly.

## Example

Intake: *Question "is `<checkout step 2>` leaking?"; range `<dates>`; funnel
`<step 1 → step 5>`; segment by platform; metric checkout conversion.*

Core finding might read: `<Step 2 → 3 drop-off is the single largest leak,
concentrated on `<platform>`; behaviour suggests a form/validation issue rather
than intent loss.>` — with a caveat that `<step 2>`'s definition was assumed.
