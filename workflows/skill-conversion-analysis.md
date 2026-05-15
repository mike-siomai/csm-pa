# CSM HQ Skill Conversion Analysis

## Recommendation

Convert repeatable, evidence-heavy workflows into project-local Codex Skills when they have stable inputs, repeatable outputs, required review gates, and recurring quality checks. Keep one-off judgment calls and sensitive message sending as manual workflows or playbooks.

## Convert First

| Candidate Skill | Priority | Why It Should Be a Skill | Current State | Next Action |
|---|---:|---|---|---|
| Daily Report | 1 | High-frequency, source-routing heavy, strict Gmail/CSV/schedule rules, required HTML dashboard. | Exists as `skills/daily-report/`. | Keep refining schemas and dashboard checks. |
| Weekly Team Review | 2 | Repeats weekly, reuses daily report evidence, needs consistent team health/risk analysis and standalone HTML output. | Added as `skills/weekly-team-review/`. | Add sample HTML pattern after next real run. |
| Monthly Checkpoint | 3 | Transcript/email extraction has strict attribution, citation, cleaning, and review requirements. | Exists as `skills/monthly-checkpoint/`. | Add speaker-attribution schema if transcript volume grows. |
| Quarterly Performance Review | 4 | Sensitive people-management output, evidence/inference separation, competency ratings, mandatory review gates. | Exists as `skills/quarterly-performance-review/`. | Add rating calibration examples over time. |
| Quarterly Account Review | 5 | Executive audience, fixed slide structure, public job-req scan rules, evidence-first account summary. | Exists as `skills/quarterly-account-review/`. | Keep public research rules tight and source-driven. |

## Good Skill Candidates Next

| Candidate Skill | Recommendation | Rationale | Review Gate |
|---|---|---|---|
| Gmail Daily Report Normalizer | Create after the weekly skill stabilizes. | Normalizes Gmail evidence into reusable records for daily and weekly reporting. Reduces repeated parsing. | Mike review only for source conflicts; no sending or labeling without approval. |
| Source Coverage Auditor | Create as a utility skill or reference module. | Missing reports, malformed reports, duplicate submissions, roster mismatches, and fallback usage recur across workflows. | Human validation for ambiguous names, conflicts, or low-confidence recovery. |
| Follow-up Drafting | Create as a draft-only skill. | Compliance reminders, blocker follow-ups, and coaching nudges repeat, but wording must stay supervised. | Mandatory Mike approval before sending. |
| Incident / Escalation Brief | Create once patterns are documented in playbooks. | Escalations need structured evidence, impact, timeline, owners, and next action. | Mandatory Mike approval before client or leadership use. |
| Timelog / Compliance Review | Create when reliable source exports are available. | Timelog compliance is recurring and rules-based, but source quality must be confirmed first. | Human review before employee-facing action. |

## Keep As Markdown Playbooks For Now

| Playbook | Why Not a Skill Yet |
|---|---|
| Poor performance escalation | High sensitivity and case-specific judgment. Use templates and checklists before automating. |
| Client no-show monthly checkpoint | Procedural and situational; a short playbook is enough until volume increases. |
| Timelog noncompliance | Needs confirmed source data and company policy rules before skill automation. |
| Client-facing apology or incident response | Tone, politics, and relationship context require manual judgment. |

## Skill vs Playbook Rule

Use a Skill when the workflow has:

- repeatable input sources,
- repeatable output files,
- stable section structure,
- recurring source-quality checks,
- evidence/inference rules,
- validation steps that Codex can verify.

Use a Playbook when the workflow is:

- sensitive and situational,
- mostly decision guidance,
- dependent on current relationship context,
- not frequent enough to justify a full skill,
- risky to automate beyond draft preparation.

## Mandatory Human Review Gates

- Any client-facing message.
- Any employee-facing coaching, compliance, or disciplinary message.
- Any finalized performance rating.
- Any account escalation outside the workspace.
- Any ambiguous transcript attribution or unclear employee/client identity.

## MVP Skill Roadmap

1. Keep Daily Report, Monthly Checkpoint, Quarterly Performance Review, and Quarterly Account Review as canonical workflow skills.
2. Use the new Weekly Team Review skill for the next weekly run and refine its HTML template based on actual output.
3. Create a Gmail Daily Report Normalizer only after the daily and weekly reports show repeated parsing friction.
4. Create a Source Coverage Auditor when missing reports, roster mismatches, and fallback conflicts become common enough to centralize.
5. Keep sensitive communication as draft-only templates/playbooks until Mike explicitly asks for more automation.
