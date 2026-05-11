# Daily Report Source Routing

## Schedule Source

Prefer the live Google Sheet roster. Use its `Employee`, `Client`, and scheduled weekday columns for routing and grouping. If unavailable, use `config/schedule.md` or the schedule snapshot in `AGENTS.md`, and state that the live sheet was unavailable.

## Evidence Priority

1. Gmail daily report emails are the primary source of truth.
2. The CSV fallback is used only for scheduled employees with missing Gmail evidence.
3. If Gmail and CSV both exist, rely on Gmail and label the row `both matched` only when the evidence aligns.
4. If Gmail and the roster conflict, keep roster-based routing and note the conflict.

## Audit Labels

| Label | Meaning |
|---|---|
| Gmail | Usable report found in Gmail. |
| CSV fallback | Gmail missing; fallback CSV provides usable substitute data. |
| both matched | Gmail and CSV both found and align; Gmail remains primary. |
| missing | No usable Gmail or CSV fallback evidence. |

## Missing or Unmapped Employees

Render scheduled employees even when evidence is missing. If an employee appears in Gmail but not in the roster, include them under `Unmapped / Needs roster validation` and do not silently exclude them.
