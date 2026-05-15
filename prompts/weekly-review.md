# Weekly Team Review Prompt

Review daily reports from the requested weekly window. If Mike does not specify dates, use the past 7 calendar days ending on the requested run date.

Group by team.

For each team:
1. Productivity trend
2. Missed reports
3. Repeated blockers
4. Strong performers
5. Low visibility members
6. Capacity issues
7. Client risk indicators

Output:
- editable Markdown source at `outputs/weekly/YYYY-MM-DD_YYYY-MM-DD/weekly-team-review.md`
- standalone HTML dashboard at `outputs/weekly/YYYY-MM-DD_YYYY-MM-DD/weekly-team-review.html`
- Weekly Team Health Score
- Red / Yellow / Green
- Recommended interventions

The standalone HTML dashboard must open directly in a browser without a local server and include search, filters, easy navigation, client/team sections, employee summaries, repeated blockers, low visibility/compliance watch, manager actions, and source audit.

Do not create a PDF or PowerPoint deck unless Mike explicitly requests that format for the run.
