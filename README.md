<div align="center">
  <h2 align="center">✨ Awesome A2A (Agent2Agent Protocol) ✨</h2>
  <p align="center">
    <img src="assets/banner.png" alt="Awesome A2A Banner - Abstract network or connection graphic" width="600">
  </p>
  <p>
      <a href="README.md">English</a> | <a href="README_zh.md">简体中文</a> | <a href="README_ja.md">日本語</a> | <a href="README_es.md">Español</a> | <a href="README_de.md">Deutsch</a> | <a href="README_fr.md">Français</a>
      <!-- Add other languages here like: | <a href="README_de.md">Deutsch</a> -->
  </p>
  <p align="center">
     A curated list of awesome resources, implementations, tools, and examples related to the Google Agent2Agent (A2A) Protocol for AI agent interoperability.
  </p>
  <h4 align="center">
    <a href="https://awesome.re">
      <img src="https://awesome.re/badge.svg" alt="Awesome" />
    </a>
    <a href="CONTRIBUTING.md"> <!-- Link to your contributing file -->
      <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square" alt="PRs Welcome" />
    </a>
  </h4>
</div>


## Contents

*   [🤔 What is A2A? (Briefly)](#-what-is-a2a-briefly)
*   [💡 Key Principles](#-key-principles)
*   [⚙️ How Does A2A Work? (High Level)](#️-how-does-a2a-work-high-level)
*   [🚀 Getting Started with A2A](#-getting-started-with-a2a)
*   [🏛️ Official Resources](#️-official-resources)
*   [📜 Specification & Core Concepts](#-specification--core-concepts)
*   [⚙️ Implementations & Libraries](#️-implementations--libraries)
    *   [Official Samples](#official-samples)
    *   [Framework Integrations (Official Samples)](#framework-integrations-official-samples)
    *   [Community Implementations](#community-implementations)
        *   [SDKs & Libraries (by language)](#sdks--libraries-by-language)
        *   [Platforms & Integrated Solutions](#platforms--integrated-solutions)
*   [🛠️ Tools & Utilities](#️-tools--utilities)
*   [📚 Tutorials & Articles](#-tutorials--articles)
*   [🎬 Demos & Examples](#-demos--examples)
*   [🔗 Related Protocols & Concepts](#-related-protocols--concepts)
*   [💬 Community](#-community)
*   [Contributing](#contributing)

---

## 🤔 What is A2A? (Briefly)

A2A (Agent2Agent) is an **open protocol** from Google and partners enabling different **AI agents** (from various vendors/frameworks) to **communicate securely** and **collaborate on tasks**. It aims to break down silos between isolated agent systems, allowing for more complex cross-application automation.

**⭐ Official Website:** [google.github.io/A2A](https://google.github.io/A2A) | **⭐ Official GitHub:** [github.com/google/A2A](https://github.com/google/A2A) | 🌐 **Multilingual Docs (EN/ZH/JA):** [agent2agent.ren](https://agent2agent.ren)

## 💡 Key Principles

*   **Simple:** Uses existing standards (HTTP, JSON-RPC, SSE).
*   **Enterprise Ready:** Focuses on Auth, Security, Privacy, Monitoring.
*   **Async First:** Handles long-running tasks & human-in-the-loop.
*   **Modality Agnostic:** Supports Text, Files, Forms, Streams, etc.
*   **Opaque Execution:** Agents interact without sharing internal logic/tools.

## ⚙️ How Does A2A Work? (High Level)

1.  **Discovery:** Agents publish an `Agent Card` (JSON) describing capabilities, endpoint, and auth needs.
2.  **Communication:** A `Client` agent sends a `Task` request (containing a `Message` with `Parts`) to a `Remote Agent (Server)` using HTTP/JSON-RPC 2.0.
3.  **Execution & Response:** The Server processes the task, updating its `status`. It responds with the final status and any generated `Artifacts` (results, also containing `Parts`).
4.  **Updates:** For long tasks, the Server can optionally stream `TaskStatusUpdateEvent` or `TaskArtifactUpdateEvent` via Server-Sent Events (SSE) or use Push Notifications.

*For details, see the [Official Technical Documentation](https://google-a2a.github.io/A2A/#/documentation).*

---

## 🚀 Getting Started with A2A

New to A2A? Here's a suggested path:

1.  **Understand the Basics:** Read the sections above ([What is A2A?](#-what-is-a2a-briefly), [Key Principles](#-key-principles), [How it Works](#️-how-does-a2a-work-high-level)). Check the 📰 [Announcement Blog Post](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/).
2.  **Explore Core Concepts:** Dive into the 📖 [Official Technical Documentation](https://google-a2a.github.io/A2A/#/documentation), focusing on `Agent Card`, `Task`, `Message`, `Part`, and `Artifact`.
3.  **See it in Action:** Watch the 🎥 [Official Demo Video](https://storage.googleapis.com/gweb-developer-goog-blog-assets/original_videos/A2A_demo_v4.mp4) and explore the code for the 🌐 [Multi-Agent Web App Demo](https://github.com/google-a2a/A2A/tree/v0.2.1/demo).
4.  **Run the Samples:** Clone the [Official Samples Repo](https://github.com/google-a2a/a2a-samples) and follow its instructions to run a client (like the CLI) and a sample agent (e.g., LangGraph or Genkit agent).
5.  **Review the Code:** Look at the `common` (Python) or `server`/`client` (JS/TS) libraries in the official samples to see how A2A communication is implemented.
6.  **Try Building:** Adapt a sample or use a library to create your own basic A2A agent or client.

---

## 🏛️ Official Resources

*   📄 [A2A Protocol Website](https://google.github.io/A2A) - The main documentation site.
*   💻 [google/A2A GitHub Repository](https://github.com/google/A2A) - Source code for the spec, docs, and official samples.
*   📰 [Google Developers Blog Post](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) - Announcement blog post explaining the motivation and partners.

## 📜 Specification & Core Concepts

*(See [How Does A2A Work?](#️-how-does-a2a-work-high-level) above for summaries)*

*   📖 [A2A Technical Documentation](https://google-a2a.github.io/A2A/#/documentation) - **(Full Details)** Detailed explanation of actors, transport, auth, core objects (Task, Artifact, Message, Part), Agent Card, etc.
*   📄 [JSON Specification](https://github.com/google-a2a/A2A/tree/main/specification/json) - The raw JSON schema definition for A2A structures.
*   💡 [Key Principles (Docs)](https://google-a2a.github.io/A2A/#/documentation?id=key-principles) - Link to the principles section in the official docs.
*   🃏 [Agent Card Specification (Docs)](https://google-a2a.github.io/A2A/#/documentation?id=agent-card) - Link to the Agent Card section in the official docs.
*   🗺️ [Agent Discovery (Topic)](https://google-a2a.github.io/A2A/#/topics/agent_discovery.md) - Discussion on how clients can find agent cards.
*   🔔 [Push Notifications (Topic)](https://google-a2a.github.io/A2A/#/topics/push_notifications.md) - Details on the push notification mechanism.
*   🛡️ [Enterprise Readiness (Topic)](https://google-a2a.github.io/A2A/#/topics/enterprise_ready.md) - Discussion on security, auth, privacy aspects.

## ⚙️ Implementations & Libraries

#### Official Samples

*These demonstrate basic A2A client/server communication.*

| Language          | Sample Name                | One-line Description                                         | GitHub URL                                                                                                                                                                              |
| ----------------- | -------------------------- | ------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🔷 **TypeScript** | Genkit SDK Core            | TS SDK + CLI, builds shared code for front- and backend      | [https://github.com/google-a2a/a2a-samples/tree/main/samples/js](https://github.com/google-a2a/a2a-samples/tree/main/samples/js)                                                        |
|                   | Movie Recommendation Agent | Movie-recommendation conversational agent built with Genkit  | [https://github.com/google-a2a/a2a-samples/tree/main/samples/js/src/agents/movie-agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/js/src/agents/movie-agent)                                |
|                   | TypeScript Client          | Pure-frontend call example written in TS                     | [https://github.com/google-a2a/a2a-samples/tree/main/samples/js/client](https://github.com/google-a2a/a2a-samples/tree/main/samples/js/client)                                          |
|                   | Node Express Server        | A2A HTTP service implemented with Node/Express               | [https://github.com/google-a2a/a2a-samples/tree/main/samples/js/server](https://github.com/google-a2a/a2a-samples/tree/main/samples/js/server)                                          |
| ☕ **Java**        | Java Client Demo           | Java client example (with streaming listener)                | [https://github.com/google-a2a/a2a-samples/tree/main/samples/java/client](https://github.com/google-a2a/a2a-samples/tree/main/samples/java/client)                                      |
|                   | Java Data Models           | Complete set of POJO data models for the protocol            | [https://github.com/google-a2a/a2a-samples/tree/main/samples/java/model](https://github.com/google-a2a/a2a-samples/tree/main/samples/java/model)                                        |
|                   | Java Server Impl           | Spring Boot A2A server                                       | [https://github.com/google-a2a/a2a-samples/tree/main/samples/java/server](https://github.com/google-a2a/a2a-samples/tree/main/samples/java/server)                                      |
| 🐍 **Python**     | CLI Quickstart             | One-liner CLI to test an A2A call loop                       | [https://github.com/google-a2a/a2a-samples/tree/main/samples](https://github.com/google-a2a/a2a-samples/tree/main/samples)                                                              |
|                   | Host Agent Service         | Entry service that hosts and dispatches downstream agents    | [https://github.com/google-a2a/a2a-samples/tree/main/samples/host\_agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/a2a-adk-app/host_agent)                                       |
|                   | Weather Agent              | Weather-query agent + HTTP server                            | [https://github.com/google-a2a/a2a-samples/tree/main/samples/weather\_agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/a2a-adk-app/weather_agent)                                 |
|                   | Minimal MCP                | Bare-metal multi-agent coordination protocol                 | [https://github.com/google-a2a/a2a-samples/tree/main/samples/a2a-mcp-without-framework](https://github.com/google-a2a/a2a-samples/tree/main/samples/a2a-mcp-without-framework)          |
|                   | Travel Agency Agents       | Multi-agent collaboration for a travel-agency scenario       | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/a2a_mcp)                                  |
|                   | A2A Telemetry              | Collects and displays agent telemetry data                   | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/a2a\_telemetry](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/a2a_telemetry)                   |
|                   | AG2 Mini-Demo              | Minimal A↔A mutual-call skeleton                             | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/ag2](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/ag2)                                        |
|                   | Analytics Workflow         | Multi-agent orchestration for data-analytics scenarios       | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/analytics](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/analytics)                            |
|                   | Autogen Integration        | Uses Microsoft Autogen as the executor                       | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/autogen](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/autogen)                                |
|                   | Azure Foundry Agent        | Example using Azure AI Foundry SDK                           | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/azureaifoundry\_sdk](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/azureaifoundry_sdk)         |
|                   | Birthday Planner           | ADK edition: multi-step birthday-party planner               | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/birthday\_planner\_adk](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/birthday_planner_adk)    |
|                   | Calendar Agent             | Reads/writes calendar and books meeting slots                | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/calendar\_agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/birthday_planner_adk/calendar_agent)                 |
|                   | CrewAI Collab              | Demonstrates multi-role collaboration with CrewAI            | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/crewai](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/crewai)                                  |
|                   | Google ADK Demo            | Google official ADK minimal demo                             | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/google\_adk](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/google_adk)                         |
|                   | Headless OAuth2            | OAuth2 flow for headless agents                              | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/headless\_agent\_auth](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/headless_agent_auth)      |
|                   | Hello World                | Recommended first-run “Hello World” scaffold                 | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/helloworld](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/helloworld)                          |
|                   | LangGraph Dialogue         | Uses LangGraph to orchestrate multi-turn dialogue            | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/langgraph](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/langgraph)                            |
|                   | LlamaIndex File QA         | Q\&A retrieval over local files                              | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/llama\_index\_file\_chat](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/llama_index_file_chat) |
|                   | Marvin Integration         | Builds domain agents with Marvin integration                 | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/marvin](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/marvin)                                  |
|                   | MindsDB Predictor          | Calls MindsDB for prediction and querying                    | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/mindsdb](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/mindsdb)                                |
|                   | Semantic Kernel Orch       | Orchestrates tools with Semantic Kernel                      | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/semantickernel](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/semantickernel)                  |
|                   | Travel Planner             | One-stop travel-planning agent                               | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/travel\_planner\_agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/travel_planner_agent)    |
|                   | Veo Video Generator        | Generates video automatically via the Veo API                | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/veo\_video\_gen](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/veo_video_gen)                  |
|                   | Host Push Listener         | Host-side listener that dispatches pushed tasks              | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/hosts](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/hosts)                                    |
|                   | Multi-Agent Orchestration  | Comprehensive example of remote invocation and collaboration | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/hosts/multiagent](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/hosts/multiagent)                          |
|                   | Common Utilities           | Common utility library (card parsing/client wrappers)        | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common)                                  |
|                   | Reference Server           | Python reference server + task management                    | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common/server](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common/server)                                  |
|                   | Helper Scripts             | General scripts for push auth, etc.                          | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common/utils](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common/utils)                                    |
| 🐹 **Go**         | Go Reference Impl          | Full A2A server + client implemented in Go                   | [https://github.com/google-a2a/a2a-samples/tree/main/samples/go](https://github.com/google-a2a/a2a-samples/tree/main/samples/go)                                                        |

> **Quick Start**
> First-time users: try **TypeScript `Movie Recommendation Agent`**, **Python `Hello World`**, or **Go `Go Reference Impl`** — minimal dependencies and the simplest startup commands.

#### Framework Integrations (Official Samples)

*These show how agents built with specific frameworks can expose an A2A interface.*

| Language   | Agent Framework | Agent Description                           | Key A2A Features Demonstrated         | Link                                                                           |
| :--------- | :-------------- | :------------------------------------------ | :-------------------------------------- | :----------------------------------------------------------------------------- |
| 🐍 Python  | LangGraph       | Currency conversion                         | Tools, Streaming, Multi-turn          | [Link](https://github.com/google-a2a/A2A/tree/v0.2.1/samples/python/agents/langgraph) |
| 🐍 Python  | CrewAI          | Image generation                            | Non-textual Artifacts (Files)         | [Link](https://github.com/google-a2a/A2A/tree/v0.2.1/samples/python/agents/crewai)   |
| 🐍 Python  | Google ADK      | Expense reimbursement                       | Multi-turn, Forms (DataPart)          | [Link](https://github.com/google-a2a/A2A/tree/v0.2.1/samples/python/agents/google_adk)|
| 🚀 JS/TS   | Genkit          | Movie info / Code generation                | Tools, Artifacts (Files), Async       | [Link](https://github.com/google-a2a/A2A/tree/v0.2.1/samples/js/src/agents)          |

#### Community Implementations

##### SDKs & Libraries (by language)

*   **Go**
    *   🌟 [trpc-a2a-go](https://github.com/trpc-group/trpc-a2a-go) by [@trpc-group](https://github.com/trpc-group) [![Stars](https://img.shields.io/github/stars/trpc-group/trpc-a2a-go?style=social)](https://github.com/trpc-group/trpc-a2a-go) - Go A2A implementation by the tRPC team featuring full client/server support, in-memory task management, streaming responses, session management, multiple auth methods (JWT, API Key, OAuth2), and comprehensive examples.
    *   🌟 [a2a-go](https://github.com/a2aserver/a2a-go) by [@a2aserver](https://github.com/a2aserver) [![Stars](https://img.shields.io/github/stars/a2aserver/a2a-go?style=social)](https://github.com/a2aserver/a2a-go) - A Go library for building A2A servers, with example implementations.
*   **Rust**
    *   🌟 [a2a-rs](https://github.com/EmilLindfors/a2a-rs) by [@EmilLindfors](https://github.com/EmilLindfors) [![Stars](https://img.shields.io/github/stars/EmilLindfors/a2a-rs?style=social)](https://github.com/EmilLindfors/a2a-rs) - An idiomatic Rust implementation following hexagonal architecture principles.
    *   🌟 [Agentic](https://github.com/jeremychone/rust-agentic) by [@jeremychone](https://github.com/jeremychone) [![Stars](https://img.shields.io/github/stars/jeremychone/rust-agentic?style=social)](https://github.com/jeremychone/rust-agentic) - A Rust crate providing essential building blocks for agentic applications, with an ergonomic API for MCP and A2A support. (Work in Progress)
*   **Python**
    *   🌟 [a2a-python](https://github.com/google/a2a-python) by [@google](https://github.com/google) [![Stars](https://img.shields.io/github/stars/google/a2a-python?style=social)](https://github.com/google/a2a-python) - **Official** Python SDK for running agentic applications as A2A servers following the Agent2Agent Protocol.
    *   🌟 [a2a_min](https://github.com/pcingola/a2a_min) by [@pcingola](https://github.com/pcingola) [![Stars](https://img.shields.io/github/stars/pcingola/a2a_min?style=social)](https://github.com/pcingola/a2a_min) - A minimalistic Python SDK for A2A communication.
    *   🌟 [python-a2a](https://github.com/themanojdesai/python-a2a) by [@themanojdesai](https://github.com/themanojdesai) [![Stars](https://img.shields.io/github/stars/themanojdesai/python-a2a?style=social)](https://github.com/themanojdesai/python-a2a) - An easy-to-use Python library for implementing the A2A protocol.
    *   🌟 [A2AServer](https://github.com/johnson7788/A2AServer) by [@johnson7788](https://github.com/johnson7788) [![Stars](https://img.shields.io/github/stars/johnson7788/A2AServer?style=social)](https://github.com/johnson7788/A2AServer) - A Python server framework implementing Google's A2A protocol with MCP integration.
*   **C#/.NET**
    *   🌟 [a2adotnet](https://github.com/azixaka/a2adotnet) by [@azixaka](https://github.com/azixaka) [![Stars](https://img.shields.io/github/stars/azixaka/a2adotnet?style=social)](https://github.com/azixaka/a2adotnet) - A C#/.NET implementation of the A2A protocol.
    *   🌟 [a2a-net](https://github.com/neuroglia-io/a2a-net) by [@neuroglia-io](https://github.com/neuroglia-io) [![Stars](https://img.shields.io/github/stars/neuroglia-io/a2a-net?style=social)](https://github.com/neuroglia-io/a2a-net) - .NET implementation of the Agent2Agent (A2A) protocol to enable secure, interoperable communication between autonomous agents across frameworks and vendors.
*   **JavaScript/TypeScript**
    *   🌟 [nestjs-a2a](https://github.com/thestupd/nestjs-a2a) by [@thestupd](https://github.com/thestupd) [![Stars](https://img.shields.io/github/stars/thestupd/nestjs-a2a?style=social)](https://github.com/thestupd/nestjs-a2a) - A module for integrating the A2A protocol into NestJS applications.
    *   🌟 [Artinet SDK](https://github.com/the-artinet-project/artinet-sdk) by [@the-artinet-project](https://github.com/the-artinet-project) [![Stars](https://img.shields.io/github/stars/the-artinet-project/artinet-sdk?style=social)](https://github.com/the-artinet-project/artinet-sdk) - TypeScript (Node.js) A2A compliant server/client simplifying interoperable AI agent creation, focusing on DX and production-readiness.
*   **Java**
    *   🌟 [a2ajava](https://github.com/vishalmysore/a2ajava) by [@vishalmysore](https://github.com/vishalmysore) [![Stars](https://img.shields.io/github/stars/vishalmysore/a2ajava?style=social)](https://github.com/vishalmysore/a2ajava) - Java A2A server/client implementation using Spring Boot with annotations. Supports WebSockets, MCP integration, and includes enterprise/Kubernetes deployment tutorials.
    *   🌟 [a2a4j](https://github.com/a2ap/a2a4j) by [@a2ap](https://github.com/a2ap) [![Stars](https://img.shields.io/github/stars/a2ap/a2a4j?style=social)](https://github.com/a2ap/a2a4j) - A2A4J is a comprehensive Java implementation of the Agent2Agent Protocol, including server, client, examples, and a starter — ready to use out of the box.

##### Platforms & Integrated Solutions

*   🌟 [Elkar](https://github.com/elkar-ai/elkar-a2a) by [@elkar-ai](https://github.com/elkar-ai) [![Stars](https://img.shields.io/github/stars/elkar-ai/elkar-a2a?style=social)](https://github.com/elkar-ai/elkar-a2a) - An open-source task-management layer for AI agents — based on Google's Agent2Agent Protocol (A2A). Send, track, and orchestrate tasks across AI agents — effortlessly.
*   🌟 [Aira](https://github.com/IhateCreatingUserNames2/Aira) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Aira?style=social)](https://github.com/IhateCreatingUserNames2/Aira) - An A2A network implementation for hosting, registering, discovering, and interacting with agents. Includes agent discovery mechanisms.
*   🌟 [Cognisphere](https://github.com/IhateCreatingUserNames2/Cognisphere) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Cognisphere?style=social)](https://github.com/IhateCreatingUserNames2/Cognisphere) - An AI agent development framework built on Google's ADK, facilitating agent creation potentially for A2A networks.
*   🌐 [Grasp](https://github.com/aircodelabs/grasp) by [@adcentury](https://github.com/adcentury) [![Stars](https://img.shields.io/github/stars/aircodelabs/grasp?style=social)](https://github.com/aircodelabs/grasp) - A Self-hosted Browser Using Agent with built-in MCP and A2A support.
*   🌟 [swissknife](https://github.com/daltonnyx/swissknife) by [@daltonnyx](https://github.com/daltonnyx) [![Stars](https://img.shields.io/github/stars/daltonnyx/swissknife?style=social)](https://github.com/daltonnyx/swissknife) - A multi-agent chat application with MCP support, aiming to expose agents via the A2A protocol and connect to remote A2A agents as a client.
*   🌟 [n8n-nodes-agent2agent](https://github.com/pjawz/n8n-nodes-agent2agent) by [@pjawz](https://github.com/pjawz) [![Stars](https://img.shields.io/github/stars/pjawz/n8n-nodes-agent2agent?style=social)](https://github.com/pjawz/n8n-nodes-agent2agent) - Adds nodes to n8n for interacting with AI agents using Google's Agent2Agent (A2A) protocol.
<!-- Add yours here! See CONTRIBUTING.md -->

## 🛠️ Tools & Utilities

This section aims to list standalone tools and utilities related to the A2A protocol. The ecosystem is still developing, and community contributions are welcome!

*   **Agent Discovery Services**
    *   Some platform-level implementations (like [Aira](https://github.com/IhateCreatingUserNames2/Aira)) include agent registration and discovery mechanisms within their features.
    *   *Community contributions welcome: Standalone agent directory service implementations, Agent Card search engines, etc.* <!-- TODO: Community contributions for related tools are welcome -->
*   **A2A Validation Tool**
    *   ⚙️ [A2A Validation Tool](https://github.com/llmx-de/a2a-validation-tool) by [@llmx-de](https://github.com/llmx-de) [![Stars](https://img.shields.io/github/stars/llmx-de/a2a-validation-tool?style=social)](https://github.com/llmx-de/a2a-validation-tool) - Cross-platform desktop app for testing & validating A2A protocol implementations, with features like multi-agent connection and session management.
    *   *Community contributions welcome: Online or command-line validators for checking if Agent Card, Task/Artifact structures comply with A2A JSON Schema specifications, or IDE plugins, etc.* <!-- TODO: Community contributions for related tools are welcome -->
*   **Monitoring/Tracing Adapters**
    *   *Community contributions welcome: Adapters or libraries for integrating A2A task flow data into mainstream monitoring platforms like OpenTelemetry, Prometheus, Grafana, etc.* <!-- TODO: Community contributions for related tools are welcome -->
*   **Other Utilities**
    *   *Community contributions welcome: e.g., A2A message construction helper tools, Agent Card generators, Mock A2A Server/Client, etc.* <!-- TODO: Community contributions for related tools are welcome -->
    *   🌟 [autoa2a](https://github.com/NapthaAI/autoa2a) by [NapthaAI](https://github.com/NapthaAI) [![Stars](https://img.shields.io/github/stars/NapthaAI/autoa2a?style=social)](https://github.com/NapthaAI/autoa2a) - Easily convert agents and orchestrators from existing agent frameworks to A2A servers.

## 📚 Tutorials & Articles

*   📄 [Official A2A Conceptual Overview (README)](https://github.com/google/A2A#conceptual-overview) - High-level explanation in the official repo's README.
*   🚀 [Getting Started Guide (Official README)](https://github.com/google/A2A#getting-started) - Links to docs, spec, samples in the official repo's README.
*   🌐 [Agent2Agent Protocol Documentation Site](https://agent2agent.ren) - Community-driven, open-source documentation site for the A2A protocol. Built with React/TypeScript, supports English, Chinese, and Japanese. ([Source Code](https://github.com/ai-boost/agent2agent_doc))
*   📄 [A Survey of AI Agent Protocols](https://arxiv.org/pdf/2504.16736) - Academic paper surveying existing LLM agent communication protocols (including the category A2A falls into), classifying them, analyzing performance, and discussing future challenges.
*   📚 [A2A and MCP Tutorial](https://github.com/Tsadoq/a2a-mcp-tutorial) by [@Tsadoq](https://github.com/Tsadoq) [![Stars](https://img.shields.io/github/stars/Tsadoq/a2a-mcp-tutorial?style=social)](https://github.com/Tsadoq/a2a-mcp-tutorial) - A tutorial on how to use Model Context Protocol by Anthropic and Agent2Agent Protocol by Google.

## 🎬 Demos & Examples

*   🌐 [Official Multi-Agent Web App (Python/Mesop)](https://github.com/google-a2a/A2A/tree/v0.2.1/demo) - Demonstrates the orchestrator agent interacting with multiple remote agents, rendering text, images, and forms. **Requires running Python code.**
*   🎥 [Official Demo Video (Section Link)](https://github.com/google/A2A#see-a2a-in-action) - Link to the video embedded in the official repository's README.
*   💻 [Agent2Agent (A2A) Samples](https://github.com/google-a2a/a2a-samples) by [@google-a2a](https://github.com/google-a2a) [![Stars](https://img.shields.io/github/stars/google-a2a/a2a-samples?style=social)](https://github.com/google-a2a/a2a-samples) - Official repository containing code samples and demos which use the Agent2Agent (A2A) Protocol.

## 🔗 Related Protocols & Concepts

*   📦 [Model Context Protocol (MCP)](https://github.com/modelcontextprotocol/servers) - Complementary protocol focused on providing tools/context *to* agents. ([A2A and MCP Discussion](https://google-a2a.github.io/A2A/#/topics/a2a_and_mcp.md)).
*   📞 *Function Calling / Tool Use Standards* - *Community contributions welcome: Discussion on patterns, best practices, or relevant standards for function calling/tool use in conjunction with A2A.* <!-- TODO: Community contributions for related standards or discussions are welcome -->

## 💬 Community

*   🐞 [google/A2A GitHub Issues](https://github.com/google-a2a/A2A/issues) - For reporting bugs or suggesting protocol improvements.
*   💬 [google/A2A GitHub Discussions](https://github.com/google-a2a/A2A/discussions/) - For general questions, ideas, and community discussions about the A2A protocol.
*   🔒 [Private Feedback Form](https://docs.google.com/forms/d/e/1FAIpQLScS23OMSKnVFmYeqS2dP7dxY3eTyT7lmtGLUa8OJZfP4RTijQ/viewform) - Google form for private feedback.

---

**Let's Make Awesome A2A More Useful, Together!**

A2A is still pretty new, and good resources or practical tips can be scattered. We created this list to bring the good stuff together, making it easier for everyone to find, learn, and reference.

Keeping this list high-quality and up-to-date relies on the community:

*   ⭐ **Star it**: If you find it useful, it's a great way to show support and makes it easy to find later.
*   ➕ **Share what you find**: Found a great library, article, tool, or even a common pitfall? Add it via an [Issue](https://github.com/ai-boost/awesome-a2a/issues) or [PR](CONTRIBUTING.md) – let's build this resource together.
*   📣 **Spread the word**: Let others know about this list if they're exploring or working with A2A.

Thanks for your interest and contributions!

---

## Contributing

Contributions are welcome! 🙌 Please read the [contributing guidelines](CONTRIBUTING.md) first. Let's build this list together!
