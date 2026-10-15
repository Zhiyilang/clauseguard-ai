# ClauseGuard AI — Demo Video Script (Dubai entry)

> 🎬 **Base footage already produced**: `clauseguard_demo.mp4` (20.1s, real
> terminal run of `python demo.py` — bilingual scan of the sample contract,
> then the 36-assertion suite). Use it as the product-proof segment inside the
> 3-minute recording below, or as a fallback submission video.

**Target length: 3:00** · Language: English (championship requires English entries) · Format: screen recording + voiceover

---

## 0:00–0:25 — Hook (problem)
**[Screen: a plain-looking contract page, slowly scrolling]**

> "This is a one-page service agreement. It looks harmless. Buried in clause 7 is an
> auto-renewal. Clause 9 lets the other side change any term without telling you.
> And clause 12 asks *you personally* to guarantee the company's debts — with your
> family's assets. A lawyer would catch this in an hour. Most small business owners
> never get that hour."

## 0:25–0:55 — The agent at work
**[Screen: deployed ClauseGuard UI. Paste the same contract. Press Analyze.]**

> "ClauseGuard AI is an autonomous contract-risk agent. You paste the contract —
> in English or Chinese. It reads every clause, and returns a risk score,
> the dangerous clauses ranked by severity, and for each one: why it hurts you,
> and exactly what to change."

## 0:55–1:30 — Findings walkthrough
**[Screen: results panel. Score dial at 75/HIGH. Point at each finding.]**

> "Seventy-five out of one hundred — high risk. Three HIGH findings.
> Auto-renewal: it explains that you can be locked into another term without
> knowing, and tells you to require written confirmation for any renewal.
> Unilateral change: the fix — no amendment without written consent from both sides.
> Personal guarantee — the most dangerous one. The agent's advice is blunt:
> refuse it. The signing entity should carry the liability, not you."

## 1:30–1:55 — Explainability & bilingual
**[Screen: hover the score dial; click English/中文 toggle — interface and findings switch.]**

> "Nothing here is a black box. Every finding carries its plain-language explanation
> and a concrete counter-proposal. And the whole agent — interface and findings —
> switches between English and Chinese, because contract risk is not an
> English-only problem."

## 1:55–2:20 — Resilience & engineering proof
**[Screen: terminal — `python eval.py` → "36 passed / 0 failed". Then show the repo README.]**

> "Under the hood: an LLM agent on the InfiniSynapse Server API, paired with a
> deterministic bilingual rule engine. If the API is ever unavailable, the local
> engine takes over — the service never breaks. Thirty-six automated assertions
> verify detection, scoring, injection safety, and that the same contract scores
> identically in both languages. Zero third-party dependencies. MIT-licensed,
> public repository."

## 2:20–2:50 — Impact close
**[Screen: split — the risky contract on the left, the fixed contract on the right.]**

> "Small businesses sign contracts they can't read, with risks they can't see.
> ClauseGuard gives them the hour a lawyer would give them — for free, in their
> own language, with evidence for every warning. That's why we entered the
> Best Societal AI Agent category."

## 2:50–3:00 — End card
**[Screen: repo URL + "Agents propose. Evidence decides. You sign informed."]**

> "ClauseGuard AI. Agents propose. Evidence decides. You sign informed."

---

## Production notes
- Record at 1080p; UI is dark-themed — looks good on projector.
- Use a realistic sample contract (freelance service agreement), not lorem ipsum.
- Keep the score-dial and finding cards on screen for at least 3 seconds each — judges screenshot.
- Voiceover: calm, measured pace. No background music over speech.
- Upload unlisted to YouTube; title: "ClauseGuard AI — Contract Risk Guardian (Create AI Agents Championship, Best Societal AI Agent)".
