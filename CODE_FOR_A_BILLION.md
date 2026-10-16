# Code for a Billion — Entry Pack (Track 07: Timely Justice / Legal Backlog)

> 赛事官方规则已从官网核实（2026-10-16）：https://codeforindia.org/hackathon
> 主办方 Code for India（硅谷 501(c)(3)，Karl Mehta 创立，NASSCOM FutureSkills Prime 为知识伙伴）

## 赛事硬事实（官方原文，非二手）

| 项 | 官方规则 |
|---|---|
| 资格 | **"Anyone, anywhere on Earth"**（官网 FAQ）——中国可参加，已核实 |
| 费用 | 免费；注册 AgentFoundry.me（官方 IDE）建项目即参赛，送 1M smart-code tokens |
| 截止 | **2026-11-15 部署+开源**；12-05 公布获奖 |
| 奖金 | 每赛道 1st ₹1,50,000(≈¥12.7k) / 2nd ₹1,00,000(≈¥8.5k) / 3rd ₹50,000(≈¥4.2k)；总池 ₹18 lakh |
| 提交物 | 公开 GitHub repo + README + 2–3 分钟 demo 视频（或 live link）+ GitHub issue 表单提交 |
| 开源 | **Apache-2.0 或 MIT，开源到 Code for India GitHub organization**（保留贡献者署名） |
| 评分 | 4×25%：问题规模 / 问题严重性 / 方案质量 / **已证实的部署影响**（要部署数据，不要意图） |
| 赞助专项 | "Best Use of AgentFoundry Agents"、"Best xSpan CareHub Integration" |

## 赛道选择：Track 07「Timely Justice — Legal Backlog」

官方赛道描述：*Case triage, document summarisation, legal aid access, court scheduling efficiency.*

**ClauseGuard 的四项能力与该赛道逐条对应**：
- document summarisation → 逐条款引用 + 大白话风险解释（双语）
- case triage → 0–100 量化风险评分，自动标出高风险条款（先看最危险的）
- legal aid access → 免费、零依赖、无 LLM key 也能跑的离线规则引擎（法援对象往往没有 API 预算）
- （延伸）court scheduling / 合同纠纷 → 合同类纠纷是民事诉讼最大来源之一，帮双方在签约时看到风险=减少未来的法庭积案

## 问题陈述（README 用，评分前两项 50% 权重在此）

> **Problem.** India's courts carry one of the world's largest backlogs — on the order of **tens of millions of pending cases**（提交前以最新 NJDG/官方数据核定具体数字并标注来源，勿用未经核实的精确值）。A large share of civil litigation originates in contract disputes that non-lawyers signed without understanding: auto-renewal traps, unlimited indemnity, one-sided non-refundable clauses. Legal-aid beneficiaries — the people the backlog hurts most — rarely reach a lawyer before signing, and cannot afford per-document LLM API budgets.
>
> **Solution.** ClauseGuard AI is an autonomous contract-risk agent. A user pastes a contract (English or Chinese); the agent returns every high-risk clause **quoted verbatim**, a plain-language explanation of the harm, a concrete fix, and a quantified 0–100 risk score — bilingual, with **assertion-tested score parity** between languages. Its offline rule engine means it runs with **zero cost and zero API key**, which is exactly the constraint legal-aid access requires.

## 四维评分映射（README / demo 脚本要主动提供"证据"）

| 评分维度 | ClauseGuard 对应证据 |
|---|---|
| 问题规模 25% | 合同纠纷基数 + 法援覆盖面（README 放可核实数据源） |
| 严重性 25% | 无理解签约 → 直接金钱损失/诉讼；用 `examples/sample_contract.txt` 的真实陷阱条款演示 |
| 方案质量 25% | 36/36 断言（双语一致性、评分单调性、引用可解析）；CI 绿；零依赖 |
| 已证实影响 25% | **必须真部署**：Render/任意云活链接 + demo 视频 + 部署后 /healthz 探针记录 |

## 提交清单（用户动作已标注）

- [ ] 用户注册 https://agentfoundry.me 建项目（免费，送 1M tokens）
- [ ] AI 建参赛专用仓 `clauseguard-justice`（**不要转现有主力仓**——CFI 要求开源进其 org；专用仓基于 ClauseGuard 派生，MIT）
- [ ] README 问题陈述按上节写入，附评分四维证据
- [ ] 2–3 分钟 demo（现有 `clauseguard_demo.mp4` 30s 可复用/扩写；或录 live link 走查）
- [ ] 部署到云（Render 免费档，沿用 app.py + PORT + /healthz 模式）
- [ ] 11-15 前：GitHub issue 表单提交（模板 submission.yml 在 karlmehta/code-for-a-billion 仓）

## 已知风险 / 待验证项

1. AgentFoundry.me 国内网络可达性未知——用户注册时试；若不可达，规则说项目"built in AgentFoundry IDE"是官方建议路径，提交实质看 GitHub repo+部署（以 Discussions Q&A 区确认为准，发问模板见下）。
2. 开源进 CFI org 的操作方式（transfer vs fork）——提交前在官方 Discussions 区确认。
3. 问题规模数字必须用可引用来源，宁可保守。

### 官方 Discussions 区确认问题模板（英文，可直接发）

```
Hi CFI team — two rules clarifications, please:
1. Our project's primary repo will live on our own GitHub org with a public
   Apache-2.0 licence, and we will also push a copy under the Code for India
   GitHub organization before the Nov 15 deadline. Is that the expected
   "released to CFI org" flow, or do you require an org transfer?
2. AgentFoundry.me is unreachable from our region (mainland China). The
   judging criteria state deployment to "any cloud" — can our project be
   developed outside the AF IDE and still be judged on the repo + deployed
   link? Happy to import the repo into AF if access is restored.
```
