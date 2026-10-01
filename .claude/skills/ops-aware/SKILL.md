---
name: ops-aware
description: Use to pick up ops-kit's outbox notes (receipts ready, trip deadlines, connector audit results) and act on them through travel-kit's own skills. Reads ops-kit; writes only to travel-kit.
---

Read the other repo only as CLAUDE.md "Cross-repo rules" allow. Start with ../ops-kit/INTERFACE.md and read only its allow-list: ../ops-kit/outbox/ and ../ops-kit/INTERFACE.md.
Never read ../ops-kit/private/, ../ops-kit/accounts.csv or ../ops-kit/logs/. Never write anything in ../ops-kit.

1. List notes in ../ops-kit/outbox/ dated after the last "[cross] ops-kit outbox read" line in trips/<trip>/decisions.md.
2. For each note, decide which travel-kit skill handles it: receipts -> budget-log (writes only trips/<trip>/budget.csv); booking or deadline facts -> booking-confirm or anchors.md, only after the owner confirms; connector or tool results -> note in decisions.md only.
3. Never copy a note into travel-kit. Log one line per note in decisions.md: `- <date>: [cross] ops-kit outbox read: <note path> -> <what travel-kit did or "no change">`.
4. If travel-kit needs to answer, write a note in travel-kit's own outbox/ (see outbox/README.md).
Finish with the end-of-session check in CLAUDE.md "Cross-repo rules".
