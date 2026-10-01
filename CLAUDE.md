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
