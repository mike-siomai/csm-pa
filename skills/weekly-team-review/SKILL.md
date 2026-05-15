---
name: weekly-team-review
description: Build CSM HQ weekly team review dashboards from aggregated daily reports, optional client notes, and optional manager notes. Use when Mike asks for a weekly report, weekly team review, weekly health summary, team/client weekly risk scan, repeated blocker analysis, or manager-ready weekly operating review.
---

# Weekly Team Review

## Core Rule

Use this skill for weekly team review generation. Read `AGENTS.md`, `config/action-policy.md`, `config/output-conventions.md`, and `prompts/weekly-review.md` before analysis. Keep outputs evidence-first and draft-only until Mike reviews sensitive follow-up language.

## Inputs

Use available evidence from:

- Aggregated daily reports for the week
- Daily report Markdown and HTML outputs under `outputs/daily/`
- Gmail daily report evidence when Mike asks for collection
- Optional client notes
- Optional manager notes
- Relevant roster or schedule references when needed for missing-report interpretation

If source coverage is unclear, state what was available and what is missing.

## Analysis Steps

1. Resolve the weekly reporting window. If Mike does not specify dates, use the past 7 calendar days ending on the requested run date.
2. Collect daily report evidence for the covered period.
3. Group findings by client/team first, then employee.
4. Summarize each client/team for productivity trend, repeated blockers, delivery risks, capacity pressure, low visibility/compliance watch, strong performer signals, and recommended manager actions.
5. Summarize each employee for active workstreams, delivery rhythm, blocker pattern, communication visibility, risk level, and recommended CSM action.
6. Identify portfolio-level repeated blockers, underperformance signals, burnout/overutilization signals, missing-report patterns, and team health.
7. Separate direct evidence, interpreted insight, assumptions, and missing data.
8. Keep confidence visible when source coverage is partial, inconsistent, or low.

## Output

Save editable source under:
`outputs/weekly/YYYY-MM-DD_YYYY-MM-DD/weekly-team-review.md`

Save the manager-facing standalone HTML dashboard under:
`outputs/weekly/YYYY-MM-DD_YYYY-MM-DD/weekly-team-review.html`

Weekly team reviews are an exception to PowerPoint-first delivery. Do not create PDF or PowerPoint outputs unless Mike explicitly requests that format for the run.

Required section order:

1. Report Header
2. Executive Summary
3. Weekly Team Health Score
4. Client / Team Review
5. Employee Summaries
6. Repeated Blockers / Delivery Risks
7. Low Visibility / Compliance Watch
8. Recommended Manager Actions
9. Source Coverage and Audit
10. Assumptions and Missing Data
11. Review Gate

Default review status: `Draft for Mike review`.

## HTML Dashboard Requirements

The standalone HTML dashboard must include:

- search across clients/teams, employees, tasks, blockers, risks, and manager actions,
- filters for client/team, health score, risk level, repeated blockers, low visibility, missing reports, and focus areas,
- easy navigation by overview, client/team, employee, blockers/risks, manager actions, and source audit,
- client/team sections with health score, productivity trend, repeated blockers, strong performer signals, low visibility or compliance watch, and recommended manager actions,
- employee summaries with active workstreams, delivery rhythm, blocker pattern, communication visibility, risk level, and recommended CSM action,
- source coverage and audit notes.

Use `references/weekly-team-review-template.md` when a structured source template is needed.

## Review Gates

Require Mike review before:

- Sending client-facing follow-up
- Sending employee-facing coaching or compliance messages
- Using weekly findings in a formal performance review
- Escalating sensitive account or employee concerns outside the workspace

## Required Checks

- Verify that both `weekly-team-review.md` and `weekly-team-review.html` exist before closing the run.
- Verify that the HTML opens as a standalone file and contains the expected sections, search, filters, source audit, and review gate.
- Keep unsupported fields as `Unclear` or `Not enough evidence`.
- Do not invent feedback, blockers, risks, sentiment, or employee intent.

## Resources

- `references/weekly-team-review-template.md`: canonical weekly source structure.
