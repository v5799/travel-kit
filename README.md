# travel-kit
Reusable, file-based travel assistant. Open this folder in Claude Code and say: "run trip-intake".

Flow: intake -> restaurant-shortlist -> reservation-drafter (you submit) -> day-planner -> group-digest -> share-export -> publish to the Lovable page.

Skills live in .claude/skills/<name>/SKILL.md. Add new trips under trips/<name>/.

New: chat-ingest (digest an exported group chat), arrival-card (door-level details per booking).

Cloud sessions reset: commit and push before you finish. Chat exports (private/) are laptop-only.
