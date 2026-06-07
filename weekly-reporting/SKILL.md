---
name: weekly-reporting
description: Turn Jira and Slack context into a concise, decision-led weekly product update. Use when writing a weekly status report, exec update, or team digest from issue trackers and chat.
---

# weekly-reporting — the status-digest function

Turn raw Jira and Slack signal into a short weekly update that a busy reader can
scan in under a minute and act on. Decisions first, narrative never.

## Intake

Ask for whatever is not supplied — do not guess:

- **Jira scope** — project key(s) or saved filter(s) / JQL to read.
- **Slack scope** — the channel(s) to scan for context and decisions.
- **Reporting period** — start and end dates (default: the last 7 days, but confirm).
- **Audience** — who reads this (e.g. exec, cross-functional team, direct squad).
- **Tone** — e.g. terse exec, neutral team, detailed working-log.
- **KPI names** — any specific metrics the audience expects to see called out.

**If any required input (Jira scope, Slack scope, period, audience) is missing,
ask for it first and do not proceed.**

## Steps

1. Pull issues in scope for the period; bucket by status (done / in progress /
   blocked) and by what actually changed *this* period, not just current state.
2. Scan the Slack channels for decisions, blockers, and risk signals that aren't
   captured in Jira. Note who/what is the source.
3. Reconcile the two sources. Where Jira and Slack disagree (e.g. a ticket marked
   done but discussed as broken), **flag the conflict** rather than picking one.
4. Separate **facts** (status, dates, merged PRs, stated decisions) from
   **inference** (your read on risk or likely slippage). Label inference.
5. Map each KPI the audience asked for to a source. If a KPI has no source this
   period, say "no data" — do not estimate it.
6. Write the report to the audience and tone, keeping every bullet decision-led.

## Output format

Use only `<angle-bracket>` placeholders below; do not invent concrete values,
numbers, names, or progress. Keep every section in the exact order shown — do
not add, drop, or reorder them.

```markdown
# Weekly update — <period> · <audience>

**Summary:** <2–3 sentences: the one thing that matters, plus headline KPI moves.>

## Shipped this week
- <What shipped + impact/KPI link.> · `<source>`

## In progress
- <Workstream> — <state + % or stage>; on track / at risk. · `<source>`

## Blockers / risks
- <Blocker> — <impact + who/what is needed to clear it>. *(fact | inference)*
- ⚠️ Conflicting sources: <Jira says X, Slack says Y — needs reconciliation.>

## Decisions needed
- <Decision> — <options + the owner who must call it + by when.>

## Next week plan
- <Top 3–5 intended outcomes, not a task dump.>
```

## Guardrails

- **Do not invent progress.** No source, no claim.
- **Label fact vs inference** explicitly; never present a guess as status.
- **Flag conflicting source information** instead of silently resolving it.
- Keep it **concise and decision-led** — cut anything the audience can't act on.
- KPIs with no data this period are reported as "no data", never estimated.

## Example

Intake: *Jira `<KEY>` + filter `<JQL>`; Slack `<#channel>`; period `<dates>`;
audience exec; tone terse; KPIs `<activation rate>`, `<checkout conversion>`.*

A "Blockers / risks" bullet then reads:
`<Payment provider sandbox flaky> — <blocks checkout test sign-off>; needs
`<infra owner>` decision on fallback. *(fact — per `<#channel>` <date>)*`
