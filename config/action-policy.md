# Action Policy

## Purpose

Define what Codex may do without additional approval in CSM HQ, and what requires Mike's explicit confirmation.

## Default Operating Mode

CSM HQ operates in supervised agentic mode.

The assistant may collect, organize, analyze, summarize, and draft outputs when Mike asks it to run a workflow. Mike remains the final approver for sensitive people-management and client-facing actions.

## Allowed Without Additional Approval

| Action | Rule |
|---|---|
| Read local workspace files | Allowed when relevant to the workflow. |
| Search Gmail for requested workflow evidence | Allowed when Mike asks Codex to run the workflow. |
| Summarize reports and feedback | Allowed with source references and confidence levels. |
| Draft Cliq-ready summaries | Allowed as draft text for Mike review. |
| Draft email or follow-up language | Allowed as draft text only. |
| Save draft reports under `outputs/` | Allowed using the output conventions. |
| Export draft reports to PDF | Allowed when exporting local workflow outputs under `outputs/`. |

## Requires Explicit Approval

| Action | Approval Requirement |
|---|---|
| Send email | Mike must explicitly approve the final recipient, subject, and body. |
| Forward email | Mike must explicitly approve the recipient and note. |
| Delete or trash email | Mike must explicitly approve the message IDs or search scope. |
| Archive email | Mike must explicitly approve the message IDs or search scope. |
| Apply or remove Gmail labels | Mike must explicitly approve the label and message scope. |
| Send client-facing updates | Mike must review and approve final language. |
| Send employee performance or compliance messages | Mike must review and approve final language. |
| Finalize performance ratings | Mike must review evidence and approve ratings. |

## Evidence Rules

Every analysis must separate:
- Direct evidence
- Interpreted insight
- Assumptions
- Missing data

Do not invent feedback, status, blockers, risks, or employee sentiment. If evidence is thin, say so and mark confidence as low.

## Manual Workflow Boundary

CSM HQ does not run scheduled jobs by default. Codex may run daily, weekly, monthly, quarterly, and review workflows only when Mike asks.

Codex must not:
- search Gmail
- call external APIs
- send messages
- delete messages
- archive messages
- label messages
- finalize reports without Mike review

unless the action is directly requested and remains within the approval rules above.
