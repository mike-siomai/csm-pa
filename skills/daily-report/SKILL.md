---
name: daily-report
description: Build CSM HQ daily report packets from Gmail daily report emails, the roster/schedule Google Sheet, and the CSV fallback. Use when Mike asks for a daily report, weekday report, employee report coverage, missing-report audit, team/client daily summary, or manager-ready daily status packet.
---

# Daily Report

## Core Rule

Use this skill as the primary workflow for CSM daily report generation. Read `AGENTS.md`, `config/action-policy.md`, `config/output-conventions.md`, and `config/schedule.md` before analysis. Follow the approval rules in `config/action-policy.md`; never send, forward, archive, delete, or label email unless Mike explicitly approves the specific action.

## Routing

1. Resolve the requested date, weekday, client, or team.
2. If Mike gives a weekday, use a 7-day reporting window ending on that weekday. Example: Tuesday means previous Tuesday through current Tuesday.
3. If Mike gives a date, infer the weekday from the date and use that weekday for schedule routing.
4. Use the live Google Sheet roster as the preferred schedule source:
   `https://docs.google.com/spreadsheets/d/11MXqgilR_YHSHxXoLW7fzuLEL76PGjuNs37NaY6MdJk/edit?usp=sharing`
5. If the live sheet is unavailable, use `config/schedule.md` or the schedule snapshot in `AGENTS.md` and explicitly note the fallback.
6. Group the final report by client first, then employee within each client.
7. Put any Gmail report sender not found in the roster under `Unmapped / Needs roster validation`.

## Source Priority

Gmail is the source of truth. Use the CSV fallback only when a scheduled employee is missing usable Gmail evidence for the employee/date window.

Source labels:

- `Gmail`: report found only in Gmail.
- `CSV fallback`: Gmail missing and fallback CSV supplies usable substitute data.
- `both matched`: Gmail and CSV both exist and align; rely on Gmail.
- `missing`: no usable Gmail or fallback evidence.

Fallback CSV:
`data/reports/custom_2026-01-01_2026-04-23.csv`

If Gmail and the roster conflict, use the roster for schedule routing and document the conflict in the audit trail. If fallback data is used, lower confidence as appropriate.

## Analysis Steps

1. Gather Gmail daily report emails for the selected employees and full reporting window.
2. Detect missing, late, duplicate, malformed, or unclear reports.
3. Use fallback CSV only for scheduled employees with missing Gmail evidence.
4. Extract all tasks mentioned in the covered period for each employee, not only currently active tasks.
5. Identify blockers, resolved blockers, performance signals, burnout/overutilization signals, risk flags, and manager actions.
6. Separate direct evidence from interpreted insight, assumptions, and missing data.
7. Include an audit row for every scheduled employee.

## Output

Save editable source under:
`outputs/daily/YYYY-MM-DD/daily-report.md`

Save the manager-facing standalone HTML dashboard under:
`outputs/daily/YYYY-MM-DD/daily-report-dashboard.html`

Daily reports are the standing exception to PowerPoint-first delivery. Do not create PDF or PowerPoint outputs unless Mike explicitly requests that format for the run.

The standalone HTML dashboard must include an employee card or section for every routed employee. Each employee card/section must visibly include:

- all tasks mentioned in the covered source data,
- individual blockers with status and notes,
- client perception, phrased only when supported by evidence,
- performance signals,
- risk assessment,
- strengths,
- improvement opportunities,
- manager actions,
- source coverage/status.

Use `templates/daily-report-template.md` if present. If not present, use `references/report-template.md` in this skill.

Required section order:

1. Report Header
2. Client and Employee Sections
3. Team-Level Manager Actions
4. Coverage and Source Audit
5. Assumptions and Missing Data
6. Review Gate
7. Optional Cliq-Ready Summary

Default review status: `Draft for Mike review`.

## Required Checks

- Include scheduled employees even when no report is found.
- Keep unsupported fields as `Unclear` or `Not enough evidence`.
- In the HTML dashboard, include the employee's individual blockers and client perception inside the employee card/section.
- Preserve source references in the audit rather than crowding employee sections.
- Use concise, manager-ready language.
- Do not invent feedback, task status, blockers, risks, sentiment, or employee intent.

## Resources

- `references/report-template.md`: canonical output structure.
- `references/source-routing.md`: source priority, roster fallback, and audit labeling rules.
- `schemas/source-audit.schema.json`: structured source-audit row schema.
