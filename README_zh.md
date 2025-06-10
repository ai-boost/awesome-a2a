<div align="center">
  <h2 align="center">✨ Awesome A2A (Agent2Agent 协议) ✨</h2>
  <p align="center">
    <img src="assets/banner.png" alt="Awesome A2A 横幅 - 抽象网络或连接图形" width="600">
  </p>
  <p>
      <a href="README.md">English</a> | <a href="README_zh.md">简体中文</a> | <a href="README_ja.md">日本語</a> | <a href="README_es.md">Español</a> | <a href="README_de.md">Deutsch</a> | <a href="README_fr.md">Français</a>
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
        *   [SDK 与库 (按语言分类)](#sdk-与库-按语言分类)
        *   [平台与集成解决方案](#平台与集成解决方案)
*   [🛠️ 工具与实用程序](#️-工具与实用程序)
*   [📚 教程与文章](#-教程与文章)
*   [🎬 Demo 与示例](#-demo-与示例)
*   [🔗 相关协议与概念](#-相关协议与概念)
*   [💬 社区](#-社区)
*   [贡献](#贡献)

---

## 🤔 什么是 A2A？ (简介)

A2A (Agent2Agent) 是由 Google 及众多合作伙伴发起的一个**开放协议**，旨在让**不同的 AI Agent**（可能来自不同供应商或使用不同框架）能够**安全地通信**并**协作完成任务**。它的目标是打破孤立 Agent 系统之间的壁垒，实现更复杂的跨应用自动化。

**⭐ 官方网站:** [google.github.io/A2A](https://google.github.io/A2A) | **⭐ 官方 GitHub:** [github.com/google/A2A](https://github.com/google/A2A) | 🌐 **多语言文档 (英/中/日):** [agent2agent.ren](https://agent2agent.ren)

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

*欲了解详情，请参阅 [官方技术文档](https://google-a2a.github.io/A2A/#/documentation)。*

---

## 🚀 开始使用 A2A

刚接触 A2A？这里是建议的入门路径：

1.  **理解基础：** 阅读上方章节 ([什么是 A2A?](#-什么是-a2a-简介), [核心原则](#-核心原则), [如何工作?](#️-a2a-如何工作-概览))。阅读 📰 [官方发布博文](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) (英文)。
2.  **探索核心概念：** 深入阅读 📖 [官方技术文档](https://google-a2a.github.io/A2A/#/documentation)，重点关注 `Agent Card`、`Task`、`Message`、`Part` 和 `Artifact`。
3.  **观看演示：** 观看 🎥 [官方 Demo 视频](https://storage.googleapis.com/gweb-developer-goog-blog-assets/original_videos/A2A_demo_v4.mp4)，并探索 🌐 [多 Agent Web 应用 Demo](https://github.com/google-a2a/A2A/tree/v0.2.1/demo) 的代码。
4.  **运行示例：** 克隆 [官方示例仓库](https://github.com/google-a2a/a2a-samples)，并按照其中的说明运行一个客户端（如 CLI）和一个示例 Agent（如 LangGraph 或 Genkit Agent）。
5.  **查阅代码：** 查看官方示例中的 `common` (Python) 或 `server`/`client` (JS/TS) 库，了解 A2A 通信是如何实现的。
6.  **动手尝试：** 修改一个官方示例 Agent 来执行新的简单任务，或者尝试用你喜欢的语言构建一个基本的 A2A 客户端，与示例 Agent 通信。

---

## 🏛️ 官方资源

*   📄 [A2A 协议网站](https://google.github.io/A2A) - 主要文档站点。
*   💻 [google/A2A GitHub 仓库](https://github.com/google/A2A) - 规范、文档和官方示例的源代码。
*   📰 [Google 开发者博客文章](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) - 宣告博文，解释动机和合作伙伴 (英文)。

## 📜 规范与核心概念

*(关于核心概念的摘要，请参见上文 [A2A 如何工作？](#️-a2a-如何工作-概览))*

*   📖 [A2A 技术文档](https://google-a2a.github.io/A2A/#/documentation) - **(完整细节)** 对参与者、传输、认证、核心对象（Task, Artifact, Message, Part）、Agent Card 等的详细解释。
*   📄 [JSON 规范](https://github.com/google-a2a/A2A/tree/main/specification/json) - A2A 结构的原始 JSON Schema 定义。
*   💡 [核心原则 (文档)](https://google-a2a.github.io/A2A/#/documentation?id=key-principles) - 指向官方文档中原则部分的链接。
*   🃏 [Agent Card 规范 (文档)](https://google-a2a.github.io/A2A/#/documentation?id=agent-card) - 指向官方文档中 Agent Card 部分的链接。
*   🗺️ [Agent 发现 (主题)](https://google-a2a.github.io/A2A/#/topics/agent_discovery.md) - 关于客户端如何找到 Agent Card 的讨论。
*   🔔 [推送通知 (主题)](https://google-a2a.github.io/A2A/#/topics/push_notifications.md) - 推送通知机制的详细信息。
*   🛡️ [企业级就绪 (主题)](https://google-a2a.github.io/A2A/#/topics/enterprise_ready.md) - 关于安全性、认证、隐私等方面的讨论。

## ⚙️ 实现与库

#### 官方示例

*这些示例展示了基本的 A2A 客户端/服务器通信。*

| 语言                | 示例名称                       | 一句话介绍                        | GitHub URL                                                                                                                                                                              |
| ----------------- | -------------------------- | ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🔷 **TypeScript** | Genkit SDK Core            | TS SDK + CLI，构建前后端共用代码       | [https://github.com/google-a2a/a2a-samples/tree/main/samples/js](https://github.com/google-a2a/a2a-samples/tree/main/samples/js)                                                        |
|                   | Movie Recommendation Agent | 基于 Genkit 的电影推荐对话 Agent      | [https://github.com/google-a2a/a2a-samples/tree/main/samples/js/src/agents/movie-agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/js/src/agents/movie-agent)                                |
|                   | TypeScript Client          | TS 编写的纯前端调用示例                | [https://github.com/google-a2a/a2a-samples/tree/main/samples/js/client](https://github.com/google-a2a/a2a-samples/tree/main/samples/js/client)                                          |
|                   | Node Express Server        | Node/Express 实现的 A2A HTTP 服务 | [https://github.com/google-a2a/a2a-samples/tree/main/samples/js/server](https://github.com/google-a2a/a2a-samples/tree/main/samples/js/server)                                          |
| ☕ **Java**        | Java Client Demo           | Java 客户端调用示例（含流式监听）          | [https://github.com/google-a2a/a2a-samples/tree/main/samples/java/client](https://github.com/google-a2a/a2a-samples/tree/main/samples/java/client)                                      |
|                   | Java Data Models           | 协议 POJO 数据模型全集               | [https://github.com/google-a2a/a2a-samples/tree/main/samples/java/model](https://github.com/google-a2a/a2a-samples/tree/main/samples/java/model)                                        |
|                   | Java Server Impl           | Spring Boot 版 A2A 服务端        | [https://github.com/google-a2a/a2a-samples/tree/main/samples/java/server](https://github.com/google-a2a/a2a-samples/tree/main/samples/java/server)                                      |
| 🐍 **Python**     | CLI Quickstart             | 终端一句命令体验 A2A 调用循环            | [https://github.com/google-a2a/a2a-samples/tree/main/samples](https://github.com/google-a2a/a2a-samples/tree/main/samples)                                                              |
|                   | Host Agent Service         | 托管并调度下游 Agent 的入口服务          | [https://github.com/google-a2a/a2a-samples/tree/main/samples/host\_agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/a2a-adk-app/host_agent)                                       |
|                   | Weather Agent              | 天气查询 Agent + HTTP 服务端        | [https://github.com/google-a2a/a2a-samples/tree/main/samples/weather\_agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/a2a-adk-app/weather_agent)                                 |
|                   | Minimal MCP                | 不依赖框架手写多-Agent 协调协议          | [https://github.com/google-a2a/a2a-samples/tree/main/samples/a2a-mcp-without-framework](https://github.com/google-a2a/a2a-samples/tree/main/samples/a2a-mcp-without-framework)          |
|                   | Travel Agency Agents       | 旅行社场景多 Agent 协同              | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/a2a_mcp)                                  |
|                   | A2A Telemetry              | 收集并展示 Agent 执行遥测数据           | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/a2a\_telemetry](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/a2a_telemetry)                   |
|                   | AG2 Mini-Demo              | 极简 A↔A 互调骨架                  | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/ag2](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/ag2)                                        |
|                   | Analytics Workflow         | 数据分析场景的多 Agent 编排            | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/analytics](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/analytics)                            |
|                   | Autogen Integration        | 用 Microsoft Autogen 作为执行器    | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/autogen](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/autogen)                                |
|                   | Azure Foundry Agent        | 调用 Azure AI Foundry SDK 示例   | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/azureaifoundry\_sdk](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/azureaifoundry_sdk)         |
|                   | Birthday Planner           | ADK 版生日派对多步骤策划               | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/birthday\_planner\_adk](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/birthday_planner_adk)    |
|                   | Calendar Agent             | 读写日历、预订会议时段                  | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/calendar\_agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/birthday_planner_adk/calendar_agent)                 |
|                   | CrewAI Collab              | 演示 CrewAI 多角色协作              | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/crewai](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/crewai)                                  |
|                   | Google ADK Demo            | Google 官方 ADK 最小示例           | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/google\_adk](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/google_adk)                         |
|                   | Headless OAuth2            | 无界面 Agent 的 OAuth2 授权流程      | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/headless\_agent\_auth](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/headless_agent_auth)      |
|                   | Hello World                | 建议首跑的“Hello World”脚手架        | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/helloworld](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/helloworld)                          |
|                   | LangGraph Dialogue         | 用 LangGraph 编排多轮对话           | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/langgraph](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/langgraph)                            |
|                   | LlamaIndex File QA         | 对本地文件做问答检索                   | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/llama\_index\_file\_chat](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/llama_index_file_chat) |
|                   | Marvin Integration         | 集成 Marvin 框架构建领域 Agent       | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/marvin](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/marvin)                                  |
|                   | MindsDB Predictor          | 调用 MindsDB 做预测与查询            | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/mindsdb](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/mindsdb)                                |
|                   | Semantic Kernel Orch       | 使用 Semantic Kernel 编排工具      | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/semantickernel](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/semantickernel)                  |
|                   | Travel Planner             | 一站式旅行规划 Agent                | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/travel\_planner\_agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/travel_planner_agent)    |
|                   | Veo Video Generator        | 借助 Veo API 自动生成视频            | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/veo\_video\_gen](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/veo_video_gen)                  |
|                   | Host Push Listener         | Host 侧监听推送并分发任务              | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/hosts](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/hosts)                                    |
|                   | Multi-Agent Orchestration  | 远程调用与协作综合示例                  | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/hosts/multiagent](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/hosts/multiagent)                          |
|                   | Common Utilities           | 公共工具库（解析卡片/客户端封装）            | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common)                                  |
|                   | Reference Server           | Python 版参考服务器 + 任务管理         | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common/server](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common/server)                                  |
|                   | Helper Scripts             | 推送鉴权等通用脚本                    | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common/utils](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common/utils)                                    |
| 🐹 **Go**         | Go Reference Impl          | Go 语言实现的完整 A2A 服务器 + 客户端     | [https://github.com/google-a2a/a2a-samples/tree/main/samples/go](https://github.com/google-a2a/a2a-samples/tree/main/samples/go)                                                        |

> **快速上手**
> 首次体验推荐：TypeScript `Movie Recommendation Agent`、Python `Hello World`，或 Go `Go Reference Impl` — 三者依赖少、启动指令最简单。

#### 框架集成 (官方示例)

*这些示例展示了使用特定框架构建的 Agent 如何提供 A2A 接口。*

| 语言       | Agent 框架      | Agent 描述                                | 关键 A2A 特性展示                     | 链接                                                                           |
| :--------- | :-------------- | :------------------------------------------ | :-------------------------------------- | :----------------------------------------------------------------------------- |
| 🐍 Python  | LangGraph       | 货币转换                                    | 工具使用, 流式传输, 多轮交互          | [链接](https://github.com/google-a2a/A2A/tree/v0.2.1/samples/python/agents/langgraph) |
| 🐍 Python  | CrewAI          | 图像生成                                    | 非文本 Artifacts (文件)             | [链接](https://github.com/google-a2a/A2A/tree/v0.2.1/samples/python/agents/crewai)   |
| 🐍 Python  | Google ADK      | 费用报销                                    | 多轮交互, 表单 (DataPart)             | [链接](https://github.com/google-a2a/A2A/tree/v0.2.1/samples/python/agents/google_adk)|
| 🚀 JS/TS   | Genkit          | 电影信息 / 代码生成                         | 工具使用, Artifacts (文件), 异步     | [链接](https://github.com/google-a2a/A2A/tree/v0.2.1/samples/js/src/agents)          |

#### 社区实现

##### SDK 与库 (按语言分类)

*   **Go**
    *   🌟 [trpc-a2a-go](https://github.com/trpc-group/trpc-a2a-go) by [@trpc-group](https://github.com/trpc-group) [![Stars](https://img.shields.io/github/stars/trpc-group/trpc-a2a-go?style=social)](https://github.com/trpc-group/trpc-a2a-go) - tRPC 团队开发的 Go 语言 A2A 实现，提供完整的客户端/服务端支持、内存任务管理、流式响应、会话管理和多种认证方式（JWT、API 密钥、OAuth2）。包含丰富的示例，包括基础服务器、流式传输和认证实现等。
    *   🌟 [a2a-go](https://github.com/a2aserver/a2a-go) by [@a2aserver](https://github.com/a2aserver) [![Stars](https://img.shields.io/github/stars/a2aserver/a2a-go?style=social)](https://github.com/a2aserver/a2a-go) - 用于构建 A2A 服务器的 Go 库，包含示例实现。
*   **Rust**
    *   🌟 [a2a-rs](https://github.com/EmilLindfors/a2a-rs) by [@EmilLindfors](https://github.com/EmilLindfors) [![Stars](https://img.shields.io/github/stars/EmilLindfors/a2a-rs?style=social)](https://github.com/EmilLindfors/a2a-rs) - 遵循 Rust 惯用实践和六边形架构原则的 Rust 实现。
    *   🌟 [Agentic](https://github.com/jeremychone/rust-agentic) by [@jeremychone](https://github.com/jeremychone) [![Stars](https://img.shields.io/github/stars/jeremychone/rust-agentic?style=social)](https://github.com/jeremychone/rust-agentic) - Rust 中的 MCP 和 A2A 支持库。通过符合人体工程学的 API 为 MCP 和 A2A 支持等核心组件提供构建 Agentic 应用和系统的基本构件。(开发中)
*   **Python**
    *   🌟 [a2a-python](https://github.com/google/a2a-python) by [@google](https://github.com/google) [![Stars](https://img.shields.io/github/stars/google/a2a-python?style=social)](https://github.com/google/a2a-python) - **官方** Python SDK，帮助运行遵循 A2A 协议的代理应用程序。
    *   🌟 [a2a_min](https://github.com/pcingola/a2a_min) by [@pcingola](https://github.com/pcingola) [![Stars](https://img.shields.io/github/stars/pcingola/a2a_min?style=social)](https://github.com/pcingola/a2a_min) - 用于 A2A 通信的极简 Python SDK。
    *   🌟 [python-a2a](https://github.com/themanojdesai/python-a2a) by [@themanojdesai](https://github.com/themanojdesai) [![Stars](https://img.shields.io/github/stars/themanojdesai/python-a2a?style=social)](https://github.com/themanojdesai/python-a2a) - 一个易于使用的 Python 库，用于实现 A2A 协议。
    *   🌟 [A2AServer](https://github.com/johnson7788/A2AServer) by [@johnson7788](https://github.com/johnson7788) [![Stars](https://img.shields.io/github/stars/johnson7788/A2AServer?style=social)](https://github.com/johnson7788/A2AServer) - 一个 Python 服务器框架，实现了 Google 的 A2A 协议并集成了 MCP。
*   **C#/.NET**
    *   🌟 [a2adotnet](https://github.com/azixaka/a2adotnet) by [@azixaka](https://github.com/azixaka) [![Stars](https://img.shields.io/github/stars/azixaka/a2adotnet?style=social)](https://github.com/azixaka/a2adotnet) - A2A 协议的 C#/.NET 实现。
    *   🌟 [a2a-net](https://github.com/neuroglia-io/a2a-net) by [@neuroglia-io](https://github.com/neuroglia-io) [![Stars](https://img.shields.io/github/stars/neuroglia-io/a2a-net?style=social)](https://github.com/neuroglia-io/a2a-net) - Agent2Agent (A2A) 协议的 .NET 实现，用于实现跨框架和供应商的自主代理之间的安全、可互操作通信。
*   **JavaScript/TypeScript**
    *   🌟 [nestjs-a2a](https://github.com/thestupd/nestjs-a2a) by [@thestupd](https://github.com/thestupd) [![Stars](https://img.shields.io/github/stars/thestupd/nestjs-a2a?style=social)](https://github.com/thestupd/nestjs-a2a) - 用于将 A2A 协议集成到 NestJS 应用程序的模块。
    *   🌟 [Artinet SDK](https://github.com/the-artinet-project/artinet-sdk) by [@the-artinet-project](https://github.com/the-artinet-project) [![Stars](https://img.shields.io/github/stars/the-artinet-project/artinet-sdk?style=social)](https://github.com/the-artinet-project/artinet-sdk) - TypeScript (Node.js) A2A 兼容服务器/客户端，简化可互操作 AI Agent 创建，注重开发者体验与生产力。
*   **Java**
    *   🌟 [a2ajava](https://github.com/vishalmysore/a2ajava) by [@vishalmysore](https://github.com/vishalmysore) [![Stars](https://img.shields.io/github/stars/vishalmysore/a2ajava?style=social)](https://github.com/vishalmysore/a2ajava) - 基于 Spring Boot 的 Java A2A 服务端/客户端实现，使用注解简化开发。支持 WebSocket、MCP 集成，并包含企业级/Kubernetes 部署教程。
    *   🌟 [a2a4j](https://github.com/a2ap/a2a4j) by [@a2ap](https://github.com/a2ap) [![Stars](https://img.shields.io/github/stars/a2ap/a2a4j?style=social)](https://github.com/a2ap/a2a4j) - A2A4J 是 Agent2Agent 协议的全面 Java 实现，为独立的 AI 代理系统之间的通信和互操作性提供了一个开放标准。

##### 平台与集成解决方案

*   🌟 [Elkar](https://github.com/elkar-ai/elkar-a2a) by [@elkar-ai](https://github.com/elkar-ai) [![Stars](https://img.shields.io/github/stars/elkar-ai/elkar-a2a?style=social)](https://github.com/elkar-ai/elkar-a2a) - 一个基于 Google Agent2Agent 协议 (A2A) 的开源 AI Agent 任务管理层。轻松实现跨 AI Agent 的任务发送、跟踪和编排。
*   🌟 [Aira](https://github.com/IhateCreatingUserNames2/Aira) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Aira?style=social)](https://github.com/IhateCreatingUserNames2/Aira) - 一个 A2A 网络实现，用于托管、注册、发现和与 Agent 交互。其包含 Agent 发现机制。
*   🌟 [Cognisphere](https://github.com/IhateCreatingUserNames2/Cognisphere) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Cognisphere?style=social)](https://github.com/IhateCreatingUserNames2/Cognisphere) - 一个基于 Google ADK 构建的 AI Agent 开发框架，可能用于创建 A2A 网络中的 Agent。
*   🌐 [Grasp](https://github.com/aircodelabs/grasp) by [@adcentury](https://github.com/adcentury) [![Stars](https://img.shields.io/github/stars/aircodelabs/grasp?style=social)](https://github.com/aircodelabs/grasp) - 可本地部署或自托管的浏览器自动化操作，原生支持 MCP 和 A2A。
*   🌟 [swissknife](https://github.com/daltonnyx/swissknife) by [@daltonnyx](https://github.com/daltonnyx) [![Stars](https://img.shields.io/github/stars/daltonnyx/swissknife?style=social)](https://github.com/daltonnyx/swissknife) - 一个支持 MCP 的多 Agent 聊天应用，旨在通过 A2A 协议暴露 Agent，并作为客户端连接到远程 A2A Agent。
*   🌟 [n8n-nodes-agent2agent](https://github.com/pjawz/n8n-nodes-agent2agent) by [@pjawz](https://github.com/pjawz) [![Stars](https://img.shields.io/github/stars/pjawz/n8n-nodes-agent2agent?style=social)](https://github.com/pjawz/n8n-nodes-agent2agent) - 为 n8n 添加了节点，用于通过 Google 的 Agent2Agent (A2A) 协议与 AI Agent 交互。
<!-- 在此添加您的实现！请参阅 CONTRIBUTING.md -->

## 🛠️ 工具与实用程序

本章节旨在收录与 A2A 协议相关的独立工具和实用程序。目前生态仍在发展，欢迎社区贡献！

*   **Agent 发现服务 (Agent Discovery Services)**
    *   一些平台级实现（如 [Aira](https://github.com/IhateCreatingUserNames2/Aira)）在其功能中包含了 Agent 的注册与发现机制。
    *   *期待社区贡献：独立的 Agent 目录服务实现、Agent Card 搜索引擎等。* <!-- TODO: 欢迎社区贡献相关工具 -->
*   **A2A 验证工具 (A2A Validation Tool)**
    *   ⚙️ [A2A Validation Tool](https://github.com/llmx-de/a2a-validation-tool) by [@llmx-de](https://github.com/llmx-de) [![Stars](https://img.shields.io/github/stars/llmx-de/a2a-validation-tool?style=social)](https://github.com/llmx-de/a2a-validation-tool) - 跨平台桌面应用，用于测试和验证 A2A 协议实现，支持多 Agent 连接和会话管理等功能。
    *   *期待社区贡献：用于检查 Agent Card、Task/Artifact 结构是否符合 A2A JSON Schema 规范的在线或命令行验证器，或集成到 IDE 的插件等。* <!-- TODO: 欢迎社区贡献相关工具 -->
*   **监控/追踪适配器 (Monitoring/Tracing Adapters)**
    *   *期待社区贡献：将 A2A 任务流数据接入 OpenTelemetry, Prometheus, Grafana 等主流监控平台的适配器或库。* <!-- TODO: 欢迎社区贡献相关工具 -->
*   **其他实用工具**
    *   *期待社区贡献：例如 A2A 消息构造辅助工具、Agent Card 生成器、Mock A2A Server/Client 等。* <!-- TODO: 欢迎社区贡献相关工具 -->
    *   🌟 [autoa2a](https://github.com/NapthaAI/autoa2a) by [NapthaAI](https://github.com/NapthaAI) [![Stars](https://img.shields.io/github/stars/NapthaAI/autoa2a?style=social)](https://github.com/NapthaAI/autoa2a) - 轻松将现有 Agent 框架中的 Agent 和编排器转换为 A2A 服务器。

## 📚 教程与文章

*   📄 [官方 A2A 概念概览 (README)](https://github.com/google/A2A#conceptual-overview) - 官方仓库 README 中的高级解释。
*   🚀 [官方入门指南 (README)](https://github.com/google/A2A#getting-started) - 官方仓库 README 中指向文档、规范、示例的链接。
*   🌐 [Agent2Agent 协议文档站](https://agent2agent.ren) - 社区驱动的开源 A2A 协议文档网站。使用 React/TypeScript 构建，支持英文、中文和日文。([源代码](https://github.com/ai-boost/agent2agent_doc))
*   📄 [A Survey of AI Agent Protocols](https://arxiv.org/pdf/2504.16736) - 学术论文，调研了现有的 LLM Agent 通信协议（包括 A2A 所属的类别），对其进行分类、性能分析，并讨论了未来挑战。
*   📚 [A2A 与 MCP 教程](https://github.com/Tsadoq/a2a-mcp-tutorial) by [@Tsadoq](https://github.com/Tsadoq) [![Stars](https://img.shields.io/github/stars/Tsadoq/a2a-mcp-tutorial?style=social)](https://github.com/Tsadoq/a2a-mcp-tutorial) - 关于如何使用 Anthropic 的 Model Context Protocol 和 Google 的 Agent2Agent Protocol 的教程。

## 🎬 Demo 与示例

*   🌐 [官方多 Agent Web 应用 (Python/Mesop)](https://github.com/google-a2a/A2A/tree/v0.2.1/demo) - 展示编排器 Agent 与多个远程 Agent 交互，渲染文本、图像和表单。**需要运行 Python 代码。**
*   🎥 [官方 Demo 视频 (章节链接)](https://github.com/google/A2A#see-a2a-in-action) - 指向官方仓库 README 中嵌入视频的链接。
*   💻 [Agent2Agent (A2A) Samples](https://github.com/google-a2a/a2a-samples) by [@google-a2a](https://github.com/google-a2a) [![Stars](https://img.shields.io/github/stars/google-a2a/a2a-samples?style=social)](https://github.com/google-a2a/a2a-samples) - 官方仓库，包含使用 Agent2Agent (A2A) 协议的代码示例和演示。

## 🔗 相关协议与概念

*   📦 [Model Context Protocol (MCP)](https://github.com/modelcontextprotocol/servers) - 互补协议，专注于向 Agent 提供工具/上下文。 ([A2A 与 MCP 讨论](https://google-a2a.github.io/A2A/#/topics/a2a_and_mcp.md)).
*   📞 *Function Calling / 工具使用标准* - *期待社区贡献：与 A2A 结合使用的函数调用/工具使用的模式、最佳实践或相关标准讨论。* <!-- TODO: 欢迎社区贡献相关标准或讨论 -->

## 💬 社区

*   🐞 [google/A2A GitHub Issues](https://github.com/google-a2a/A2A/issues) - 用于报告 Bug 或建议协议改进。
*   💬 [google/A2A GitHub Discussions](https://github.com/google-a2a/A2A/discussions/) - 用于有关 A2A 协议的一般性问题、想法和社区讨论。
*   🔒 [私密反馈表单](https://docs.google.com/forms/d/e/1FAIpQLScS23OMSKnVFmYeqS2dP7dxY3eTyT7lmtGLUa8OJZfP4RTijQ/viewform) - 用于私密反馈的 Google 表单。

---

**一起让 Awesome A2A 更有用！**

A2A 还是个新东西，相关的资源和实践经验比较分散。我们创建这个列表，就是想把好东西集中起来，方便大家查找、学习和参考。

要让这个列表持续保持高质量，离不开社区每个人的帮助：

*   ⭐ **点个 Star**：如果你觉得它有用，这既是支持，也方便你自己以后回来找。
*   ➕ **分享你的发现**：看到好的库、文章、工具或者踩过的坑？通过 [Issue](https://github.com/ai-boost/awesome-a2a/issues) 或 [PR](CONTRIBUTING.md) 加上来，一起完善它。
*   📣 **告诉其他人**：让更多正在研究或使用 A2A 的朋友知道这里。

感谢你的关注和贡献！

---

## 贡献

欢迎贡献！ 🙌 请先阅读 [贡献指南](CONTRIBUTING.md)。让我们一起构建这个列表！
