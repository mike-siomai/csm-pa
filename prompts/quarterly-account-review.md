# Quarterly Account Review Prompt

Analyze the requested quarter for the requested client/account set.

Use:
- Daily Reports
- Monthly Checkpoints
- Client Feedback emails
- External websites for open job requisitions for positions related to software development

## Required output format

Produce the QAR as a PowerPoint-style account review, following the `QAR0-Sample.pdf` format:

- one account per slide/page
- compact executive summary, not a long narrative report
- clear Health and Confidence labels near the top
- evidence-first bullets
- growth/resource opportunities tied to actual account signals
- public software-development job requisition scan where available
- source footer listing Gmail and public sources used

## Slide/page structure

Use this exact section order for each account:

```markdown
# Quarterly Account Review

ACCOUNT NAME Health: Green / Green / Watch / Yellow / Red / Recovery / Low Signal
Confidence: High / Medium / Low

## Client Health Evidence
- ...
- ...
- ...

## Growth / Resource Opportunities
- ...
- ...
- ...

## Open Software-Development Job Reqs
- ...
- ...
- ...

Gmail: source summary. Public: public source summary.
```

## Health labels

Use the clearest appropriate label:

- `Green` — positive client feedback, stable delivery, no meaningful risk.
- `Green / Watch` — generally healthy, with one specific watch item.
- `Green / Low Signal` — likely healthy but feedback is thin.
- `Yellow` — active concern that requires follow-up.
- `Red / Recovery` — serious relationship, performance, delivery, or retention risk.
- `Coverage-Limited` — not enough source evidence to judge account health.
- `Onboarding` — account/resource is too new for quarterly performance judgment.

## Confidence labels

- `High` — direct client feedback and/or multiple checkpoint sources.
- `Medium` — useful but partial evidence, such as Gemini notes without direct client-written confirmation.
- `Low` — mostly outbound asks, calendar artifacts, or sparse source coverage.

## Writing rules

- Keep each account slide/page concise.
- Prefer 2-4 bullets per section.
- Do not invent feedback.
- Separate direct evidence from inference.
- If public job reqs are not reliable or company identity is ambiguous, say so directly.
- Do not include long source analysis in the main slide/page.
- If there are many accounts, produce one slide/page per account rather than a portfolio narrative first.
- Use an appendix/source-audit slide only if needed.

## Required content checks

1. Overall account health
2. Team performance trend
3. Delivery quality
4. Risks
5. Staffing recommendations
6. Upsell opportunities
7. Client relationship score
8. Action plan next quarter
