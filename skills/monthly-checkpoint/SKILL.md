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

Ask or infer from the request whether Mike needs:

- Internal summary: may include risks, coaching flags, confidence notes, and manager actions.
- Client-ready summary: polished, diplomatic, and excludes sensitive internal interpretation unless approved.
- Evidence packet: source-heavy version for audit and review.

Use `references/internal-summary-template.md` and `references/client-ready-template.md` as needed.

Save outputs under:
`outputs/monthly/YYYY-MM/checkpoints/`

PowerPoint is preferred for manager-facing delivery when a final artifact is requested. Keep Markdown as editable/audit source when useful.

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

## Resources

- `references/internal-summary-template.md`: internal checkpoint output.
- `references/client-ready-template.md`: client-facing summary draft.
- `schemas/feedback-item.schema.json`: structured feedback extraction schema.
