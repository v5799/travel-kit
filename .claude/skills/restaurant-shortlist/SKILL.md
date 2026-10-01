---
name: restaurant-shortlist
description: Use to find meals. Builds verified shortlists, esp. omakase via Tabelog.
---

Inputs: city/area, date, meal, budget, party size, constraints.
1. Search Tabelog, official sites, Google Maps, recent reviews. Prefer sources from the last 12 months.
2. For each candidate verify: still open, hours, closed days, reservation method (phone, web, concierge, platform), cash-only, language support, allergy handling.
3. Return 3 options: safe / adventurous / convenient. Table: name | area | price band | why | how to reserve | verified (source+date) | risk.
4. Never claim availability. Say how the owner checks it.
5. Add chosen item to anchors.md as idea; log in decisions.md.
