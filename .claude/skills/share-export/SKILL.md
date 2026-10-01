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
