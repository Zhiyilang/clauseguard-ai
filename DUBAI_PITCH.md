# ClauseGuard AI — Pitch Deck Outline
### Create AI Agents Championship · Dubai Chamber of Digital Economy
**Category: Best Societal AI Agent** · Prepared October 2026 · All-English entry

> Prize: AED 550,000 per category winner + AED 1,000,000 "AI Agent of the Year".
> Total pool > AED 2.5M (~US$680k). Registration closes December 2026.
> Grand final (first week of May 2027) requires a **fully working agent demonstrated live** — not an MVP.

---

## Slide 1 — Title
**ClauseGuard AI — the contract-risk guardian for people who can't afford a lawyer**
- An autonomous agent that reads a contract, flags high-risk clauses, explains each risk in plain language, and tells you exactly what to change.
- Tagline: *"Agents propose. Evidence decides. You sign informed."*
- Built by a one-person team; open-source, zero-dependency, bilingual (EN/中文).

## Slide 2 — The problem
- Micro and small businesses sign dozens of contracts a year (leases, supplier terms, service agreements, freelance NDAs) with **no legal review**.
- The dangerous clauses are invisible to non-lawyers: auto-renewal, unilateral amendment, broad indemnity, personal guarantees.
- Consequences fall hardest on people with the least cushion — a personal guarantee can consume an entrepreneur's family assets.
- Legal review costs hundreds of dollars per contract — out of reach exactly where the risk is highest.
- **This is an inclusion and economic-resilience problem**, not a convenience problem.

## Slide 3 — Why now
- Contract risk review was expert-only. LLM agents changed that — but raw chat gives unverifiable answers.
- What was missing: a **deterministic, explainable agent** that shows its work and never invents a risk.
- ClauseGuard pairs an LLM agent (InfiniSynapse Server API) with a deterministic bilingual rule engine — every finding carries a plain-language explanation and a concrete fix.

## Slide 4 — Meet ClauseGuard AI
- Paste a contract (Chinese or English) → risk score 0–100 → ranked findings (HIGH/MEDIUM/LOW) → plain-language explanation per clause → a specific suggested fix.
- Zero third-party dependencies (Python standard library only) — runs anywhere, auditable end-to-end.
- **Always-on**: if the LLM API is unavailable, the local rule engine takes over seamlessly, so the service never breaks.

## Slide 5 — Live demo (screenshots from the deployed instance)
1. Paste a one-page service agreement.
2. Score dial: 75 / HIGH.
3. Findings: Auto-renewal (HIGH), Unilateral change of terms (HIGH), Personal guarantee (HIGH).
4. Each finding: why it hurts you + the exact counter-language to request.
5. Toggle to English/中文 — full interface and findings switch language.

## Slide 6 — How it works (architecture)
```
Browser → app backend → InfiniSynapse agent (SSE + task API)   [primary path]
                     → offline bilingual rule engine            [resilience path]
```
- API key stays server-side; the browser never talks to the LLM provider directly.
- The rule engine is transparent: 10 clause families, deterministic regex matching, weighted scoring capped at 100 — no black box, no hallucinated risks.

## Slide 7 — The agent loop
PERCEIVE (contract text) → ANALYZE (agent + rules) → EXPLAIN (plain language, per clause) → ADVISE (concrete fix) → SCORE (quantified risk band). Every step is visible in the receipt the user keeps.

## Slide 8 — Engineering quality (proof it is real)
- **36/36 automated assertions pass** (`python eval.py`): detection accuracy, score capping, injection safety, bilingual parity (same contract scores identically in EN and ZH), graceful degradation.
- CI on three Python versions; MIT-licensed public repository.
- Real HTTP smoke-tested end to end.

## Slide 9 — Societal impact (category mapping)
- **Inclusion**: enterprise-grade contract review for people priced out of legal help.
- **Economic resilience**: prevents the single worst financial event for a small entrepreneur — a personal guarantee or open-ended indemnity.
- **Education**: every finding teaches the user *why* a clause is dangerous — financial literacy by use.
- **Sustainability of small business**: fewer disputes, fairer terms, longer-lived businesses.

## Slide 10 — Roadmap (what the grant funds)
- Phase 1 (grant months 1–3): Arabic UI + Gulf-contract clause library; pilot with a Dubai SME Chamber working group.
- Phase 2: document upload (PDF/DOCX), clause diffing against a "fair terms" baseline, browser extension.
- Phase 3: measured-outcome study — disputes avoided, money saved — published openly.

## Slide 11 — Path to scale (not a commercialised product today)
- Free tier for individuals; affordable SME subscription; B2B2C via chambers of commerce and banks' SME onboarding.
- **Eligibility note**: ClauseGuard is a pre-commercial, open-source prototype — it does not compete as a commercialised solution.

## Slide 12 — Team & the ask
- Solo founder (21, Shanghai): RPA/automation engineer turned AI-agent builder; shipped 10+ open-source agent projects.
- The ask: **AED 550,000 Best Societal AI Agent grant** to turn the prototype into a deployed, measured public good — and to prove an agent can protect the people least able to protect themselves.

---

## Judge Q&A prep
- *"Why not just use ChatGPT?"* — Chat gives unverifiable prose. ClauseGuard gives a deterministic, scored, explainable receipt with per-clause fixes, in two languages, with a resilient offline engine.
- *"Is it commercialised?"* — No. Open-source MIT prototype; grant funds the pilot and impact study.
- *"Can it demo live?"* — Yes: zero dependencies, offline-capable, deployed publicly.
- *"Measured impact?"* — Detection accuracy is assertion-tested; pilot outcome metrics are Phase-1 deliverables.
