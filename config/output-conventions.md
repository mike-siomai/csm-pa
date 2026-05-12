# Output Conventions

## Purpose

Keep CSM HQ outputs easy to audit, review, and reuse across daily, weekly, monthly, quarterly, and performance workflows.

## Daily Report Paths

Daily report generation is complete only when both the source draft and standalone dashboard exist.

| Artifact | Path |
|---|---|
| Daily source draft | `outputs/daily/YYYY-MM-DD/daily-report.md` |
| Daily final dashboard | `outputs/daily/YYYY-MM-DD/daily-report-dashboard.html` |

## Required Daily Report Sections

Daily reports must use an employee-first layout. The first manager-facing pages should be the per-employee review sections, not a broad operations summary.

1. Report Header
2. Employee Sections
3. Team-Level Manager Actions
4. Coverage and Source Audit
5. Assumptions and Missing Data
6. Review Gate
7. Optional Cliq-Ready Summary

## Employee Section Format

Create one section per assigned employee, in schedule order. Use this structure:

```markdown
## N) Lastname, Firstname Middlename

### Active Work Summary

| Task | Description | Status | Duration Open |
|---|---|---|---|

### Blockers

| Issue | Status | Notes |
|---|---|---|

### Performance Signals

| Dimension | Rating | Key Observations |
|---|---|---|
| Delivery Visibility | High / Moderate / Low | ... |
| Ownership | Strong / Adequate / Concerning / Unclear | ... |
| Execution Rhythm | Efficient / Steady / Slow / Unclear | ... |
| Blocker Management | Proactive / Reactive / Unclear | ... |
| Communication | Clear / Moderate / Needs Improvement / Unclear | ... |

### Client Perception

Short paragraph. Phrase as likely perception only when supported by evidence.

### Risk Assessment

**Risk Level: Green / Yellow / Red**

Short paragraph explaining the risk level.

### Strengths

1. ...
2. ...
3. ...

### Improvement Opportunities

1. ...
2. ...
3. ...

### Manager Actions (CSM)

1. ...
2. ...
3. ...

### Executive Summary

Short manager-ready paragraph.
```

For missing reports, still render the employee section. Use `Unclear` or `Not enough evidence` for unsupported judgments and add a manager action to follow up on the missing report.

## Source Audit Rules

Every daily report must include a coverage table with one row per assigned employee.

Required columns:

| Column | Requirement |
|---|---|
| Employee | Name from `config/schedule.md` or the generated run packet. |
| Source email status | Found, not found, duplicate, late, malformed, or unclear. |
| Source reference | Gmail message ID, sender/date/subject, or `not found`. |
| Report quality | Complete, partial, malformed, duplicate, or missing. |
| Confidence | High, medium, or low. |
| Notes | Missing data, assumptions, or review flags. |

## Team-Level Manager Action Format

Manager actions should use this format:

| Owner | Action | Urgency | Reason | Source |
|---|---|---|---|---|

Urgency values:
- High: same day follow-up needed.
- Medium: follow up within 2 business days.
- Low: monitor or include in next check-in.

## Review Status

Every report should end with one of these statuses:

- Draft for Mike review
- Ready for internal sharing
- Needs source validation
- Blocked by missing data

Daily reports produced from Gmail should default to `Draft for Mike review`.

## Daily HTML Dashboard Rules

The final daily report artifact should be a standalone HTML dashboard. It must open directly in a browser without requiring a local server.

The dashboard should include:

1. Search across employees, clients/teams, tickets, tasks, blockers, risks, and manager actions.
2. Filters for client/team, risk level, and practical focus areas such as missing reports, blockers, QA/testing, and release work.
3. Easy navigation by overview, client/team, employee, manager actions, and source audit.
4. Employee cards or sections with expandable detail.
5. An individual `Blockers` table inside every employee card/section, with issue, status, and notes. If no blockers are supported by the source data, show `None reported` or `Not enough evidence`.
6. A `Client Perception` section inside every employee card/section. Use evidence-based phrasing only; if unsupported, show `Not enough evidence`.
7. Team-level manager actions and coverage/source notes.

Markdown drafts should be kept as editable source files for auditability.

Before closing a daily report run, verify that the HTML dashboard exists and includes the expected employee sections/cards, individual blockers, client perception, manager actions, source audit, search control, and filters.

Do not create daily PDF or PowerPoint artifacts by default. Create `daily-report.pdf`, `daily-report.pptx`, or a deck builder only when Mike explicitly requests that format for a specific run.

## Monthly Checkpoint Paths

Monthly checkpoint generation is complete only when both standard deliverables exist in Markdown and standalone HTML.

Save monthly checkpoint outputs under:
`outputs/monthly/YYYY-MM/checkpoints/`

| Artifact | Path |
|---|---|
| Cliq-ready verbatim report source | `outputs/monthly/YYYY-MM/checkpoints/CLIENT-SLUG-monthly-checkpoint-report.md` |
| Cliq-ready verbatim report HTML | `outputs/monthly/YYYY-MM/checkpoints/CLIENT-SLUG-monthly-checkpoint-report.html` |
| Internal analysis source | `outputs/monthly/YYYY-MM/checkpoints/CLIENT-SLUG-monthly-checkpoint-analysis.md` |
| Internal analysis HTML | `outputs/monthly/YYYY-MM/checkpoints/CLIENT-SLUG-monthly-checkpoint-analysis.html` |

## Required Monthly Checkpoint Report Sections

The Monthly Checkpoint Report is the Cliq-ready version. It should be concise, factual, and easy to post internally.

1. Report Header
2. Source Coverage
3. Company Situation / Account Context with citations
4. Employee Feedback, one section per employee
5. Verbatim Client Feedback with citations
6. Short Employee Summary
7. Recommended Action
8. Action Items
9. Validation Notes
10. Review Gate

Every verbatim client feedback item must include a citation such as transcript timestamp, email subject/date, or source document reference. Do not attribute comments from Mike as client feedback unless explicitly requested.

## Required Monthly Checkpoint Analysis Sections

The Monthly Checkpoint Analysis is the internal manager-facing analysis.

1. Executive Summary
2. Source Coverage and Confidence
3. Employee Feedback Tables
4. Team Health
5. Client Sentiment
6. Growth Opportunities
7. Risks
8. Recommended Manager Actions
9. Human Validation Needed
10. Review Gate

Monthly checkpoint analysis must separate direct evidence, cleaned summary, interpretation, assumptions, and missing data.

## Monthly Checkpoint HTML Rules

Monthly checkpoint HTML files must be standalone files that open directly in a browser without a local server.

Each HTML file should include:

1. Clear title and date/client header.
2. Navigation links to major sections.
3. Search or quick-scan structure where useful for longer reports.
4. Tables preserved from the Markdown source.
5. Citations visibly attached to verbatim feedback and company/account context notes.
6. A visible review status or review gate.

Before closing a monthly checkpoint run, verify that all four files exist and that the HTML files contain the expected employee sections, cited feedback, account context, action items, and review gate.
