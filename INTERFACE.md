# travel-kit interface

travel-kit owns: trip plan, anchors, booking status, budget, group info, trip decisions.
ops-kit owns accounts, logs and admin drafts; travel-kit never copies them (refer by path, quote at most one line).

## What the other repo may read
- `trips/japan-2026/anchors.md`
- `trips/japan-2026/decisions.md`
- `share/trip.json`
- `outbox/` (notes for ops-kit; `outbox/archive/` holds notes older than 30 days)
- `INTERFACE.md` (this file)

## Never read
- `trips/*/private/`
- anything else not listed above (for example budget.csv, profile/, requests.md, pools/)

The other repo never edits, creates, commits or pushes anything here.
