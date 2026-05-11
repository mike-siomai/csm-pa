---
name: quarterly-account-review
description: Create CSM HQ Quarterly Account Review slide/page outputs for Sales and COO from checkpoints, daily reports, client feedback, delivery trends, compliance patterns, and reliable public software-development job requisitions. Use when Mike asks for QARs, account health reviews, quarterly client/account summaries, growth signals, or Sales/COO-ready account review decks.
---

# Quarterly Account Review

## Core Rule

Use this skill for Quarterly Account Review work. Read `AGENTS.md`, `config/action-policy.md`, `config/output-conventions.md`, and `prompts/quarterly-account-review.md` before creating outputs. QARs are evidence-first executive updates, not long narrative reports.

If the quarter, account set, audience, source coverage, output format, or QAR theme file is unclear, ask Mike before proceeding.

## Inputs

Use available evidence from:

- Monthly checkpoints
- Daily reports
- Client feedback emails
- Gemini notes or transcripts
- Compliance and staffing patterns
- Reliable public software-development job requisition sources

Do not assume direct API access. Use the available connector, local file, or browser/search route for the task.

## Required Theme

Final deck output should use the Google Drive `QAR Theme` deck as the theme/template source:
`https://docs.google.com/presentation/d/1ETHEwUDG42jwsuL7ofminmuhxQOpMC2pNEogUp1vGDQ`

If the theme is unavailable, state the limitation and create a draft structure for Mike review rather than inventing a separate visual system.

## Growth Signal Rules

Growth Signal may include only:

1. Reliable public software-development job requisitions tied to the correct company identity.
2. Evidence-based software-development resource opportunities based on checkpoints or daily reports, such as roadmap demand, burnout, overutilization, recurring blockers, QA needs, DevOps/platform gaps, mobile/backend/frontend needs, AI enablement, or automation demand.

If no reliable external software-development job requisition is found, write exactly:
`No external job requistion found`

Do not use vague company news, non-technical openings, general expansion language, or unsupported upsell ideas as growth signals.

## Slide Structure

Use one account per slide/page. Prefer 2-4 bullets per section. Do not label bullets as `Sales:` or `COO:` unless naming an action owner.

Use `references/account-slide-template.md` as the canonical structure.

Required order:

1. Quarterly Account Review
2. ACCOUNT NAME Health: ...
3. Confidence: ...
4. Client Health Evidence
5. Growth Signal
6. Open Software-Development Job Reqs
7. Recommended Resource Opportunity
8. Action Items
9. Source footer: `Gmail: ... Public: ...`

## Health and Confidence

Health labels:
`Green`, `Green / Watch`, `Green / Low Signal`, `Yellow`, `Red / Recovery`, `Coverage-Limited`, `Onboarding`

Confidence labels:
`High`, `Medium`, `Low`

Lower confidence when source coverage is thin, public company identity is ambiguous, or evidence comes mainly from indirect artifacts.

## Output

Save working notes and source audit under:
`outputs/quarterly/YYYY-Q#/quarterly-account-review/`

PowerPoint is the default manager-facing artifact. Keep concise Markdown as an editable/audit source when useful.

## Required Checks

- Separate direct evidence from inference.
- Do not invent client feedback, risks, resource needs, or growth signals.
- Use public job requisition scans only when company identity is reliable.
- Keep action items owned by CSM and Sales where appropriate.
- Preserve a source footer on each account slide/page.
- Default to draft for Mike review.

## Resources

- `references/account-slide-template.md`: canonical QAR slide structure.
- `references/research-rules.md`: public job requisition and source confidence rules.
- `schemas/account-slide.schema.json`: structured account slide schema.
