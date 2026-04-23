# Daily Report Workflow

## Purpose

Produce a manager-ready daily CSM status report for only the employees assigned to the current weekday.

The manager-facing report must use an employee-first format. Each assigned employee gets a self-contained section with task tables, blockers, performance signals, risk assessment, strengths, improvement opportunities, manager actions, and a short executive summary. Source audit details remain required, but they belong after the employee sections so the first pages are immediately useful for review.

## Required Inputs

Read these files before analysis:
- `AGENTS.md`
- `config/action-policy.md`
- `config/output-conventions.md`
- `config/schedule.md`

Use today's local date and `config/schedule.md` as the source of truth for the weekday and assigned employees unless Mike provides a different date or team.

## Gmail Search

Search Gmail using:

```text
label:daily-reports newer_than:2d
```

Only analyze reports for employees assigned to the current weekday. Do not include unassigned employees unless they appear as relevant context for a blocker or risk.

## Required Analysis Per Employee

For every assigned employee, including employees with no found report, provide:

1. Source email status: found, not found, duplicate, late, malformed, or unclear.
2. Source reference: Gmail message ID or sender/date/subject when available; otherwise `not found`.
3. Active tasks, including ticket/task identifier when available.
4. Task descriptions, status, and duration open when available.
5. Blockers.
6. Performance signals.
7. Client perception, only when evidence supports it.
8. Risk level: Green, Yellow, or Red.
9. Strengths.
10. Improvement opportunities.
11. Manager actions.
12. Confidence level: high, medium, or low.

Separate direct evidence from interpreted insight. Do not invent status, blockers, risks, performance concerns, or burnout signals.

## Required Output Sections

Save the final report as a PDF to:

```text
outputs/daily/YYYY-MM-DD/daily-report.pdf
```

If you compose the report as Markdown first, save the editable source to `outputs/daily/YYYY-MM-DD/daily-report.md`. Export to PDF only when Mike asks for a manager-facing copy or when the current workflow explicitly requires it.

Use these sections in this order:

1. Report Header
2. Employee Sections
3. Team-Level Manager Actions
4. Coverage and Source Audit
5. Assumptions and Missing Data
6. Review Gate
7. Optional Cliq-Ready Summary

## Employee Section Format

Create one section per assigned employee, in schedule order. Use this exact structure:

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

For missing reports, still render the employee section. Mark unsupported fields as `Unclear` or `Not enough evidence`, set confidence to low in the source audit, and include a manager action to follow up on the missing report.

## Formatting Rules

- Keep the employee sections concise, direct, and CSM-ready.
- Use tables for structured analysis and numbered lists for strengths, improvement opportunities, and manager actions.
- Avoid overstating evidence. Use `Unclear` or `Not enough evidence` where the report does not support a judgment.
- Preserve source references in the audit section rather than crowding each employee section.

## Coverage and Source Audit

Include one row per assigned employee.

| Employee | Source email status | Source reference | Report quality | Confidence | Notes |
|---|---|---|---|---|---|

Use `not found` when no matching report is found.

## Team-Level Manager Actions

Use this format:

| Owner | Action | Urgency | Reason | Source |
|---|---|---|---|---|

Urgency values:
- High: same day follow-up needed.
- Medium: follow up within 2 business days.
- Low: monitor or include in next check-in.

## Review Gate

End with a review status:
- Draft for Mike review
- Ready for internal sharing
- Needs source validation
- Blocked by missing data

Default to `Draft for Mike review`.

Do not send, delete, archive, forward, or label emails unless Mike explicitly approves the specific action.
