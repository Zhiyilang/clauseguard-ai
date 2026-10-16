# ClauseGuard AI — Dubai "Create AI Agents Championship" Entry Checklist
**Category: Best Societal AI Agent** · Entry language: English · Prepared 2026-10-15

---

## 1. Championship facts (verified against official announcements, Oct 2026)

| Item | Detail |
|---|---|
| Competition | Create AI Agents Championship, Dubai Chamber of Digital Economy (Dubai Chambers) |
| Announced | 7 October 2026 (successor to the Create Apps Championship) |
| Prize pool | > AED 2.5M (~US$680k): **AED 550,000 per category winner**; one winner also named **AI Agent of the Year (+AED 1,000,000)** |
| Categories | Best Societal / Best Personal / Best Business / **Best Youth (under 21 at registration — NOT eligible: applicant is 21)** |
| Eligibility | Open worldwide, individuals or teams up to 6, no minimum age; **fully commercialised solutions NOT eligible** |
| Registration | Open now; **closes January 2027 (official timeline + FAQ; press reported December — official page wins)** — dubaichamberdigital.com/en/create-ai-agents |
| Required deliverables | **AI-agent prototype + pitch deck + demo video**, all in English |
| Multiple entries | Allowed — you may file more than one application without re-registering |
| Support | 3 intro workshops (Oct–Nov); Digital Academy opens November (courses + mentorship) |
| Finalists | 12 finalists; semi-finalists/high-potential teams join a Tech Accelerator; finalists get Oraseya Capital Launchpad access |
| Grand final | First week of **May 2027** — finalists must demonstrate a **fully working agent live**, not an MVP |

## 2. Category choice: Best Societal AI Agent
Official framing: agents that strengthen **social cohesion and inclusion**, and support **education, sustainability and social resilience**.
ClauseGuard maps directly: enterprise-grade contract review for people priced out of legal help (inclusion), prevention of personal-guarantee disasters (economic resilience), and per-clause financial education (education).

> Strategic note: multiple entries are allowed. Secondary options later — **Best Personal AI Agent** (GardenPlanner: daily-life/wellbeing agent) and **Best Business AI Agent** (AirPilot: payment-ops incident commander). Do NOT enter Best Youth — applicant is 21, category requires under 21 at registration.

## 3. Deliverables mapping

| Required deliverable | Status | File / source |
|---|---|---|
| AI-agent prototype (public URL) | ✅ built & bilingual | https://github.com/Zhiyilang/clauseguard-ai (deployed instance — redeploy before submitting; see DEPLOY notes in repo) |
| Pitch deck | ✅ outline ready (12 slides) | `DUBAI_PITCH.md` — convert to slides (Google Slides/PowerPoint), keep all-English |
| Demo video (<3 min) | ✅ script ready | `DUBAI_DEMO_SCRIPT.md` — record per production notes, upload unlisted YouTube |
| Public repo + open-source licence | ✅ MIT, zero-dependency, 36/36 assertions, 3-version CI | README.md (English version needed for repo front page — see action A4) |

## 4. Applicant action list (in order)
- [ ] **A1. Register** at dubaichamberdigital.com/en/create-ai-agents (before January 2027 (earlier registration = workshop/Academy access); earlier = access to workshops/Academy materials). Confirm whether the submission window has opened on the platform — registering tells you when submissions open.
- [ ] **A2. Redeploy** the ClauseGuard instance (Render) so the live URL is healthy at submission time; verify the English toggle works on the deployed build.
- [ ] **A3. Record the demo video** per `DUBAI_DEMO_SCRIPT.md` (3 min, English, unlisted YouTube).
- [ ] **A4. Convert `DUBAI_PITCH.md` to a slide deck** (12 slides, English) — or ask the agent to produce an HTML/PPTX version.
- [ ] **A5. Submit** prototype URL + deck + video before the platform deadline; select **Best Societal AI Agent**.
- [ ] **A6 (optional, higher EV)** — file a second entry from another project once the primary is submitted (multiple entries allowed; see strategic note).

## 5. Judging criteria (per official process) → our coverage
1. **Identify a priority problem** → Slides 2–3: invisible contract risk for the under-served. ✅
2. **Design an agent to address it** → Slides 4–7: agent + deterministic engine, explainable receipt. ✅
3. **Test its impact** → Slide 8: 36/36 assertions, bilingual parity, HTTP smoke tests; pilot metrics in roadmap. ✅
4. **Path to scalable product/service/business** → Slides 10–11: grant-funded roadmap + freemium/B2B2C model, explicitly pre-commercial (eligibility-safe). ✅

## 6. Risks & mitigations
| Risk | Mitigation |
|---|---|
| Live final (May 2027) must be a **fully working agent**, not an MVP | Zero-dependency offline engine means the demo can never fail on network/API; roadmap phases funded by the grant deliver the production hardening |
| "Fully commercialised solutions not eligible" | Entry is explicitly framed as an open-source, pre-commercial prototype; the grant funds the pilot |
| Youth category confusion | We are 21 → only Societal/Personal/Business are open to us; youth is excluded by rule |
| Language | Entire entry (deck, video, UI) is English; the zh mode is an extra, not the entry |
