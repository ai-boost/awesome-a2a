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

*For details, see the [Official Technical Documentation](https://google.github.io/A2A/#/documentation).*

---

## 🚀 Getting Started with A2A

New to A2A? Here's a suggested path:

1.  **Understand the Basics:** Read the sections above ([What is A2A?](#-what-is-a2a-briefly), [Key Principles](#-key-principles), [How it Works](#️-how-does-a2a-work-high-level)). Check the 📰 [Announcement Blog Post](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/).
2.  **Explore Core Concepts:** Dive into the 📖 [Official Technical Documentation](https://google.github.io/A2A/#/documentation), focusing on `Agent Card`, `Task`, `Message`, `Part`, and `Artifact`.
3.  **See it in Action:** Watch the 🎥 [Official Demo Video](https://storage.googleapis.com/gweb-developer-goog-blog-assets/original_videos/A2A_demo_v4.mp4) and explore the code for the 🌐 [Multi-Agent Web App Demo](https://github.com/google/A2A/tree/main/demo).
4.  **Run the Samples:** Clone the [Official Repo](https://github.com/google/A2A) and follow the instructions in `/samples` to run a client (like the CLI) and a sample agent (e.g., LangGraph or Genkit agent). See the [Official Samples](#official-samples) tables below for links.
5.  **Review the Code:** Look at the `common` (Python) or `server`/`client` (JS/TS) libraries in the official samples to see how A2A communication is implemented.
6.  **Try Building:** Adapt a sample or use a library to create your own basic A2A agent or client.

---

## 🏛️ Official Resources

*   📄 [A2A Protocol Website](https://google.github.io/A2A) - The main documentation site.
*   💻 [google/A2A GitHub Repository](https://github.com/google/A2A) - Source code for the spec, docs, and official samples.
*   📰 [Google Developers Blog Post](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) - Announcement blog post explaining the motivation and partners.

## 📜 Specification & Core Concepts

*(See [How Does A2A Work?](#️-how-does-a2a-work-high-level) above for summaries)*

*   📖 [A2A Technical Documentation](https://google.github.io/A2A/#/documentation) - **(Full Details)** Detailed explanation of actors, transport, auth, core objects (Task, Artifact, Message, Part), Agent Card, etc.
*   📄 [JSON Specification](https://github.com/google/A2A/tree/main/specification/json) - The raw JSON schema definition for A2A structures.
*   💡 [Key Principles (Docs)](https://google.github.io/A2A/#/documentation?id=key-principles) - Link to the principles section in the official docs.
*   🃏 [Agent Card Specification (Docs)](https://google.github.io/A2A/#/documentation?id=agent-card) - Link to the Agent Card section in the official docs.
*   🗺️ [Agent Discovery (Topic)](https://google.github.io/A2A/#/topics/agent_discovery.md) - Discussion on how clients can find agent cards.
*   🔔 [Push Notifications (Topic)](https://google.github.io/A2A/#/topics/push_notifications.md) - Details on the push notification mechanism.
*   🛡️ [Enterprise Readiness (Topic)](https://google.github.io/A2A/#/topics/enterprise_ready.md) - Discussion on security, auth, privacy aspects.

## ⚙️ Implementations & Libraries

#### Official Samples

*These demonstrate basic A2A client/server communication.*

| Language   | Type             | Framework   | Description                                     | Link                                                                              |
| :--------- | :--------------- | :---------- | :---------------------------------------------- | :-------------------------------------------------------------------------------- |
| 🐍 Python  | Common Library   | -           | Core HTTP, JSON-RPC, SSE handling             | [Link](https://github.com/google/A2A/tree/main/samples/python/common)             |
| 🐍 Python  | Host (Client)    | CLI         | Command-line client example                     | [Link](https://github.com/google/A2A/tree/main/samples/python/hosts/cli)          |
| 🐍 Python  | Host (Agent)     | ADK         | Orchestrator agent delegating to A2A agents     | [Link](https://github.com/google/A2A/tree/main/samples/python/hosts/multiagent)   |
| 🚀 JS/TS   | Server Library   | Express     | Core server implementation                    | [Link](https://github.com/google/A2A/tree/main/samples/js/src/server)             |
| 🚀 JS/TS   | Client Library   | -           | Client implementation                           | [Link](https://github.com/google/A2A/tree/main/samples/js/src/client)             |
| 🚀 JS/TS   | Host (Client)    | CLI         | Command-line client example                     | [Link](https://github.com/google/A2A/blob/main/samples/js/src/cli.ts)             |

#### Framework Integrations (Official Samples)

*These show how agents built with specific frameworks can expose an A2A interface.*

| Language   | Agent Framework | Agent Description                           | Key A2A Features Demonstrated         | Link                                                                           |
| :--------- | :-------------- | :------------------------------------------ | :-------------------------------------- | :----------------------------------------------------------------------------- |
| 🐍 Python  | LangGraph       | Currency conversion                         | Tools, Streaming, Multi-turn          | [Link](https://github.com/google/A2A/tree/main/samples/python/agents/langgraph) |
| 🐍 Python  | CrewAI          | Image generation                            | Non-textual Artifacts (Files)         | [Link](https://github.com/google/A2A/tree/main/samples/python/agents/crewai)   |
| 🐍 Python  | Google ADK      | Expense reimbursement                       | Multi-turn, Forms (DataPart)          | [Link](https://github.com/google/A2A/tree/main/samples/python/agents/google_adk)|
| 🚀 JS/TS   | Genkit          | Movie info / Code generation                | Tools, Artifacts (Files), Async       | [Link](https://github.com/google/A2A/tree/main/samples/js/src/agents)          |

#### Community Implementations

*   🌟 [trpc-a2a-go](https://github.com/trpc-group/trpc-a2a-go) by [@trpc-group](https://github.com/trpc-group) [![Stars](https://img.shields.io/github/stars/trpc-group/trpc-a2a-go?style=social)](https://github.com/trpc-group/trpc-a2a-go) - Go A2A implementation by the tRPC team featuring full client/server support, in-memory task management, streaming responses, session management, multiple auth methods (JWT, API Key, OAuth2), and comprehensive examples.
*   🌟 [a2a-go](https://github.com/a2aserver/a2a-go) by [@a2aserver](https://github.com/a2aserver) [![Stars](https://img.shields.io/github/stars/a2aserver/a2a-go?style=social)](https://github.com/a2aserver/a2a-go) - A Go library for building A2A servers, with example implementations.
*   🌟 [a2a-rs](https://github.com/EmilLindfors/a2a-rs) by [@EmilLindfors](https://github.com/EmilLindfors) [![Stars](https://img.shields.io/github/stars/EmilLindfors/a2a-rs?style=social)](https://github.com/EmilLindfors/a2a-rs) - An idiomatic Rust implementation following hexagonal architecture principles.
*   🌟 [a2a_min](https://github.com/pcingola/a2a_min) by [@pcingola](https://github.com/pcingola) [![Stars](https://img.shields.io/github/stars/pcingola/a2a_min?style=social)](https://github.com/pcingola/a2a_min) - A minimalistic Python SDK for A2A communication.
*   🌟 [a2adotnet](https://github.com/azixaka/a2adotnet) by [@azixaka](https://github.com/azixaka) [![Stars](https://img.shields.io/github/stars/azixaka/a2adotnet?style=social)](https://github.com/azixaka/a2adotnet) - A C#/.NET implementation of the A2A protocol.
*   🌟 [nestjs-a2a](https://github.com/thestupd/nestjs-a2a) by [@thestupd](https://github.com/thestupd) [![Stars](https://img.shields.io/github/stars/thestupd/nestjs-a2a?style=social)](https://github.com/thestupd/nestjs-a2a) - A module for integrating the A2A protocol into NestJS applications.
*   🌟 [python-a2a](https://github.com/themanojdesai/python-a2a) by [@themanojdesai](https://github.com/themanojdesai) [![Stars](https://img.shields.io/github/stars/themanojdesai/python-a2a?style=social)](https://github.com/themanojdesai/python-a2a) - An easy-to-use Python library for implementing the A2A protocol.
*   🌟 [Aira](https://github.com/IhateCreatingUserNames2/Aira) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Aira?style=social)](https://github.com/IhateCreatingUserNames2/Aira) - An A2A network implementation for hosting, registering, discovering, and interacting with agents.
*   🌟 [Cognisphere](https://github.com/IhateCreatingUserNames2/Cognisphere) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Cognisphere?style=social)](https://github.com/IhateCreatingUserNames2/Cognisphere) - An AI agent development framework built on Google's ADK, facilitating agent creation potentially for A2A networks.
<!-- Add yours here! See CONTRIBUTING.md -->

## 🛠️ Tools & Utilities

*   🔍 *Agent Discovery Services* - [Link] - Description (e.g., implementation of an 'Agent Catalog'). <!-- TODO -->
*   ✅ *A2A Validation Tool* - [Link] - Tool to check compliance of an A2A endpoint. <!-- TODO -->
*   📊 *Monitoring/Tracing Adapters* - [Link] - Integrations for observability platforms. <!-- TODO -->

## 📚 Tutorials & Articles

*   📄 [Official A2A Conceptual Overview (README)](https://github.com/google/A2A#conceptual-overview) - High-level explanation in the official repo's README.
*   🚀 [Getting Started Guide (Official README)](https://github.com/google/A2A#getting-started) - Links to docs, spec, samples in the official repo's README.
*   🌐 [Agent2Agent Protocol Documentation Site](https://agent2agent.ren) - Community-driven, open-source documentation site for the A2A protocol. Built with React/TypeScript, supports English, Chinese, and Japanese. ([Source Code](https://github.com/ai-boost/agent2agent_doc))
*   ✍️ *[Blog Post/Tutorial Title]* - [Link] - Description. <!-- TODO: Add community articles/guides here -->

## 🎬 Demos & Examples

*   🌐 [Official Multi-Agent Web App (Python/Mesop)](https://github.com/google/A2A/tree/main/demo) - Demonstrates the orchestrator agent interacting with multiple remote agents, rendering text, images, and forms. **Requires running Python code.**
*   🎥 [Official Demo Video (Section Link)](https://github.com/google/A2A#see-a2a-in-action) - Link to the video embedded in the official repository's README.

## 🔗 Related Protocols & Concepts

*   📦 [Model Context Protocol (MCP)](https://github.com/modelcontextprotocol/servers) - Complementary protocol focused on providing tools/context *to* agents. ([A2A and MCP Discussion](https://google.github.io/A2A/#/topics/a2a_and_mcp.md)).
*   📞 *Function Calling / Tool Use Standards* - [Link] - Relevant standards (e.g., OpenAI function calling). <!-- TODO -->

## 💬 Community

*   🐞 [google/A2A GitHub Issues](https://github.com/google/A2A/issues) - For reporting bugs or suggesting protocol improvements.
*   💬 [google/A2A GitHub Discussions](https://github.com/google/A2A/discussions/) - For general questions, ideas, and community discussions about the A2A protocol.
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
