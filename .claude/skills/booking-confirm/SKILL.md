---
name: booking-confirm
description: Use when Varun pastes a confirmation email/text. Extracts the booking and updates anchors.md and trip.json.
---

1. Extract: restaurant, date, time, party size, price, platform, cancel-by deadline, status.
2. Strip booking/confirmation numbers, phone numbers and guest full names. Never write them anywhere, including drafts.
3. Mark CONFIRMED only if the pasted text confirms it; otherwise requested/proposed.
4. Update anchors.md and trip.json (keep trip.json isSample true until Varun confirms the plan); log in decisions.md.
5. Add a calendar draft (restaurant, date, time, cancel-by reminder) as plain text; Varun adds it himself.
6. Offer the arrival-card skill for door details.
