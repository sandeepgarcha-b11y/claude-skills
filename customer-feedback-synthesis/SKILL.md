---
name: customer-feedback-synthesis
description: Turn customer feedback from Slack, tickets, notes, or surveys into themes and clear actions. Use when synthesising qualitative feedback into patterns, severity, and next steps.
---

# customer-feedback-synthesis — the voice-of-customer function

Turn scattered feedback into a ranked set of themes with severity and a next
action each. Patterns over anecdotes; signal over the loudest voice.

## Intake

Ask for whatever is not supplied — do not guess:

- **Source types** — e.g. support tickets, Slack threads, sales notes, survey
  comments, app-store reviews. Note the rough volume of each.
- **Date range** — the window of feedback to synthesise.
- **Product area** — the surface or journey in scope, if narrowing.
- **Output wanted** — themes, pain points, verbatim examples, action items, or a mix.
- **Priority questions** — anything specific the reader is trying to learn.

**If any required input (source types, date range, output wanted) is missing, ask
for it first and do not proceed.**

## Steps

1. Cluster feedback into themes by underlying problem, not by surface wording.
2. Quantify each theme's prominence (count / share of sources) so frequency is
   evidence, not impression.
3. Weight by severity and reach, not volume alone — a rare data-loss bug outranks
   a common cosmetic gripe.
4. Pull one or two representative verbatims per theme; redact names and sensitive
   detail.
5. Separate **pattern** (recurring across independent sources) from **anecdote**
   (a single, possibly loud, voice) and label likely signal vs noise.
6. Convert each theme into the clearest product or ops action.

## Output format

Use only `<angle-bracket>` placeholders below; do not invent concrete values,
counts, quotes, or names. Keep every section in the exact order shown — do not
add, drop, or reorder them.

```markdown
# Feedback synthesis — <product area> · <date range>

## Top themes
1. **<Theme>** — <one-line description of the underlying problem.>
2. **<Theme>** — <…>

## Frequency / prominence
- <Theme>: <count / share> across <which sources>. *(pattern | anecdote)*

## Representative examples
- <Theme>: "<redacted verbatim>" — `<source type>`.

## Severity / impact
- <Theme>: <severity> — affects <reach / who> · <business/ops consequence>.

## Suggested next action
- <Theme>: <the clearest product or ops action + likely owner.>

## Signal vs noise
- Likely signal: <themes backed by independent, repeated sources.>
- Likely noise: <one-off or low-reach items to watch, not act on yet.>
```

## Guardrails

- **Do not overfit to one loud comment** — volume of voice ≠ severity.
- **Separate anecdote from pattern** and label each theme accordingly.
- **Keep sensitive customer details minimal** — redact names, IDs, and PII.
- **Prioritise clear product or ops actions** over restating complaints.
- When a theme rests on thin or single-source evidence, say so plainly.

## Example

Intake: *Sources `<tickets + #channel + survey>`; range `<dates>`; area
`<post-purchase>`; output themes + actions; priority question
`<why are refunds rising?>`.*

A theme entry: `**<Slow refund confirmation>** — users unsure a refund was
accepted.` Frequency `<n>` across tickets and survey *(pattern)*; severity high
(`<drives repeat contacts>`); action `<send an immediate refund-received
confirmation>`; owner `<support ops>`.
