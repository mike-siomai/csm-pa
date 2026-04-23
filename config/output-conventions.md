# Output Conventions

## Purpose

Keep CSM HQ outputs easy to audit, review, and reuse across daily, weekly, monthly, quarterly, and performance workflows.

## Daily Report Paths

| Artifact | Path |
|---|---|
| Daily source draft | `outputs/daily/YYYY-MM-DD/daily-report.md` |
| Daily final report | `outputs/daily/YYYY-MM-DD/daily-report.pdf` |

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

## Export Rules

The final daily report artifact should be a PDF when a manager-facing copy is needed.

Markdown drafts should be kept as editable source files for auditability. Export manually or through an explicitly requested Codex action; there is no scheduled-job requirement.
