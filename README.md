# Reddit heat

Static demo dashboard of hot Reddit posts about AI agents / agent tools (snapshot from 2026-10-02).

**Live:** [https://plutunieer.github.io/reddit-heat/](https://plutunieer.github.io/reddit-heat/)

## Open locally

Open `index.html` (or `reddit-dashboard.html`) in any browser. No build step. Data is embedded in the HTML; `reddit-dashboard.json` is the same snapshot for reuse.

```bash
# optional local server
python3 -m http.server 8080
# then visit http://localhost:8080/
```

## What this is

A read-only heat table of ~30 posts (score, comments, subreddit, title) scraped for an Agent-Reach evaluation run. Includes a short walkthrough video and poster screenshot.

## How the data was collected

1. Tried [Agent-Reach](https://github.com/Panniantong/Agent-Reach) for the Reddit channel.
2. **Agent-Reach needed login** — Reddit has no zero-config anonymous path in that stack (OpenCLI browser session or `rdt-cli` + cookie). Direct Reddit `.json` endpoints returned HTTP 403 from the demo network.
3. **Fallback:** [Scrapling](https://github.com/D4Vinci/Scrapling) `StealthyFetcher` against a public [Redlib](https://github.com/redlib-org/redlib) instance (`redlib.nadeko.net`), read-only HTML listings/search.

See `REPORT.md` and `agent-reach-doctor.txt` for details.

## Disclaimer

Not affiliated with the Agent-Reach authors beyond trying their stack for this demo. Not affiliated with Reddit. Snapshot only; metrics are not live. No posts or comments were written to Reddit.

## Files

| File | Purpose |
|------|---------|
| `index.html` | Dashboard (GitHub Pages entry) |
| `reddit-dashboard.html` | Same dashboard (alternate name) |
| `reddit-dashboard.json` | Structured snapshot |
| `REPORT.md` | Collection notes / blockers |
| `reddit-dashboard-poster.png` | Poster frame |
| `reddit-dashboard-walkthrough-2026-10-02.mp4` | Short walkthrough |
| `reddit-walkthrough-contact.png` | Contact/end frame |
