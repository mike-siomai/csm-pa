---
name: monthly-checkpoint
description: Extract, clean, categorize, and package CSM HQ monthly checkpoint feedback from client emails, Gemini meeting notes, transcripts, and informal written feedback. Use when Mike asks for monthly checkpoint summaries, client feedback by employee, team health, client sentiment, coaching flags, checkpoint-ready outputs, or client-ready/internal checkpoint versions.
---

# Monthly Checkpoint

## Core Rule

Use this skill for monthly checkpoint analysis and client feedback extraction. Read `AGENTS.md`, `config/action-policy.md`, and `prompts/monthly-checkpoint.md` before analysis. Preserve meaning, avoid invention, and keep sensitive outputs in draft form for Mike review.

## Inputs

Use available evidence from:

- Client feedback email replies
- Gemini meeting notes
- Gemini transcripts
- Informal written feedback supplied by Mike
- Relevant daily report context when Mike asks for it

If source coverage is unclear, state what was available and what is missing.

## Extraction Rules

1. Extract client feedback per employee.
2. Exclude comments made by Mike, Michael, or the CSM unless Mike explicitly asks to include manager observations.
3. Preserve verbatim client feedback where possible.
4. Remove filler words only when preparing cleaned summaries; do not change meaning.
5. If speaker identity, employee name, or client reference is unclear, flag for human validation.
6. Do not invent feedback or assign vague comments to an employee without evidence.

## Categories

Categorize feedback into:

- Performance
- Quality
- Communication
- Reliability

Also identify:

- Team health
- Client sentiment
- Account growth opportunities
- Churn or relationship risks
- Employees needing coaching
- Employee health concerns

## Output Modes

When Mike asks to generate a Monthly Checkpoint, default to producing two paired outputs:

1. Monthly Checkpoint Report
   - Client feedback captured verbatim per employee.
   - Ready for internal Cliq posting.
   - Include citations for each verbatim feedback item, using transcript timestamps, email dates/message subjects, or document references.
   - Include a company situation / account context section with citations.
   - Keep sensitive wording factual and reviewable.
2. Monthly Checkpoint Analysis
   - Internal manager analysis with categorized feedback, team health, client sentiment, risks, growth opportunities, coaching flags, and recommended actions.
   - Separate direct evidence, cleaned summary, interpretation, assumptions, and missing data.

For each of the two outputs, create both:

- Markdown source file.
- Standalone HTML file that opens directly in a browser without a local server.

Save outputs under:
`outputs/monthly/YYYY-MM/checkpoints/`

Default filenames:

- `CLIENT-SLUG-monthly-checkpoint-report.md`
- `CLIENT-SLUG-monthly-checkpoint-report.html`
- `CLIENT-SLUG-monthly-checkpoint-analysis.md`
- `CLIENT-SLUG-monthly-checkpoint-analysis.html`

Use `references/cliq-report-template.md`, `references/internal-summary-template.md`, and `references/html-output-rules.md` as needed.

PowerPoint is not the default for monthly checkpoint runs unless Mike explicitly requests it for that run. Markdown and standalone HTML are the standard deliverables.

## Review Gates

Default to `Draft for Mike review`.

Require Mike review before:

- Sending client-ready text
- Sending employee-facing feedback
- Finalizing sensitive coaching language
- Using ambiguous transcript feedback in performance records

## Required Checks

- Separate verbatim evidence, cleaned summary, interpretation, and missing data.
- Keep confidence visible for each employee or feedback item.
- Preserve names exactly as source evidence supports them.
- Flag unclear attribution instead of guessing.
- Verify that both Monthly Checkpoint Report and Monthly Checkpoint Analysis exist as Markdown and standalone HTML before closing the run.
- The Cliq-ready report must include verbatim client feedback per employee and cited company/account situation notes.

## Resources

- `references/internal-summary-template.md`: internal checkpoint output.
- `references/client-ready-template.md`: client-facing summary draft.
- `references/cliq-report-template.md`: Cliq-ready verbatim feedback report.
- `references/html-output-rules.md`: standalone HTML output requirements.
- `schemas/feedback-item.schema.json`: structured feedback extraction schema.
