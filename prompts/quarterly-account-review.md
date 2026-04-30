# Quarterly Account Review Prompt

Analyze the requested quarter for the requested client/account set.

The target audience is Sales and the COO. Prioritize the information these roles can act on:

- Sales: account sentiment, relationship health, expansion or upsell signals, open software-development roles, staffing gaps, renewal risk, and recommended commercial follow-up.
- COO: delivery quality, staffing health, compliance patterns, performance risks, operational blockers, escalation needs, and leadership support required.
- Treat Sales and COO as the intended readers, not as visible report categories. Do not write bullets labeled `Sales:` or `COO:` unless Sales is explicitly the action owner in the `Action Items` section.

Use:
- Daily Reports
- Monthly Checkpoints
- Client Feedback emails
- External websites for open job requisitions for positions related to software development

## Assumption handling

- Clarify with Mike before proceeding if the quarter, account list, audience, source coverage, output format, or theme/template file is unclear.
- Do not silently assume client identity when using public job requisition sources.
- If a source is unavailable, say so in the output and lower confidence as appropriate.

## Required output format

Produce the QAR as a PowerPoint-style account review for Sales and COO updates, using the Google Drive `QAR Theme` deck as the required theme/template source:

- `https://docs.google.com/presentation/d/1ETHEwUDG42jwsuL7ofminmuhxQOpMC2pNEogUp1vGDQ`

Follow the QAR sample structure:

- one account per slide/page
- compact executive summary, not a long narrative report
- clear Health and Confidence labels near the top
- evidence-first bullets
- growth signals limited to external software-development job requisitions and evidence-based resource-role recommendations
- operational risks/support needs written as account implications, not COO-labeled notes
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

## Growth Signal

## Open Software-Development Job Reqs
- Public software-development related role title and source, if reliable.
- If none are found: `No external job requistion found`

## Recommended Resource Opportunity
- Evidence-based software-development role recommendation, if monthly checkpoints or daily reports support one.
- Base recommendations on roadmap demand, burnout/overutilization, lack of required expertise, recurring blockers, QA needs, DevOps/platform gaps, mobile/backend/frontend needs, AI enablement, or automation demand.
- If evidence does not support a recommendation, say no clear resource recommendation found.

## Action Items
- CSM action item.
- Sales action item.

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
- Write for Sales and COO readers, not a general internal audience.
- Make each recommendation action-oriented and role-relevant.
- Do not use Sales and COO as visible audience labels or generic bullet prefixes.
- Put recommended action items for CSM and Sales only, using them as owners rather than audience labels.
- Do not invent feedback.
- Separate direct evidence from inference.
- If public job reqs are not reliable or company identity is ambiguous, say `No external job requistion found`.
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
8. CSM and Sales action plan next quarter
