# travel-kit
Travel assistants
You are in a repo named travel-kit (a README may already exist; overwrite it). This is a file-based travel assistant for Varun. Do not add features, files or dependencies beyond what is listed.

Create EXACTLY these files with EXACTLY this content (paths relative to the repo root). Use ~~~~ blocks as file boundaries.

FILE: .claude/skills/arrival-card/SKILL.md
~~~~
---
name: arrival-card
description: Use for each confirmed or requested booking. Builds the on-the-ground details people actually need at the door.
---

For a given item, fill in (verify with sources, cite date; mark unknowns as unknown):
1. Address in English and Japanese (copy exact text so it can be shown to a taxi driver).
2. Nearest station, exit number, and walking directions in plain words ("exit 14, straight 6 minutes, building with green sign, 3F").
3. How to enter: bell, lift, shoes, queue rules, which door.
4. Arrive-by time and what happens if late. Name the booking is under. Cash-only? Cancellation cutoff.
5. "Say at the door": one Japanese line with romaji and English.
6. Photo request: ask the owner for one entrance or storefront photo (a Google Maps Street View screenshot is fine) and a caption. Never use stock or AI images.
Output as an object matching the item schema in share-export.
~~~~

FILE: .claude/skills/budget-log/SKILL.md
~~~~
---
name: budget-log
description: Use to log or summarize spending.
---

Append rows to trips/<trip>/budget.csv (JPY). Summarize by category and per person on request. Convert currency only with a stated rate and date.
~~~~

FILE: .claude/skills/chat-ingest/SKILL.md
~~~~
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
~~~~

FILE: .claude/skills/day-planner/SKILL.md
~~~~
---
name: day-planner
description: Use to turn anchors and pools into a day plan.
---

1. Start from anchors for the date, then pull pool items near them.
2. Cluster by walking distance; give transit with line/station; estimate energy and steps.
3. Leave free blocks; add a rain/fatigue backup (see pivot).
Output: morning/afternoon/evening, with times, travel legs, and what is fixed vs flexible.
~~~~

FILE: .claude/skills/docs-checklist/SKILL.md
~~~~
---
name: docs-checklist
description: Use before departure.
---

Check: passport validity, visa/entry rules for the owner's passport, Visit Japan Web, insurance, copies stored offline, customs rules for medicines. Verify on official government sites; cite them. Output a dated checklist.
~~~~

FILE: .claude/skills/group-digest/SKILL.md
~~~~
---
name: group-digest
description: Use to write updates for the group chat or email.
---

Output a short iMessage-ready text and an email version: tomorrow's plan, meeting point and time, what to bring, one question to vote on. Plain language for first-timers. Never include confirmation numbers or phone numbers.
~~~~

FILE: .claude/skills/language-kit/SKILL.md
~~~~
---
name: language-kit
description: Use for phrases and menus.
---

Output situational phrases (kanji, romaji, English): arriving at a restaurant, allergies, ordering omakase, paying, asking directions, emergencies. Keep to what is requested.
~~~~

FILE: .claude/skills/logistics/SKILL.md
~~~~
---
name: logistics
description: Use for trains, passes, eSIM, airport transfers, luggage.
---

Verify current options and prices with sources. Cover: airport to hotel, IC card/mobile wallet, intercity trains (Osaka-Tokyo), luggage forwarding, eSIM, power adapters. Give step-by-step instructions a first-timer can follow.
~~~~

FILE: .claude/skills/pivot/SKILL.md
~~~~
---
name: pivot
description: Use when plans break: rain, tiredness, closure, delay.
---

Ask: where are you, time, energy, weather. Pull alternatives from pools/ first, then search. Offer 3 options sorted by effort. Update anchors/pools if something changes.
~~~~

FILE: .claude/skills/reddit-research/SKILL.md
~~~~
---
name: reddit-research
description: Use to mine Reddit discussions for practical, recent, on-the-ground info (travel, tools, how people built things). Handles the fact that Reddit blocks direct fetching.
---

Reddit pages usually cannot be fetched directly. Work in this order:
1. Web search with site words (e.g. "reddit Tokyo omakase reservation tips 2026") and read what the results return.
2. Use links, PDFs or screenshots the owner provides (the owner can print a thread to PDF and upload it).
3. If the owner has official Reddit API credentials, use the official API (read-only, rate-limited, within Reddit's terms). Never store credentials in the repo; read them from environment variables.

Output: dated summary of recurring themes, what is current vs outdated (check post dates), conflicting opinions, and the thread links used. Quote sparingly; paraphrase. Flag anecdotes as anecdotes.

Scope for private-research topics: summarize discussion about legal changes, scams and overcharging patterns, safety, health, etiquette, and licensed retail. Do not compile venue-by-venue reviews or rankings of paid sexual services.
~~~~

FILE: .claude/skills/reservation-drafter/SKILL.md
~~~~
---
name: reservation-drafter
description: Use after the owner picks a restaurant. Drafts the request; the owner submits it.
---

Inputs: venue, date/time, party size, dietary notes, owner name.
Output: (a) Japanese message, (b) English message, (c) phone script in Japanese with romaji, (d) what to expect (deposit, cancellation policy, cut-off times).
Rules: never invent details; no payment info; keep it polite and short. Mark anchor status 'requested' only after the owner says it was sent.
~~~~

FILE: .claude/skills/restaurant-shortlist/SKILL.md
~~~~
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
~~~~

FILE: .claude/skills/share-export/SKILL.md
~~~~
---
name: share-export
description: Use to publish the group page data. Writes a sanitized share/trip.json for the Lovable page.
---

Read anchors.md, pools/, decisions.md and write share/trip.json using the schema in trips/japan-2026/trip.json.
Item fields: time, title, type (meal|transit|activity|stay), status (confirmed|requested|idea), area, address_en, address_ja, maps_url, station, how_to_get_there, how_to_enter, arrive_by, reservation_name, cash_only, cancel_by, notes[], say_at_door{ja,romaji,en}, photo{url,caption}.
Day fields: date, city, title, who[], items[], options[{title, why, area, walk_minutes, maps_url}].
Food fields: name, area, city, price_band, status, why, maps_url, photo.

Include only what helps people on the ground: address in English and Japanese, station and exit, how to enter, arrive-by, name on the booking, cash-only, cancel-by, one-line notes.
STRIP: phone numbers (except 110 and 119), confirmation codes, passport, card or payment info, email addresses, anything from private chats not meant for the group.
Set status honestly: confirmed only after the owner says it is confirmed. Leave out empty fields.
Show the owner a diff before they paste it into the Lovable page (public/trip.json).
~~~~

FILE: .claude/skills/trip-intake/SKILL.md
~~~~
---
name: trip-intake
description: Use at the start of a trip or when facts are missing. Gathers dates, group, constraints.
---

1. Read profile/ and the trip folder. Ask at most 8 questions, grouped, skipping what is known.
2. Cover: who joins which legs, hotels, arrival/departure, diet/allergies per person, pace, budget band per meal, must-do/never-do, shopping targets.
3. Update profile/group.md, trips/<trip>/anchors.md, decisions.md.
Output: a 10-line trip brief and a list of what is still unknown.
~~~~

FILE: .gitignore
~~~~
.env
*.key
trips/*/private/
.DS_Store
~~~~

FILE: CLAUDE.md
~~~~
# travel-kit — rules for Claude

Owner: Varun. Frequent traveler, speaks some Japanese. Current trip: trips/japan-2026 (Osaka + Tokyo, Oct 14-24, 2026, with aunt and cousin for parts; first Japan trip for them).

## Principles
1. Claude organizes, the human decides. Offer 3 options with tradeoffs; never pick silently.
2. Plan with ANCHORS (fixed/booked, in anchors.md) and POOLS (flexible nearby options, in pools/). Never over-schedule; leave free blocks.
3. Never book or pay. Draft reservation requests (Japanese + English) and track status. The owner submits and pays.
4. Verify before recommending: opening hours, closed days, reservation method, still operating. Use web search; note source + date. If unverified, say so.
5. Shared outputs (share/, group messages) must never contain confirmation numbers, phone numbers, passport, card or payment info.
6. Log every decision in trips/<trip>/decisions.md with date and reason. Read it at the start of every session.
7. Keep files small. Markdown / JSON / CSV only. No database, no secrets in the repo.
8. Group of three: respect each person's constraints in profile/group.md (diet, pace, budget comfort).

## Session start checklist
Read profile/*, trips/<trip>/decisions.md, anchors.md, then ask what we are doing today.

## Models
Default Sonnet for planning. Haiku is fine for routine runs (digest, budget log). Escalate only if stuck.

9. Chat exports (private/) stay local and uncommitted. Use only trip-related content; protect other people's personal details.
10. Optimize the shared page for use on the ground: address in English and Japanese, station and exit, how to enter, status, one photo only when it helps find the place.
~~~~

FILE: README.md
~~~~
# travel-kit
Reusable, file-based travel assistant. Open this folder in Claude Code and say: "run trip-intake".

Flow: intake -> restaurant-shortlist -> reservation-drafter (you submit) -> day-planner -> group-digest -> share-export -> publish to the Lovable page.

Skills live in .claude/skills/<name>/SKILL.md. Add new trips under trips/<name>/.

New: chat-ingest (digest an exported group chat), arrival-card (door-level details per booking).
~~~~

FILE: profile/group.md
~~~~
# Group (fill in via trip-intake)
- Aunt: diet/allergies ? | pace ? | budget comfort ? | joins: Osaka + Tokyo, Oct 14-24 (confirm which legs)
- Cousin: diet/allergies ? | pace ? | budget comfort ? | first time in Japan
- Rule: first-timers need simple instructions (station names, exits, what to say at the door).
~~~~

FILE: profile/preferences.md
~~~~
# Varun — travel preferences (edit freely)
- Food: high-end omakase and Michelin-level meals (found via Tabelog), plus convenient everyday meals chosen by location and timing.
- Shopping: streetwear, accent jewelry (Chrome Hearts-type), sneakers.
- Pace: balanced; likes route-optimised days with minimal backtracking.
- Language: some Japanese.
- Always flag: closed days, reservation difficulty, cash-only places.
~~~~

FILE: share/README.md
~~~~
share-export writes a sanitized trip.json here. Paste or upload it into the Lovable page. Never put booking codes or phone numbers here.
~~~~

FILE: trips/japan-2026/anchors.md
~~~~
# Anchors (fixed/booked) — date | time | what | city | status (idea/requested/confirmed)
~~~~

FILE: trips/japan-2026/budget.csv
~~~~
date,category,item,amount_jpy,paid_by,notes
~~~~

FILE: trips/japan-2026/decisions.md
~~~~
# Decision log (newest first)
- 2026-10-01: Project set up. Claude organizes; owner books and pays. Group sees a read-only page.
~~~~

FILE: trips/japan-2026/pools/README.md
~~~~
Flexible options grouped by area, e.g. ginza.md, shibuya.md, namba.md. One line each: name | type | why | hours/closed days | verified date.
~~~~

FILE: trips/japan-2026/private/README.md
~~~~
Put chat exports here. This folder is gitignored, so it never reaches GitHub. Cloud sessions cannot see it; process exports on a laptop session or upload them to a Claude chat.
~~~~

FILE: trips/japan-2026/trip.json
~~~~
{
  "isSample": false,
  "title": "Osaka + Tokyo",
  "startDate": "2026-10-14",
  "endDate": "2026-10-24",
  "travelers": [
    {
      "name": "Varun",
      "legs": "Oct 14-24"
    },
    {
      "name": "Aunt",
      "legs": "confirm"
    },
    {
      "name": "Cousin",
      "legs": "confirm"
    }
  ],
  "feedbackUrl": "",
  "days": [
    {
      "date": "2026-10-14",
      "city": "Osaka",
      "title": "",
      "who": [
        "Varun"
      ],
      "items": [],
      "options": []
    }
  ],
  "food": [],
  "practical": []
}
~~~~

AFTER CREATING FILES: commit with message 'Initial scaffold' and push. Then reply in 5 lines: what was created, and the first question from the trip-intake skill. Do not run installs. Never book or pay for anything.
