# Output Conventions

## Purpose

Keep CSM HQ outputs easy to audit, review, and reuse across daily, weekly, monthly, quarterly, and performance workflows.

## Daily Report Paths

Daily report generation is complete only when both the source draft and standalone dashboard exist.

| Artifact | Path |
|---|---|
| Daily source draft | `outputs/daily/YYYY-MM-DD/daily-report.md` |
| Daily final dashboard | `outputs/daily/YYYY-MM-DD/daily-report-dashboard.html` |

## Weekly Team Review Paths

Weekly team review generation is complete only when both the source draft and standalone dashboard exist.

| Artifact | Path |
|---|---|
| Weekly source draft | `outputs/weekly/YYYY-MM-DD_YYYY-MM-DD/weekly-team-review.md` |
| Weekly final dashboard | `outputs/weekly/YYYY-MM-DD_YYYY-MM-DD/weekly-team-review.html` |

## Required Weekly Team Review Sections

Weekly team reviews should be organized by client/team first, then employee within each client/team.

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

## Weekly HTML Dashboard Rules

The final weekly team review artifact should be a standalone HTML dashboard. It must open directly in a browser without requiring a local server.

The dashboard should include:

1. Search across clients/teams, employees, tasks, blockers, risks, and manager actions.
2. Filters for client/team, health score, risk level, repeated blockers, low visibility, missing reports, and focus areas.
3. Easy navigation by overview, client/team, employee, blockers/risks, manager actions, and source audit.
4. Client/team sections with health score, productivity trend, repeated blockers, strong performer signals, low visibility or compliance watch, and recommended manager actions.
5. Employee summaries covering active workstreams, delivery rhythm, blocker pattern, communication visibility, risk level, and recommended CSM action.
6. A source coverage and audit section showing evidence sources, gaps, fallback usage, and confidence notes.

Markdown drafts should be kept as editable source files for auditability.

Before closing a weekly team review run, verify that the HTML dashboard exists and includes the expected client/team sections, employee summaries, health score, repeated blockers, low-visibility/compliance watch, manager actions, source audit, search control, and filters.

Do not create weekly PDF or PowerPoint artifacts by default. Create `weekly-team-review.pdf`, `weekly-team-review.pptx`, or a deck builder only when Mike explicitly requests that format for a specific run.

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

Short paragraph from a client/customer or Senior Sales lens. Phrase as likely inferred perception based on daily-report evidence, not direct feedback, unless direct feedback exists. Include confidence when useful.

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
6. A `Client Perception` section inside every employee card/section. Use an evidence-based client/customer or Senior Sales lens based on daily reports. Do not present inferred perception as direct client feedback. If unsupported by the source data, show `Not enough evidence`.
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

## Quarterly Performance Review Paths

Quarterly performance review generation is complete when each employee in scope has a draft Markdown review and matching standalone HTML review. When Mike requests a final manager-facing package, create a PowerPoint deck after the Markdown and HTML drafts are reviewed.

Save quarterly performance review outputs under:
`outputs/quarterly/YYYY-Q#/performance-reviews/`

| Artifact | Path |
|---|---|
| Per-employee review draft | `outputs/quarterly/YYYY-Q#/performance-reviews/EMPLOYEE-SLUG-performance-review.md` |
| Per-employee standalone review | `outputs/quarterly/YYYY-Q#/performance-reviews/EMPLOYEE-SLUG-performance-review.html` |
| Combined review index | `outputs/quarterly/YYYY-Q#/performance-reviews/performance-review-index.md` |
| Combined standalone review index | `outputs/quarterly/YYYY-Q#/performance-reviews/performance-review-index.html` |
| Final manager-facing deck, when requested | `outputs/quarterly/YYYY-Q#/performance-reviews/performance-review-deck.pptx` |

## Required Quarterly Performance Review Sections

Create one review per employee in scope.

1. Employee and review-period header
2. Evidence Coverage
3. Recommended Ratings for all 10 competencies
4. Top 3 Highlights
5. Top 3 Lowlights
6. Growth Opportunities
7. Manager Summary
8. Evidence vs. Interpretation
9. Missing Data / Validation Needed
10. Review Gate

Required competencies:

- Quality of Deliverables
- Efficiency and Speed
- Collaboration and Teamwork
- Problem Solving
- Communication
- Overall Attitude / Response to Feedback
- Reliability / Meeting Deadlines
- Punctuality / Shows Up to Meetings on Time
- Ability to Work Independently
- Connectivity / Bandwidth

Allowed ratings:

- Needs Improvement
- Meets Expectation
- Exceeds Expectation

Every competency rating must include evidence summary, manager rationale, and confidence. Use a developmental but firm manager tone. Do not invent client feedback, punctuality issues, connectivity concerns, attitude concerns, missed deadlines, or root cause.

## Quarterly Performance Review Source Rules

Use daily reports as operating evidence and monthly checkpoints as client/context evidence.

If both are available, consider both before assigning ratings. If either source is missing, proceed only as a lower-confidence draft and flag the missing source clearly.

Performance review ratings are not final until Mike reviews and approves them. End each employee review with:

`Status: Draft for Mike review. Ratings require Mike approval before final use.`

## Quarterly Performance Review HTML Rules

Quarterly performance review HTML files must be standalone files that open directly in a browser without a local server.

Each per-employee HTML file should include:

1. Employee name, client/team, review period, overall confidence, and review status.
2. Navigation links to ratings, highlights, lowlights, growth opportunities, manager summary, evidence, missing data, and review gate.
3. A readable competency rating table with rating, evidence summary, manager rationale, and confidence.
4. Visible confidence labels for ratings and source coverage.
5. Clear separation between direct evidence and interpreted insight.
6. A visible review gate stating that ratings require Mike approval before final use.

When more than one employee is reviewed, create a standalone `performance-review-index.html` that links or navigates to each employee review and summarizes employee, client/team, overall confidence, key rating concerns, and validation needs.

Before closing a quarterly performance review run, verify that each employee has both `.md` and `.html` files, and that the HTML files contain the expected ratings, highlights, lowlights, growth opportunities, manager summary, evidence separation, missing-data section, and review gate.
