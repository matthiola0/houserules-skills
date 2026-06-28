# Project memory (long-term) — conventions & decisions

> The team's long-term memory for THIS repo. Unlike `prd.md` / `sdd.md` / `plan.md` (per
> task, thrown away after), this file **persists across tasks** so the team stops relearning
> the same things and stops relitigating settled calls. The CEO reads it every run and
> appends to it; the Coder and Reviewer propose entries. Keep it short and high-signal —
> prune anything stale.

## Conventions & gotchas (the "landmines")
Things that bit us once and shouldn't again. One line each, concrete.
- <e.g. `npm test` hangs unless `DATABASE_URL` is set — source `.env.test` first>
- <e.g. this repo uses workspaces; run scripts from the package dir, not the root>

## Decisions (lightweight ADR)
Why we chose what we chose, so nobody reopens it without new information. Append-only —
don't rewrite history; add a new row that supersedes an old one.
| date | decision | why | alternatives rejected |
|------|----------|-----|-----------------------|
| <YYYY-MM-DD> | <chose X> | <reason> | <Y — because …> |

## How the team updates this
- **CEO**: after each task/project, add new conventions learned and any design decisions made
  (and record any guardrail overrides the human approved).
- **Coder**: when a non-obvious gotcha cost you time, propose a one-line entry to the CEO.
- **Reviewer**: if the same class of finding recurs, propose a convention so it stops recurring.
