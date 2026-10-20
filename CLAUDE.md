# Which video topic should I make next?

This repo holds a small export of my YouTube channel data for a live demo at the CGCC Entrepreneurship Series. Requests here are short on purpose: these project rules fill in the rest.

## The data

`data/demo-data.csv` has one row per video published from 2026-01-01 to 2026-07-19: 23 full-length videos and 107 Shorts. Each row covers that video's first 90 days after publishing, so every video gets the same amount of time. Columns: video_id, title, video_format, published_date, window_end, views, engaged_views, subscribers_gained, subscribers_lost. The numbers come from the YouTube Analytics API, and subscribers are those made on each video's watch page.

## How to work here

- Work only in this repo. Treat `data/demo-data.csv` as read-only.
- Compare full-length videos only with full-length videos, and Shorts only with Shorts.
- Show counts first, then rates, and leave a rate blank when its denominator is zero.
- Build the dashboard as one offline HTML file in the repo root named `live-dashboard.html` (`live-dashboard-bigquery.html` when built from BigQuery), with no external fonts, libraries, or network calls. Include the units, denominator, time window, source, and a plain-English explanation for somebody new to analytics, plus a source table of the rows.
- Before calling anything done, check that full-length plus Shorts equals the overall total and that the totals match the CSV, and say what the data cannot prove.
- This runs live in front of an audience. Keep the checks quick: verify totals by reading the data directly, skip browser screenshots and extra test tools, and aim to finish in about five minutes.
- When the checks pass, commit the dashboard with a short, plain message.

## BigQuery (only when a request asks for it)

- Use the `bq` command-line tool with my existing sign-in, read-only: never create, change, or delete anything, and add `--maximum_bytes_billed=1000000000` to every query. Make no other network calls.
- Tables are in the `youtube_analytics` dataset:
  - `video_current`: video_id, title, video_type (full_length or short), published_at.
  - `daily_video_analytics`: activity_date, video_id, subscribers_gained, snapshot_date.
  - `daily_traffic_sources`: activity_date, video_id, traffic_source_type, views, snapshot_date.
- A day can be loaded more than once: keep only the latest snapshot_date for each day, video, and traffic source.
- Use videos published from 2026-01-01 through 2026-07-19 in Pacific time, and sum each video's views and subscribers gained from its publish day through 89 days later. Save the result as `data/bq-first-90-days.csv`.
- These tables have no engaged views before June 15, 2026, so use subscribers per 1,000 views, and list any videos whose subscriber totals differ from `data/demo-data.csv`.
