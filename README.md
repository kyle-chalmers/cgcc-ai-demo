# Which video topic should I make next?

The demo repo from Kyle Chalmers' CGCC Entrepreneurship Series talk, "Turning the questions your business is asking into answers you can act on with AI" (October 20, 2026). It shows how to put an AI coding agent to work on real business data in a way you can check.

## What's here

- `data/demo-data.csv`: one row per YouTube video published from 2026-01-01 through 2026-07-19 (23 full-length videos and 107 Shorts). Each row covers that video's first 90 days after publishing, so every video gets the same amount of time. The numbers come from the YouTube Analytics API, and subscriptions are those made on each video's watch page.
- `CLAUDE.md`: the project rules the agent reads first. They are why the prompts can stay short.
- `prompts/`: the two prompts from the talk, one for the CSV and one that pulls from BigQuery.

## Try it

1. Clone this repo and open it in [Claude Code](https://claude.com/product/claude-code) (or another coding agent).
2. Paste `prompts/dashboard.txt`.
3. Open `live-dashboard.html` and check its totals against the CSV yourself.

To do the same with your own data, swap in your CSV and update `CLAUDE.md` to describe it. The BigQuery prompt needs your own warehouse and tables.

Slides and a one-page guide with an AI coach prompt: https://kclabs.ai/resources/cgcc
