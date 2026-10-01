---
name: chat-ingest
description: Use to turn an exported group chat (iMessage .txt/.html) into a structured trip digest: bookings, recommendations, open questions.
---

Input: a chat export placed in trips/japan-2026/private/ (gitignored) or provided in the conversation. Work locally; never commit exports.

Steps:
1. Read in date order. Only extract trip-related content (places, dates, bookings, preferences, constraints, who is joining what).
2. Produce a digest with: (a) Bookings made, with date/time, venue, who made them, and evidence; (b) Requests or ideas not yet booked; (c) Recommendations people gave (who, what, why); (d) Open questions and decisions needed; (e) Conflicts or dates that do not line up.
3. Mark confidence: stated plainly in chat = confirmed in chat; implied = unverified. Never mark a booking confirmed unless someone said so; ask the owner to verify against the actual confirmation.
4. Propose updates to anchors.md, pools/ and decisions.md and show a diff. Do not apply without approval.
5. On later runs, process only messages after the last processed date (record it in decisions.md) and report what changed.
Privacy: ignore personal chatter not about the trip. Omit phone numbers, addresses of private homes, and anything sensitive about the other people. Do not quote messages in anything that goes to share/.
