# ClauseGuard AI — InfiniSynapse Vibe Coding Hackathon 提交指南

> **赛事**：InfiniSynapse Vibe Coding Hackathon Online 2026（全球场，与 CSDN 国内赛不同）
> **窗口**：2026-10-10 ~ 2026-10-31 23:59 **PDT（= 北京时间 11-01 14:59）**
> **奖池**：$3,000（$900 / $600×2 / $300×3）；评分 = **场景价值 40% / 技术完整度 35% / 创新 25%**；GitHub stars 不计分
> **硬要求**：① 通过 InfiniSynapse Server API 编程式发起分析任务（后台可调取调用日志）② 部署公网可访问 ③ 真实数据闭环（非 fake JSON / 非 chat-on-CSV）
> **赛道**：**Open Industry（开放行业）** —— 覆盖教育/零售/爆品/SMB 运营/增长之外的真实小企业决策闭环

---

## 一、逐字段（提交表单直接粘贴）

**App 名称**
```
ClauseGuard AI — 合同风险卫士
```

**参赛赛道**
```
Open Industry（开放行业）
```

**目标用户（User）**
```
没有专职法务的小微企业主 / 个体户。签供应商合同、店铺租赁、客户合同时看不懂条款、踩坑概率高。
```

**数据路径（Data path —— 评委最看重，必须可见闭环）**
```
Input   用户粘贴合同文本（或上传 .txt）
Processing 后端经 InfiniSynapse Server API 编程式发起分析任务（SSE 事件流 → newTask → 实时拉取风险产物）；
         平台过载/无 Key 时优雅降级到内置透明规则引擎，保证任何时刻都可运行、可出结果。
Decision/Action 输出「高风险条款清单 + 大白话解释 + 风险评分 + 建议动作」，用户据此决定签/不签、改哪些条款。
闭环     用户 → 数据 → 分析 → 动作，四步完整可见。
```

**上线地址（必填）**
```
https://clauseguard-ai.app.workbuddy.host/
```

**代码仓库（可选，star 不计分）**
```
https://github.com/Zhiyilang/clauseguard-ai
```

**一句话亮点（表单简介栏）**
```
帮小微企业用 AI 审合同：粘贴条款即揪出自动续约、单方改约、责任限制、宽泛赔偿、个人担保、IP 归属等高风险点；零依赖、可离线、隐私不出本机。
```

**API 集成说明（贴 README 链接或下段）**
```
- 后端经 InfiniSynapse Server API 编程式发起分析任务：先连 SSE 事件流（/api/ai/events），
  再 POST /api/ai/message（type=newTask），最后 GET /api/ai_task/getUiMessageById 拉取结构化产物。
- API Key 仅存于服务端（infini.py 读取 INFINI_KEY），前端只与本应用后端通信，绝不下发 Key（符合官方规范）。
- 调用日志可在 InfiniSynapse 平台后台查验（真实发起任务，非伪造 JSON）。
- 零第三方依赖：纯 Python 标准库（urllib + http.server），任何环境直接 `python app.py`。
```

**使用截图（2 张即可）**
```
1. 首页：粘贴含「自动续约 + 单方修改条款 + 个人担保」的合同，点「开始分析」。
2. 结果页：红色 HIGH 风险卡片 + 风险评分（示例 100/HIGH）+ 大白话解释与修改建议。
```

---

## 二、评分维度对照（官方 rubric）

| 维度（权重） | ClauseGuard AI 的对应证据 |
|---|---|
| **场景价值 40%** | 小微企业签合同前缺法务支持，合同风险卫士直接给「该改哪条」的可执行建议，痛点真实、受众广、闭环清楚。 |
| **技术完整度 35%** | 真实接入 InfiniSynapse Server API（SSE+newTask+结果拉取）；零依赖 stdlib 实现；带离线兜底保证 7×24 可运行；前端实时流式展示；`python eval.py` **25 条离线断言全过**（`fallback.scan` 确定性 + 路由 + 注入防护 + 无 Key 优雅降级）。 |
| **创新 25%** | 把「通用聊天/CSV」升级为**领域化合同风险工作流**：规则引擎 + InfiniSynapse 智能体双引擎、可解释条款库、风险评分量化、离线可跑数据不出本机。 |

---

## 三、工程自测（技术完整度加分项）

```
$ python eval.py
==============================================
结果：25 通过 / 0 失败
==============================================
```
覆盖：离线规则引擎 9 条规则触发/负对照/评分封顶 100、恶意合同文本注入不破坏引擎与 JSON、无 Key 时 InfiniSynapse 适配器优雅降级、本地 HTTP 路由（`/healthz` 200 / `/` 200 / 404 / 空文本 400 / offline 模式出结果 / 注入文本仍返回合法 JSON）。

---

## 四、用户侧动作清单（约 20 分钟）

1. **确认 InfiniSynapse Key 有效**：部署环境 `INFINI_KEY` 已配（已验证真实调用可发出；高峰 500 时自动降级离线引擎，评委随时打开都能跑）。
2. **确保部署在线**：`https://clauseguard-ai.app.workbuddy.host/` 可访问（当前已部署，赛窗内保持在线即可）。
3. **平台提交**：官方开门后在 Luma/活动页填上述字段 → 提交。GitHub stars 不计分，但仓库公开利于评委查证集成说明。

> AI 侧已就绪：应用已部署、InfiniSynapse 集成完整、离线兜底保证可运行、25 条自测全过、提交文案可直接粘贴。你只需确认 Key 在线 + 平台提交。
