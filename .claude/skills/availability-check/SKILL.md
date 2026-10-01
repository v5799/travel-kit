---
name: availability-check
description: Use to check public booking pages for open dates/seats on a list of restaurants. Read-only; never books.
---

Inputs: restaurants/URLs, date range, party size.
1. Open each public booking page read-only. Never log in, never submit, never fill payment. One pass per run. Respect each site's terms and rate limits.
2. If a site blocks automation, say so and give Varun the manual link.
3. Report a table: restaurant | platform | dates/seats open in range | price | fee | cancel-by | checked (date/time).
4. Availability changes daily: label results "as of <time>"; Varun checks live before booking.
5. Note anything useful in pools/ or decisions.md; do not mark anything requested/confirmed.
