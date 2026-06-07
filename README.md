# claude-skills

A portable, company-agnostic suite of reusable Claude Skills for product
management. Every skill collects its workspace-specific context (Jira keys,
Slack channels, event names, KPIs, date ranges) at runtime — nothing is
hardcoded — so the set drops into any workspace.

## Skills

| Skill | Use when |
|-------|----------|
| [`weekly-reporting`](weekly-reporting/SKILL.md) | Writing a weekly product/exec update from Jira and Slack. |
| [`mixpanel-synthesis`](mixpanel-synthesis/SKILL.md) | Turning Mixpanel funnels, cohorts, or events into product insight. |
| [`hypothesis-generator`](hypothesis-generator/SKILL.md) | Turning a problem statement into ranked, testable hypotheses. |
| [`experiment-review`](experiment-review/SKILL.md) | Reading out an A/B test and recommending ship / iterate / kill. |
| [`customer-feedback-synthesis`](customer-feedback-synthesis/SKILL.md) | Synthesising qualitative feedback into themes and actions. |

Each skill follows the same shape: an `Intake` step that asks for missing
context, a standard `Output format`, and `Guardrails` against vague or
overconfident answers.
