# CGCC local data snapshot

The CSV has one row per video published from 2026-01-01 through 2026-07-19: 23 full-length videos and 107 Shorts. Each row covers that video's first 90 days after publishing (published_date through window_end, Pacific time), so every video gets the same amount of time. The numbers come from the YouTube Analytics API. Subscriptions are those made on each video's watch page.

Use only the local CSV. Do not modify it. Write live-dashboard.html in this repo.

The prompts used in the talk are in `prompts/`.
