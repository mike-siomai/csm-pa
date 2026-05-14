# Quarterly Performance Review Workflow

## Trigger

Use this workflow when Mike asks for:

- Quarterly performance reviews
- Employee competency ratings
- Performance review drafts
- Top highlights/lowlights per employee
- Growth opportunities or manager summaries

Preferred skill:
`skills/quarterly-performance-review/`

## Scope Routing

Determine employee scope from Mike's request:

| Request Type | Routing |
|---|---|
| Single employee | Generate one employee review. |
| Client/account | Generate one review per employee mapped to that client. |
| Team | Generate one review per employee in that team. |
| Quarter/all employees | Generate one review per employee in scope, grouped by client when possible. |

If scope is unclear, ask Mike before producing formal review drafts.

## Evidence Collection

Use the best available evidence for each employee:

1. Daily reports for the covered period.
2. Monthly checkpoint report and analysis files for the relevant client/months.
3. Compliance, timelog, attendance, punctuality, connectivity, or manager notes when supplied.
4. Client observations when available.

Daily reports are the primary operating evidence. Monthly checkpoints are the primary client/context evidence.

## Review Generation

For each employee, generate:

- Evidence Coverage
- Recommended rating per competency
- Top 3 Highlights
- Top 3 Lowlights
- Growth Opportunities
- Manager Summary
- Evidence vs. Interpretation
- Missing Data / Validation Needed
- Review Gate

Ratings must use only:

- Needs Improvement
- Meets Expectation
- Exceeds Expectation

## Output Location

Save outputs under:
`outputs/quarterly/YYYY-Q#/performance-reviews/`

Default files:

- `EMPLOYEE-SLUG-performance-review.md`
- `EMPLOYEE-SLUG-performance-review.html`
- `performance-review-index.md` when more than one employee is reviewed
- `performance-review-index.html` when more than one employee is reviewed
- `performance-review-deck.pptx` only when Mike requests a final manager-facing deck

The HTML files must be standalone browser-ready review artifacts with navigation, readable tables, confidence labels, evidence separation, missing-data notes, and the review gate.

## Approval Gate

All performance reviews remain drafts until Mike approves final ratings.

Required closing status:

`Status: Draft for Mike review. Ratings require Mike approval before final use.`
