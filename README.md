# ClauseGuard AI · Contract Risk Guardian (powered by InfiniSynapse)

An autonomous **contract-risk agent**: paste a contract (English or Chinese), and the agent flags high-risk clauses, explains each risk in plain language, and gives a concrete fix — with a quantified 0–100 risk score.

> Demo · not legal advice.

**Now bilingual (EN / 中文)** — the whole interface and every finding switches language with one click. Bilingual parity is assertion-tested: the same contract scores identically in both languages.

## Contest entries
| Championship | Category | Status |
|---|---|---|
| **Dubai Create AI Agents Championship** (Dubai Chamber of Digital Economy, prize > AED 2.5M) | **Best Societal AI Agent** | entry pack ready — see `DUBAI_SUBMISSION.md` (checklist), `DUBAI_PITCH.md` (deck outline), `DUBAI_DEMO_SCRIPT.md` (3-min video script) |
| InfiniSynapse Vibe Coding Hackathon 2026 | Open Industry | see `SUBMISSION.md` |

## Architecture

```
Browser -> app backend -> InfiniSynapse Server API (SSE + newTask)   [primary]
                       -> offline bilingual rule engine              [resilience]
```

- **API key stays server-side**; the browser never calls the LLM provider directly.
- **Zero third-party dependencies** — pure Python standard library (`urllib` + `http.server`), runs anywhere, fully auditable.
- **Always runnable**: if the LLM API is unavailable, the local rule engine takes over seamlessly.

## Run

```bash
export INFINI_KEY="sk-xxxx"   # optional; without it the offline engine runs
python app.py
# open http://localhost:8000
```

## Try it in 30 seconds (no key needed)

1. `python app.py` and open http://localhost:8000
2. Copy the contents of [`examples/sample_contract.txt`](examples/sample_contract.txt)
   (a realistic freelance agreement with auto-renewal, indemnity and
   non-refundable clauses) and paste it into the textarea
3. Press **Analyze** — every finding quotes the clause, explains the risk in
   plain language, and gives a concrete fix. The same contract in English and
   Chinese returns the same 0–100 risk score (assertion-tested in `eval.py`).

Command-line equivalent (offline engine, no server, no key):

```bash
python demo.py    # scans examples/sample_contract.txt in EN + ZH, asserts parity
```

## Agent integration (InfiniSynapse Server API)

1. **Launch analysis** — `POST /api/ai/message` (type=newTask), subscribing to SSE on `/api/ai/events`;
2. **Manage context/data sources** — `GET /api/ai_database/list`, `/api/ai_rag_sdk`;
3. **Pull results** — `GET /api/ai_task/getUiMessageById`, `/api/ai_task/getTaskWorkspace`.

Details in `infini.py`.

## Files

| File | Role |
|---|---|
| `app.py` | zero-dependency HTTP server, routing, frontend hosting |
| `infini.py` | InfiniSynapse Server API adapter (SSE, tasks, results, retries) |
| `fallback.py` | offline bilingual rule engine (10 clause families, weighted score capped at 100) |
| `index.html` | single-page frontend with EN/中文 toggle |
| `eval.py` | **36 assertions, all passing** — detection, capping, injection safety, bilingual parity, degradation |
| `DUBAI_*.md` | Dubai championship entry pack (checklist / pitch / demo script) |

## Quality

```bash
python eval.py   # 36 passed / 0 failed — no network needed
```

CI runs the suite on Python 3.10 / 3.11 / 3.12. MIT licensed.

## Links
- Repository: https://github.com/Zhiyilang/clauseguard-ai
- 中文说明：[README.zh.md](README.zh.md)
