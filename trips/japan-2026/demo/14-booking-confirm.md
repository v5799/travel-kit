# 14 booking-confirm (FAKE TEXT ONLY; anchors.md, trip.json NOT changed)
**Input (fake):** "Reservation confirmed: Test Restaurant, Oct 21, 19:00, 2 guests, 8,000 yen, cancel free until Oct 18. Ref ABC-123."
## Extracted
- Restaurant: Test Restaurant | Date: Wed 2026-10-21 | Time: 19:00 | Party: 2 | Price: 8,000 yen (total vs per person not stated) | Platform: not stated | Cancel-by: free until Oct 18 (time not stated; Oct 18 is 3 days before) | Status: the text says "confirmed", so would be recorded confirmed.
- **Dropped:** "Ref ABC-123" (booking reference). No phone or guest name in the text.
## Proposed anchors.md line (not written)
`- Wed Oct 21 | 19:00 | Test Restaurant, 2 guests, 8,000 yen, cancel free until Oct 18 | Tokyo | CONFIRMED (per pasted text)`
## Proposed trip.json item (not written)
`{"time":"19:00","title":"Test Restaurant","type":"meal","status":"confirmed","cancel_by":"2026-10-18","notes":["2 guests","8,000 yen"]}`
## Calendar draft (plain text)
Wed Oct 21 19:00, Test Restaurant (2 guests). Reminder: cancel by Oct 18.
Verified: the reference code is absent from every output above.
**What it could not do:** nothing missing: ran on fake text, so no real file was updated; real runs also need the platform and time zone.
