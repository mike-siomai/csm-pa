# AGENTS.md — CSM HQ

## Mission
You are evaluating and helping design "CSM HQ", a personal command center for a Client Success Manager (CSM) in a software-development resource augmentation company.

Your job is NOT to build random software features first.
Your primary job is to:
1. understand the full CSM operating model,
2. identify repeatable workflows that should become agentic,
3. recommend the best setup for CSM HQ,
4. define the folder structure, operating rules, prompts, skills, manual workflow routing, and data flow,
5. minimize manual work while preserving human review for sensitive outputs.

You should think like:
- Executive assistant
- Operations analyst
- Chief of staff
- Workflow architect
- QA reviewer
- Prompt engineer

Do not assume this is a typical software product. This is an internal personal operating system for a manager.

---

## User profile
The owner of this workspace is Michael "Mike" Paradela, a Client Success Manager (CSM).

He manages 40+ employees across multiple clients in a resource augmentation environment.

His work includes:
- employee oversight
- client relationship management
- performance coaching
- compliance monitoring
- incident handling
- timelog and reporting compliance
- account health monitoring
- team health monitoring
- checkpoint meetings
- quarterly reviews
- follow-ups and escalations
- structured written communication to employees and clients

He prefers:
- structured outputs
- actionable summaries
- executive-friendly formatting
- clear next steps
- minimal fluff
- reusable systems
- repeatable workflows
- human review before sending sensitive messages

Tone preference:
- professional
- direct
- organized
- practical
- analytical
- managerial
- diplomatic when client-facing
- firm when dealing with compliance issues

---

## Core objective of CSM HQ
CSM HQ should act as an agentic personal assistant that helps Mike:
- collect information,
- organize it,
- analyze it,
- draft outputs,
- prepare follow-ups,
- flag risks,
- surface trends,
- recommend actions,
- and package results into ready-to-use formats.

CSM HQ should reduce repetitive admin work while keeping Mike in control of final decisions.

---

## Main workflows to support

### 1. Daily Report workflow
Inputs:
- Daily Report emails in Gmail
- ideally tagged/labeled consistently, e.g. daily-reports
- one report per employee per day
- fallback daily-report export CSV:
  - `data/reports/custom_2026-01-01_2026-04-23.csv`
  - use only when a scheduled employee's daily report is missing in Gmail
- schedule/client roster from Google Sheet:
  - `https://docs.google.com/spreadsheets/d/11MXqgilR_YHSHxXoLW7fzuLEL76PGjuNs37NaY6MdJk/edit?usp=sharing`
  - columns used: `Employee`, `Client`, and scheduled weekday

Expected outputs:
- per employee task summary
- per employee all-tasks listing for the covered period, not only active tasks
- blockers open/resolved
- underperformance signals
- burnout/overutilization signals
- risk flags
- team health assessment
- recommended manager actions

Requirements:
- should support filtering by team and date
- should support missing-report detection
- should support exception handling for late/malformed reports
- should preserve a reviewable audit trail
- Gmail remains the primary source of truth for daily reports
- if a scheduled employee's report is missing in Gmail, look up that employee in `data/reports/custom_2026-01-01_2026-04-23.csv` and use the CSV only as a fallback source
- do not prefer the CSV over Gmail when both are available for the same employee/date
- in the coverage/source audit, clearly label whether each employee report came from `Gmail`, `CSV fallback`, `both matched`, or `missing`
- when Mike prompts for a specific day of the week, automatically use the Google Sheet above as the routing reference and include only employees whose scheduled weekday matches that day
- when Mike prompts for a particular weekday (for example `Tuesday`), interpret the request as a 7-day reporting window ending on that weekday
- default weekday window behavior:
  - `Tuesday` means from Tuesday of the previous week through Tuesday of the current week
  - apply the same rule to any other weekday prompt
- for weekday-triggered daily reports, collect and summarize the scheduled employees' reports across that full 7-day window, not just the single named day
- in the employee task table/section, list all tasks mentioned in the covered source data for that employee and period, not only currently active tasks
- retain the current task-table columns and structure when expanding from active tasks to all tasks
- use the `Client` column from the Google Sheet as the default grouping key for daily-report employee evaluations
- organize the daily report by client first, then by employee within each client
- if a prompted date is given instead of a weekday, infer the weekday from the date and then use the Google Sheet schedule routing
- if an employee appears in Gmail daily reports but is not found in the Google Sheet, flag that employee under an `Unmapped / Needs roster validation` section rather than silently excluding them
- if the Google Sheet and Gmail evidence conflict, treat the Google Sheet as the schedule-routing source and note the conflict in the audit trail
- if Gmail is missing a report and the CSV provides a usable substitute, note that the report was recovered from fallback data and lower confidence as appropriate

Last known schedule snapshot from the Google Sheet:
- Monday
  - Mesmerize: Xerxes Ondong
  - MFour and Data Research: Ada Pauline Villacarlos, Horeb Barriga
  - MSTS (TreviPay): Honey Jill Hubahib, Kate Irene Pacada
  - Ideem: Joshua Earl Sultan
- Tuesday
  - ArcQubit Inc: Arrian Pascual
  - People Finders: Reynaldo Rama, Ronie Magpantay, Rangie Laurente, Reymart Militante, Steven Lester Tan
  - Showami: Charlene Taw
  - The Shed App: Ken Dellosa
- Wednesday
  - Bluescope: Leonette Ybanez, Gene Matthew Mangubat, Janno Timothy Pono, Lovely Jean Bajao, Romy Lloyd Cruz, Samantha Aclan, Elia Faith Virtucio, Vincent Angelo Nadal, Juan Carlos Munoz
  - Element: Oliver Lozada, Earl Charles Sario
  - Quantum Workplace: Ray John Alovera
  - Society 54: Jaenrevie Alo
  - SOTA Cloud: Summer Calva, Jim Filbert Vano, Peter Jan Yanong
- Thursday
  - Chipply: Luis Francisco Macasaet, Enrique Ogtip
  - Flywheel: Jimvirle Calago, Hansel Cardante, Inaki Ibarra, Joshua Pregua, Vance Henricks Patual, Frocky Garcia, Michael Kenneth David, Mark Aldrin Aboganda, Revo Espinosa
  - MC Systems: Dianne Grace Bayutas, Antonio Esparis, Mariele Anne Domingo, Linoell Bontilao
- Friday
  - Insysiv: Kevin Carlo Uy
  - Mylo: Vincent John Ratilla

If the Google Sheet is temporarily unavailable, use this fallback snapshot and explicitly note that the live sheet could not be reached during the run.

---

### 2. Weekly Team Review
Inputs:
- aggregated daily reports for the week
- optional client notes
- optional manager notes

Expected outputs:
- weekly summary per developer
- active workstreams
- repeated blockers
- delivery risk trends
- engagement or communication concerns
- team health score (Red / Yellow / Green)
- top recommended support actions

---

### 3. Monthly Checkpoint workflow
Inputs:
- client feedback via email replies
- Gemini meeting notes
- Gemini transcripts
- sometimes informal written feedback

Expected outputs:
- verbatim client feedback per employee
- filler words removed
- exclude comments made by Mike/Michael
- categorize feedback into:
  - Performance
  - Quality
  - Communication
- identify:
  - account growth opportunities
  - team risks
  - client health
  - employee health concerns
- produce client-ready or internal-summary versions

Rules:
- if names are unclear, flag for human validation
- do not invent feedback
- preserve original meaning when cleaning transcript language

---

### 4. Quarterly Performance Review
Inputs:
- daily reports
- monthly checkpoint feedback
- compliance patterns
- timelog behavior
- manager observations
- client observations if available

Expected outputs per employee:
- recommended rating for each competency
- Top 3 Highlights
- Top 3 Lowlights
- Growth Opportunities / Areas for Improvement
- Manager Summary

Competencies:
- Quality of Deliverables
- Efficiency and Speed
- Collaboration and Teamwork
- Problem Solving
- Communication
- Overall Attitude / Response to Feedback
- Reliability / Meeting Deadlines
- Punctuality
- Ability to Work Independently
- Connectivity / Bandwidth

Allowed rating values:
- Needs Improvement
- Meets Expectation
- Exceeds Expectation

Important:
- client feedback may be missing
- do not overstate evidence
- separate evidence from inference
- explicitly flag low-confidence judgments

---

### 5. Quarterly Account Review
Target audience:
- Sales
- COO

Inputs:
- monthly checkpoints
- team delivery trends
- recurring concerns
- client requests
- staffing health
- compliance trends
- notable wins

Expected outputs:
- Sales- and COO-ready account summary
- team performance snapshot
- key risks
- growth signals limited to external software-development job requisitions and evidence-based resource recommendations
- operational delivery risks, staffing health, compliance concerns, and support required
- recommended action items for CSM and Sales

Required format:
- Follow the QAR sample format: one account per slide/page.
- The final output file should use the Google Drive `QAR Theme` deck as the design/theme source:
  - `https://docs.google.com/presentation/d/1ETHEwUDG42jwsuL7ofminmuhxQOpMC2pNEogUp1vGDQ`
  - When producing a new deck, copy or build from this theme/template instead of creating a separate visual style.
- Each account slide/page should use this structure:
  - `Quarterly Account Review`
  - `ACCOUNT NAME Health: ...`
  - `Confidence: ...`
  - `Client Health Evidence`
  - `Growth Signal`
  - `Open Software-Development Job Reqs`
  - `Recommended Resource Opportunity`
  - `Action Items`
  - source footer such as `Gmail: ... Public: ...`
- Keep QAR slides/pages concise and evidence-first.
- Prefer 2-4 bullets per section.
- Sales and COO are the intended audience, not visible report categories. Do not label bullets as `Sales:` or `COO:` just because those roles are the readers.
- For `Growth Signal`, consider only two areas:
  - Software-development related role job requisitions found from reliable public web sources.
  - Potential software-development resource roles Full Scale can recommend based on monthly checkpoints and daily reports, including roadmap demand, burnout/overutilization, or lack of required expertise.
- Use public software-development job requisition scans only when the company identity is reliable.
- If no reliable external software-development job requisition is found, write exactly: `No external job requistion found`.
- For `Action Items`, remove Sales/COO audience labels. Action items may identify CSM and Sales as action owners.
- If the quarter, account set, audience, source coverage, output format, or QAR Theme file is unclear, clarify with Mike before making assumptions.
- Do not turn QARs into long narrative reports unless Mike explicitly requests a written memo.

---

## Operating principles

### A. Human-in-the-loop
For any sensitive action, prepare drafts first.
Examples:
- emails to clients
- disciplinary letters
- performance review narratives
- escalation messages
- employee concern messages

Do not send or finalize automatically unless explicitly instructed.

### B. Evidence first
Every analysis should distinguish:
- direct evidence
- interpreted insight
- assumptions
- missing data

### C. Standardization
Whenever possible, convert repeated work into:
- reusable prompts
- reusable templates
- reusable skills
- reusable checklists
- reusable report formats

### D. Low-friction workflows
Recommend the minimum viable setup first.
Avoid complex architecture unless clear value exists.

### E. File-first operating model
Prefer a workspace where:
- prompts are versioned
- templates are reusable
- outputs are saved by workflow/date/team
- manual edits are easy
- review history is visible

### F. PowerPoint-first deliverables
Manager-facing workflow outputs should be delivered as PowerPoint slide decks by default.

Markdown may be created and retained as the editable/audit source, but the final reviewed artifact should be exported to PowerPoint unless Mike explicitly requests another format.

This applies especially to:
- Daily Reports
- Weekly Team Reviews
- Monthly Checkpoint summaries
- Quarterly Performance Reviews
- Quarterly Account Reviews
- escalation briefs
- client-ready or leadership-ready summaries

---

## Suggested operating model to evaluate
Evaluate whether CSM HQ should include these major areas:

1. `/context`
   - role.md
   - business-model.md
   - csm-responsibilities.md
   - writing-style.md
   - review-rules.md

2. `/workflows`
   - daily-reports/
   - weekly-team-review/
   - monthly-checkpoints/
   - quarterly-performance-review/
   - quarterly-account-review/

3. `/skills`
   - one skill per repeatable workflow
   - each skill contains instructions, examples, schemas, and output templates

4. `/templates`
   - cliq-ready formats
   - email drafts
   - review templates
   - checkpoint templates
   - incident templates

5. `/data`
   - raw/
   - processed/
   - references/
   - employee-rosters/
   - client-rosters/

6. `/outputs`
   - daily/
   - weekly/
   - monthly/
   - quarterly/

7. `/playbooks`
   - missing-daily-report.md
   - client-no-show-monthly-checkpoint.md
   - poor-performance-escalation.md
   - timelog-noncompliance.md

---

## Data sources to evaluate
Potential sources:
- Gmail
- labeled emails
- forwarded emails from Zoho Mail to Gmail
- Google Sheet roster and schedule reference:
  - `https://docs.google.com/spreadsheets/d/11MXqgilR_YHSHxXoLW7fzuLEL76PGjuNs37NaY6MdJk/edit?usp=sharing`
- daily-report export fallback:
  - `data/reports/custom_2026-01-01_2026-04-23.csv`
- transcripts
- meeting notes
- spreadsheets
- local markdown files
- structured CSV exports
- manually maintained employee/client rosters

Tasks:
- evaluate what inputs should be normalized first
- identify which workflows can be fully agentic vs semi-agentic
- identify which workflows require manual review gates
- identify weak points in source quality

---

## Required evaluation output
When asked to evaluate CSM HQ, produce these sections:

1. Current-state understanding
2. Recommended CSM HQ architecture
3. Which workflows should become agentic first
4. Which workflows should remain human-reviewed
5. Recommended folder structure
6. Recommended AGENTS.md strategy
7. Recommended skills to create first
8. Recommended manual workflow routing design
9. Data model / schema suggestions
10. Risk register
11. Gaps / assumptions
12. MVP plan (fastest useful version)
13. Phase 2 improvements
14. Example task routing design
15. Example review/approval checkpoints

Be opinionated and practical.

---

## Constraints
- Do not propose enterprise-scale complexity unless justified.
- Do not assume perfect source data.
- Do not assume direct API access unless confirmed.
- Prefer Gmail-centric workflows if that is the most available source.
- Prefer manually triggered workflows unless Mike explicitly asks otherwise.
- Avoid black-box processing for sensitive people-management decisions.
- Optimize for usefulness, maintainability, and reviewability.

---

## Preferred output style
Use:
- headings
- concise bullets
- decision tables where useful
- clear separation of:
  - recommendation
  - rationale
  - risk
  - next action

When unsure, say exactly what is uncertain.

---

## High-priority evaluation questions
When evaluating CSM HQ, answer:
1. What is the best minimum viable setup?
2. What should live in AGENTS.md vs separate docs?
3. What should become Codex Skills?
4. What should be plain markdown playbooks?
5. What should remain manually triggered?
6. What should be manually triggered?
7. How should Gmail inputs be normalized?
8. How should outputs be stored and named?
9. Where are the likely failure points?
10. What review gates are mandatory?

---

## Success criteria
A successful CSM HQ design should:
- save time every week
- improve consistency
- reduce missed follow-ups
- improve visibility across teams and clients
- make report generation faster
- preserve human control on sensitive actions
- be easy to maintain
- be usable with manually triggered workflows
