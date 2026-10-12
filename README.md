# ClauseGuard AI · 合同风险卫士（InfiniSynapse 驱动）

一个**构建在 InfiniSynapse 数据智能体之上的**合同风险分析 Web 应用。用户粘贴合同文本，
后端通过 InfiniSynapse Server API 发起分析任务（SSE + `newTask`），由智能体识别高风险条款、
用大白话解释并给出修改建议；前端实时展示流式结果。

> 参赛作品 · 演示用途 · 非法律意见。

## 架构（符合 InfiniSynapse Vibe Coding 官方规范）

```
浏览器 -> 本应用后端 (app.py) -> InfiniSynapse Adapter (infini.py) -> InfiniSynapse Server API
                                  -> 本地离线兜底引擎 (fallback.py)
```

- **API Key 仅存于服务端**，前端永不直接调用 InfiniSynapse（官方硬性要求）。
- 先连 SSE 事件流，再发 `newTask`（顺序不可颠倒）。
- 零第三方依赖：**纯 Python 标准库**（`urllib` + `http.server`），任何环境可直接运行。

## 运行

```bash
# 设置你的 InfiniSynapse API Key（海外 .com 账号）
export INFINI_KEY="sk-xxxx"
python app.py
# 打开 http://localhost:8000
```

不设置 `INFINI_KEY` 也能跑：应用会自动切换到**离线规则扫描兜底**，保证始终可演示。

## 与 InfiniSynapse 的集成点（参赛准入要求）

按比赛要求，本应用**通过 Server API 编程式地**：

1. **发起分析任务** — `POST /api/ai/message`（type=newTask），并以 SSE 订阅 `/api/ai/events` 接收实时结果；
2. **管理上下文/数据源** — 通过 `GET /api/ai_database/list`、`/api/ai_rag_sdk` 查询并启用数据库/RAG 知识库；
3. **拉取结果** — `GET /api/ai_task/getUiMessageById`、`/api/ai_task/getTaskWorkspace` 获取结构化分析与产物。

详见 `infini.py`。

## 文件结构

| 文件 | 作用 |
|---|---|
| `app.py` | 零依赖 HTTP 服务 + 路由 + 前端托管 |
| `infini.py` | InfiniSynapse Server API Adapter（SSE、任务、结果、重试、代理兼容） |
| `fallback.py` | 离线规则兜底引擎（API 不可用时保证可运行） |
| `index.html` | 单页前端（粘贴合同 → 实时分析 → 风险报告） |

## 提交信息（Submission）

- **App 名称**：ClauseGuard AI — 合同风险卫士
- **用例**：帮助企业/个人在签署合同前快速识别自动续约、单方改条款、责任限制、宽泛赔偿、
  个人担保、IP 归属、竞业等高风险条款，降低法律踩坑概率。
- **集成说明**：后端经 InfiniSynapse Server API 编程式发起分析任务并拉取产物；
  Key 留存服务端，前端只与本应用后端通信。
- **仓库**：https://github.com/Zhiyilang/clauseguard-ai
