# Monthly Checkpoint Standalone HTML Rules

Create standalone HTML files for both standard Monthly Checkpoint deliverables:

1. Monthly Checkpoint Report
2. Monthly Checkpoint Analysis

## Requirements

- The HTML must open directly in a browser without a local server.
- Use embedded CSS only.
- Do not depend on external fonts, scripts, images, or stylesheets.
- Preserve the Markdown sections and tables in a readable manager-facing layout.
- Include a clear review status.
- Include source coverage and confidence.
- Include citations visibly next to verbatim feedback and account/company situation notes.
- Include easy navigation to major sections.
- For longer reports, include a simple search/filter control when practical.

## Suggested Layout

- Header with client, month, status, and source coverage.
- Navigation bar with section anchors.
- Main content constrained to a readable width.
- Employee sections as separate blocks.
- Tables with visible headers and enough spacing for scanning.
- Validation and review gate sections near the end.

## Verification

Before closing the run, verify that:

- `CLIENT-SLUG-monthly-checkpoint-report.md` exists.
- `CLIENT-SLUG-monthly-checkpoint-report.html` exists.
- `CLIENT-SLUG-monthly-checkpoint-analysis.md` exists.
- `CLIENT-SLUG-monthly-checkpoint-analysis.html` exists.
- The report HTML contains verbatim client feedback per employee.
- The report HTML contains cited company/account situation notes.
- The analysis HTML contains team health, client sentiment, risks, and recommended actions.
