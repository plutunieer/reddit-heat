# Agent-Reach Reddit demo — REPORT

**Generated:** 2026-10-02 07:52 CEST (Europe/Zurich)  
**User-facing outputs:**
- `/workspace/agent-reach-demo/reddit-dashboard.html`
- `/workspace/agent-reach-demo/reddit-dashboard.json`

## What ran

1. Cloned [Panniantong/Agent-Reach](https://github.com/Panniantong/Agent-Reach) → `/workspace/agent-reach`.
2. Installed package in a local venv (`/workspace/agent-reach/.venv`) and ran `agent-reach doctor`.
3. Reddit channel status: **not usable** without login. Docs state there is **no zero-config path** (anonymous `.json` blocked; backends are OpenCLI browser session or `rdt-cli` + Cookie). No `~/.config/rdt-cli/credential.json` and no OpenCLI Reddit session on this box.
4. Attempted documented public endpoints `www.reddit.com/.../.json` and `old.reddit.com/.../.json` → **HTTP 403** (datacenter IP / anti-bot). Jina Reader also blocked (AS reputation).
5. **Fallback used (authorized by task):** [Scrapling](https://github.com/D4Vinci/Scrapling) `StealthyFetcher` against public Redlib instance `https://redlib.nadeko.net` (read-only HTML listings/search).

## Topic

AI tools / agent culture — Redlib queries:
- `/search/?q=AI+agent+tools&sort=hot&t=week`
- `/search/?q=AI+agents&sort=top&t=week`
- `/r/LocalLLaMA/hot`, `/r/ClaudeAI/hot`, `/r/MachineLearning/hot`

Selected **30** unique posts (preferring search hits, filled from community hot lists), sorted by score.

## Totals (scraped)

| Metric | Value |
|--------|------:|
| Posts | 30 |
| Unique subreddits | 23 |
| Sum score | 59,846 |
| Sum comments | 9,192 |
| Max score | 12,364 |
| Posts with score | 30 |
| Posts with comment count | 29 |

## Top 5 by score

1. **Q: Who should be held accountable when the AI agents commit a crime? | Trump: It's not AI. It's SI. We changed the name officially today** — r/ChatGPT · score 12364 · comments None · https://www.reddit.com/r/ChatGPT/comments/1wu1w1q/q_who_should_be_held_accountable_when_the_ai/
2. **The personal AI agent horror stories are rolling in** — r/technology · score 5207 · comments 745 · https://www.reddit.com/r/technology/comments/1wppgtp/the_personal_ai_agent_horror_stories_are_rolling/
3. **FTC chair suggests AI developers should be liable for conduct of agents** — r/technology · score 3498 · comments 190 · https://www.reddit.com/r/technology/comments/1wrihsr/ftc_chair_suggests_ai_developers_should_be_liable/
4. **FTC chair suggests AI developers should be liable for conduct of agents** — r/Futurology · score 3102 · comments 110 · https://www.reddit.com/r/Futurology/comments/1wqjyoj/ftc_chair_suggests_ai_developers_should_be_liable/
5. **To ask who should be held accountable when the AI agents commit a crime?** — r/therewasanattempt · score 2658 · comments 462 · https://www.reddit.com/r/therewasanattempt/comments/1wua35u/to_ask_who_should_be_held_accountable_when_the_ai/

## Blockers

- Agent-Reach Reddit: requires credentials / browser login we do not have.
- Direct Reddit JSON / RSS: 403 from this network.
- Pullpush / Arctic Shift archives: rate-limited or unusable for this agent IP.
- One top post has `comments_count: null` because Redlib HTML omitted a parseable comment count for that card; score was present and is shown as scraped.

## Constraints honored

- Read-only network use; no Reddit posts/comments/writes.
- No invented metrics (nulls left null where HTML lacked a field).
