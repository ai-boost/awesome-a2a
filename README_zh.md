<div align="center">
  <h2 align="center">✨ Awesome A2A (Agent2Agent 协议) ✨</h2>
  <p align="center">
    <img src="assets/banner.png" alt="Awesome A2A 横幅 - 抽象网络或连接图形" width="600">
  </p>
  <p>
      <a href="README.md">English</a> | <a href="README_zh.md">简体中文</a>
      <!-- 在此添加其他语言链接，例如： | <a href="README_de.md">Deutsch</a> -->
  </p>
  <p align="center">
     一个精选列表，包含与 Google Agent2Agent (A2A) 协议相关的优质资源、实现、工具和示例，助力 AI Agent 互操作。
  </p>
  <h4 align="center">
    <a href="https://awesome.re">
      <img src="https://awesome.re/badge.svg" alt="Awesome" />
    </a>
    <a href="CONTRIBUTING.md"> <!-- 链接到贡献指南 -->
      <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square" alt="欢迎提交 PR" />
    </a>
  </h4>
</div>

---

## 目录

*   [🤔 什么是 A2A？ (简介)](#-什么是-a2a-简介)
*   [💡 核心原则](#-核心原则)
*   [⚙️ A2A 如何工作？ (概览)](#️-a2a-如何工作-概览)
*   [🚀 开始使用 A2A](#-开始使用-a2a)
*   [🏛️ 官方资源](#️-官方资源)
*   [📜 规范与核心概念](#-规范与核心概念)
*   [⚙️ 实现与库](#️-实现与库)
    *   [官方示例](#官方示例)
    *   [框架集成 (官方示例)](#框架集成-官方示例)
    *   [社区实现](#社区实现)
*   [🛠️ 工具与实用程序](#️-工具与实用程序)
*   [📚 教程与文章](#-教程与文章)
*   [🎬 Demo 与示例](#-demo-与示例)
*   [🔗 相关协议与概念](#-相关协议与概念)
*   [💬 社区](#-社区)
*   [贡献](#贡献)

---

## 🤔 什么是 A2A？ (简介)

A2A (Agent2Agent) 是由 Google 及众多合作伙伴发起的一个**开放协议**，旨在让**不同的 AI Agent**（可能来自不同供应商或使用不同框架）能够**安全地通信**并**协作完成任务**。它的目标是打破孤立 Agent 系统之间的壁垒，实现更复杂的跨应用自动化。

**⭐ 官方网站:** [google.github.io/A2A](https://google.github.io/A2A) | **⭐ 官方 GitHub:** [github.com/google/A2A](https://github.com/google/A2A)

## 💡 核心原则

*   **简洁 (Simple):** 利用并复用现有的、广泛采用的标准（HTTP, JSON-RPC, SSE）。
*   **企业级就绪 (Enterprise Ready):** 关注认证、安全、隐私、监控等企业级需求。
*   **异步优先 (Async First):** 处理长时间运行的任务和包含人机交互的场景。
*   **模态无关 (Modality Agnostic):** 支持文本、文件、表单、流等多种数据类型。
*   **不透明执行 (Opaque Execution):** Agent 交互时无需共享内部逻辑或工具。

## ⚙️ A2A 如何工作？ (概览)

1.  **发现 (Discovery):** Agent 发布 `Agent Card` (JSON 文件)，描述其能力、端点和认证要求。
2.  **通信 (Communication):** `客户端 (Client)` Agent 使用 HTTP/JSON-RPC 2.0 向 `远程 Agent (服务器 Server)` 发送 `Task` 请求（包含带有 `Part` 的 `Message`）。
3.  **执行与响应 (Execution & Response):** 服务器处理任务，更新 `status` 状态。最终响应包含最终状态和生成的 `Artifact` (结果，也包含 `Part`)。
4.  **更新 (Updates):** 对于长任务，服务器可以选择通过 SSE 流式传输 `TaskStatusUpdateEvent` 或 `TaskArtifactUpdateEvent`，或使用推送通知 (Push Notifications) 进行状态更新。

*欲了解详情，请参阅 [官方技术文档](https://google.github.io/A2A/#/documentation)。*

---

## 🚀 开始使用 A2A

刚接触 A2A？这里是建议的入门路径：

1.  **理解基础：** 阅读上方章节 ([什么是 A2A?](#-什么是-a2a-简介), [核心原则](#-核心原则), [如何工作?](#️-a2a-如何工作-概览))。阅读 📰 [官方发布博文](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) (英文)。
2.  **探索核心概念：** 深入阅读 📖 [官方技术文档](https://google.github.io/A2A/#/documentation)，重点关注 `Agent Card`、`Task`、`Message`、`Part` 和 `Artifact`。
3.  **观看演示：** 观看 🎥 [官方 Demo 视频](https://storage.googleapis.com/gweb-developer-goog-blog-assets/original_videos/A2A_demo_v4.mp4)，并探索 🌐 [多 Agent Web 应用 Demo](https://github.com/google/A2A/tree/main/demo) 的代码。
4.  **运行示例：** 克隆 [官方仓库](https://github.com/google/A2A)，并按照 `/samples` 目录中的说明运行一个客户端（如 CLI）和一个示例 Agent（如 LangGraph 或 Genkit Agent）。请参考下方的 [官方示例](#官方示例) 表格获取链接。
5.  **查阅代码：** 查看官方示例中的 `common` (Python) 或 `server`/`client` (JS/TS) 库，了解 A2A 通信是如何实现的。
6.  **动手尝试：** 修改一个官方示例 Agent 来执行新的简单任务，或者尝试用你喜欢的语言构建一个基本的 A2A 客户端，与示例 Agent 通信。

---

## 🏛️ 官方资源

*   📄 [A2A 协议网站](https://google.github.io/A2A) - 主要文档站点。
*   💻 [google/A2A GitHub 仓库](https://github.com/google/A2A) - 规范、文档和官方示例的源代码。
*   📰 [Google 开发者博客文章](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) - 宣告博文，解释动机和合作伙伴 (英文)。

## 📜 规范与核心概念

*(关于核心概念的摘要，请参见上文 [A2A 如何工作？](#️-a2a-如何工作-概览))*

*   📖 [A2A 技术文档](https://google.github.io/A2A/#/documentation) - **(完整细节)** 对参与者、传输、认证、核心对象（Task, Artifact, Message, Part）、Agent Card 等的详细解释。
*   📄 [JSON 规范](https://github.com/google/A2A/tree/main/specification/json) - A2A 结构的原始 JSON Schema 定义。
*   💡 [核心原则 (文档)](https://google.github.io/A2A/#/documentation?id=key-principles) - 指向官方文档中原则部分的链接。
*   🃏 [Agent Card 规范 (文档)](https://google.github.io/A2A/#/documentation?id=agent-card) - 指向官方文档中 Agent Card 部分的链接。
*   🗺️ [Agent 发现 (主题)](https://google.github.io/A2A/#/topics/agent_discovery.md) - 关于客户端如何找到 Agent Card 的讨论。
*   🔔 [推送通知 (主题)](https://google.github.io/A2A/#/topics/push_notifications.md) - 推送通知机制的详细信息。
*   🛡️ [企业级就绪 (主题)](https://google.github.io/A2A/#/topics/enterprise_ready.md) - 关于安全性、认证、隐私等方面的讨论。

## ⚙️ 实现与库

#### 官方示例

*这些示例展示了基本的 A2A 客户端/服务器通信。*

| 语言       | 类型             | 框架        | 描述                                          | 链接                                                                              |
| :--------- | :--------------- | :---------- | :-------------------------------------------- | :-------------------------------------------------------------------------------- |
| 🐍 Python  | 通用库           | -           | 核心 HTTP, JSON-RPC, SSE 处理                | [链接](https://github.com/google/A2A/tree/main/samples/python/common)             |
| 🐍 Python  | 主机 (客户端)    | CLI         | 命令行客户端示例                              | [链接](https://github.com/google/A2A/tree/main/samples/python/hosts/cli)          |
| 🐍 Python  | 主机 (Agent)     | ADK         | 委托任务给其他 A2A Agent 的编排器 Agent        | [链接](https://github.com/google/A2A/tree/main/samples/python/hosts/multiagent)   |
| 🚀 JS/TS   | 服务端库         | Express     | 核心服务器实现                                | [链接](https://github.com/google/A2A/tree/main/samples/js/src/server)             |
| 🚀 JS/TS   | 客户端库         | -           | 客户端实现                                    | [链接](https://github.com/google/A2A/tree/main/samples/js/src/client)             |
| 🚀 JS/TS   | 主机 (客户端)    | CLI         | 命令行客户端示例                              | [链接](https://github.com/google/A2A/blob/main/samples/js/src/cli.ts)             |

#### 框架集成 (官方示例)

*这些示例展示了使用特定框架构建的 Agent 如何提供 A2A 接口。*

| 语言       | Agent 框架      | Agent 描述                                | 关键 A2A 特性展示                     | 链接                                                                           |
| :--------- | :-------------- | :------------------------------------------ | :-------------------------------------- | :----------------------------------------------------------------------------- |
| 🐍 Python  | LangGraph       | 货币转换                                    | 工具使用, 流式传输, 多轮交互          | [链接](https://github.com/google/A2A/tree/main/samples/python/agents/langgraph) |
| 🐍 Python  | CrewAI          | 图像生成                                    | 非文本 Artifacts (文件)             | [链接](https://github.com/google/A2A/tree/main/samples/python/agents/crewai)   |
| 🐍 Python  | Google ADK      | 费用报销                                    | 多轮交互, 表单 (DataPart)             | [链接](https://github.com/google/A2A/tree/main/samples/python/agents/google_adk)|
| 🚀 JS/TS   | Genkit          | 电影信息 / 代码生成                         | 工具使用, Artifacts (文件), 异步     | [链接](https://github.com/google/A2A/tree/main/samples/js/src/agents)          |

#### 社区实现

*   🌟 _你的框架/语言 A2A 服务端/客户端库?_ - 添加到这里！请查看 [CONTRIBUTING.md](CONTRIBUTING.md)。
*   <!-- TODO: 添加社区实现 -->

## 🛠️ 工具与实用程序

*   🔍 *Agent 发现服务* - [链接] - 描述 (例如，'Agent Catalog' 的实现)。 <!-- TODO -->
*   ✅ *A2A 验证工具* - [链接] - 用于检查 A2A 端点合规性的工具。 <!-- TODO -->
*   📊 *监控/追踪适配器* - [链接] - 与可观察性平台的集成。 <!-- TODO -->

## 📚 教程与文章

*   📄 [官方 A2A 概念概览 (README)](https://github.com/google/A2A#conceptual-overview) - 官方仓库 README 中的高级解释。
*   🚀 [官方入门指南 (README)](https://github.com/google/A2A#getting-started) - 官方仓库 README 中指向文档、规范、示例的链接。
*   ✍️ *[博客文章/教程标题]* - [链接] - 描述。 <!-- TODO: 添加社区文章/指南 -->

## 🎬 Demo 与示例

*   🌐 [官方多 Agent Web 应用 (Python/Mesop)](https://github.com/google/A2A/tree/main/demo) - 展示编排器 Agent 与多个远程 Agent 交互，渲染文本、图像和表单。**需要运行 Python 代码。**
*   🎥 [官方 Demo 视频 (章节链接)](https://github.com/google/A2A#see-a2a-in-action) - 指向官方仓库 README 中嵌入视频的链接。

## 🔗 相关协议与概念

*   📦 [Model Context Protocol (MCP)](https://github.com/modelcontextprotocol/servers) - 互补协议，专注于向 Agent 提供工具/上下文。 ([A2A 与 MCP 讨论](https://google.github.io/A2A/#/topics/a2a_and_mcp.md)).
*   📞 *Function Calling / 工具使用标准* - [链接] - 相关标准 (例如，OpenAI function calling)。 <!-- TODO -->

## 💬 社区

*   🐞 [google/A2A GitHub Issues](https://github.com/google/A2A/issues) - 用于报告 Bug 或建议协议改进。
*   🔒 [私密反馈表单](https://docs.google.com/forms/d/e/1FAIpQLScS23OMSKnVFmYeqS2dP7dxY3eTyT7lmtGLUa8OJZfP4RTijQ/viewform) - 用于私密反馈的 Google 表单。

---

## 贡献

欢迎贡献！ 🙌 请先阅读 [贡献指南](CONTRIBUTING.md)。让我们一起构建这个列表！