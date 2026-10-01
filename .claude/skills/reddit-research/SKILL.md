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
