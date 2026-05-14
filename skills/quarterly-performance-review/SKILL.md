---
name: quarterly-performance-review
description: Generate CSM HQ quarterly performance review drafts per employee using daily reports, monthly checkpoint feedback, compliance patterns, timelog behavior, manager observations, and client observations. Use when Mike asks for performance reviews, competency ratings, quarterly employee reviews, highlights/lowlights, growth opportunities, or manager summaries.
---

# Quarterly Performance Review

## Core Rule

Use this skill for employee performance review workflows. Read `AGENTS.md`, `config/action-policy.md`, `config/output-conventions.md`, and `prompts/performance-review.md` before drafting reviews.

Performance reviews are evidence-backed drafts. Mike must review and approve final ratings before they are used in employee-facing or HR-facing contexts.

When Mike asks for a review that is "ready to be communicated to the employee," produce an employee-facing draft, not only an internal evidence memo. The language should be direct, fair, developmental, and ready for Mike to send after review. Keep sensitive wording as draft language and preserve the review gate.

## Inputs

Use available evidence from:

- Daily reports for the covered quarter or requested period.
- Monthly checkpoint report and analysis outputs for the employee's client/team.
- Compliance patterns, timelog behavior, attendance notes, and punctuality notes when supplied.
- Manager observations from Mike when supplied.
- Client observations or feedback when available.

Do not assume every source exists. State source coverage and missing data per employee.

## Employee Scope

Run the workflow per employee.

When Mike asks for:

- One employee: produce one employee review.
- One client/account: produce one review per employee mapped to that client.
- One quarter/team/all employees: produce one review per employee in scope, grouped by client when possible.

If an employee has daily reports but no checkpoint feedback, continue with lower confidence and flag missing checkpoint evidence.

If an employee has checkpoint feedback but limited daily-report coverage, continue with lower confidence and flag missing operating evidence.

## Evidence Handling

Daily reports are operating evidence for delivery rhythm, task ownership, blockers, execution, communication clarity, reliability, independence, and burnout/overload signals.

Monthly checkpoints are client/context evidence for quality, communication, collaboration, client sentiment, account context, and repeated strengths or concerns.

Keep these separate:

- Direct evidence
- Interpreted insight
- Assumptions
- Missing data

Do not invent:

- Client feedback
- Attendance or punctuality issues
- Connectivity or bandwidth issues
- Missed deadlines
- Attitude concerns
- Root cause or employee intent

## Ratings

Use only these rating values:

- Needs Improvement
- Meets Expectation
- Exceeds Expectation

Rate every competency:

1. Quality of Deliverables
2. Efficiency and Speed
3. Collaboration and Teamwork
4. Problem Solving
5. Communication
6. Overall Attitude / Response to Feedback
7. Reliability / Meeting Deadlines
8. Punctuality / Shows Up to Meetings on Time
9. Ability to Work Independently
10. Connectivity / Bandwidth

Each rating must include:

- Recommended rating
- Evidence summary
- Manager rationale
- Confidence: High / Medium / Low

When evidence is insufficient, prefer `Meets Expectation` only if there is enough neutral/positive evidence to support it. Otherwise state that the rating is low-confidence and explain what Mike should validate.

## Outputs

Default output folder:
`outputs/quarterly/YYYY-Q#/performance-reviews/`

Create:

- One Markdown source file per employee.
- One standalone HTML review file per employee that opens directly in a browser without a local server.
- A combined manager review index in Markdown when more than one employee is reviewed.
- A combined standalone HTML index when more than one employee is reviewed.
- PowerPoint output only when Mike explicitly requests it or asks for a manager-facing final package.

Use filename slugs:

- `employee-name-performance-review.md`
- `employee-name-performance-review.html`
- `performance-review-index.md`
- `performance-review-index.html`
- `performance-review-deck.pptx` when requested.

Use `references/per-employee-review-template.md` as the canonical employee review structure.

HTML outputs must preserve the same sections as the Markdown source, include clear navigation, readable rating tables, visible confidence labels, and the review gate. Keep HTML self-contained with inline CSS and no external runtime dependency.

## Employee-Ready Draft Mode

Use this mode when Mike asks for wording that is ready to communicate to the employee.

Employee-ready reviews should:

- Address the employee directly by name or with second-person wording.
- Lead with the overall assessment and the practical message the employee needs to hear.
- Include the 10 competency ratings using the allowed values.
- Replace internal labels like `Manager Rationale`, `Interpreted Insight`, and `Missing Data` with employee-appropriate sections such as `Feedback`, `Key Strengths`, `Development Focus`, `Manager Summary`, and `Next-Step Coaching Plan`.
- Keep validation caveats in a short `Mike Review Notes Before Sending` section, not in the main employee message.
- Avoid exposing speculative internal analysis, unsupported concerns, or sensitive source limitations as if they are employee conclusions.
- Do not include direct client feedback unless it is sourced, in-period, and approved for use.
- Preserve a review gate stating that Mike must approve ratings and employee-facing language before final use.

Recommended employee-ready structure:

1. Employee Review header
2. Opening Message
3. Recommended Ratings
4. Key Strengths
5. Development Focus
6. Manager Summary
7. Next-Step Coaching Plan
8. Mike Review Notes Before Sending
9. Review Gate

## Tone

Act as a manager. Use a developmental but firm tone:

- Balanced and executive-ready.
- Specific enough for coaching.
- Diplomatic but direct about concerns.
- No exaggerated praise or unsupported criticism.
- Draft language only for sensitive conclusions.
- For employee-ready drafts, write in clear coaching language that an employee can receive without needing to understand the internal audit process.

## Review Gates

Default status:
`Draft for Mike review`

Require Mike approval before:

- Finalizing ratings.
- Sending employee-facing language.
- Sharing performance conclusions with HR, leadership, or clients.
- Using low-confidence judgments in a formal review.

## Required Checks

- One review per employee in scope.
- Ratings cover all 10 competencies.
- Ratings use only allowed values.
- Daily reports and monthly checkpoints are both considered when available.
- Missing daily report or checkpoint evidence is clearly flagged.
- Direct evidence is separated from interpretation.
- Low-confidence judgments are explicitly marked.
- Final section includes the review gate.
- Each per-employee Markdown draft has a matching standalone HTML file.

## Resources

- `references/per-employee-review-template.md`: canonical employee review format.
