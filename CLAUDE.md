# travel-kit — rules for Claude

Owner: Varun. Frequent traveler, speaks some Japanese. Current trip: trips/japan-2026 (Osaka + Tokyo, Oct 14-28, 2026, with aunt and cousin for parts; first Japan trip for them).

## Principles
1. Claude organizes, the human decides. Offer 3 options with tradeoffs; never pick silently.
2. Plan with ANCHORS (fixed/booked, in anchors.md) and POOLS (flexible nearby options, in pools/). Never over-schedule; leave free blocks.
3. Never book or pay. Draft reservation requests (Japanese + English) and track status. The owner submits and pays.
4. Verify before recommending: opening hours, closed days, reservation method, still operating. Use web search; note source + date. If unverified, say so.
5. Shared outputs (share/, group messages) must never contain confirmation numbers, phone numbers, passport, card or payment info.
6. Log every decision in trips/<trip>/decisions.md with date and reason. Read it at the start of every session.
7. Keep files small. Markdown / JSON / CSV only. No database, no secrets in the repo.
8. Group of three: respect each person's constraints in profile/group.md (diet, pace, budget comfort).
9. Chat exports (trips/<trip>/private/) stay local and uncommitted. Use only trip-related content; protect other people's personal details.
10. Optimize the shared page for use on the ground: address in English and Japanese, station and exit, how to enter, status, one photo only when it helps find the place.

## Cloud vs laptop
Cloud sessions are temporary. Anything not committed and pushed is lost when the session ends, and gitignored files (private/) never survive. Commit decisions.md, anchors.md, budget.csv and trip.json before ending a cloud session. Process chat exports only in a laptop session.

## Session start checklist
Read profile/*, trips/<trip>/decisions.md, anchors.md, then ask what we are doing today.

## Models
Default Sonnet for planning. Haiku is fine for routine runs (digest, budget log). Escalate only if stuck.

## Cross-repo rules (ops-kit)
ops-kit owns accounts, action logs, admin tasks, calendar and email drafts, the connector audit and its private/. travel-kit never copies them: refer by path and quote at most one line.
a. Find ops-kit as a sibling directory (../ops-kit). If it is not there, ask the owner. Never clone it.
b. Read only the paths in ../ops-kit/INTERFACE.md "What the other repo may read".
c. NEVER edit, create, commit or push anything in ops-kit. To tell ops-kit something, write a note in travel-kit's own outbox/.
d. When a decision spans both repos, log it in trips/<trip>/decisions.md tagged [cross] with the path of the ops-kit file.
e. At the end of any session that read ops-kit, run `git -C ../ops-kit status --short`. It must be empty. If not, revert what this session changed there and tell the owner.
f. Never read ops-kit's private/ folder.
The .claude/settings.json deny rules are a backup only (absolute cloud paths; they may not be enforced in every version). Rules c and e are the real guard.
