<div align="center">
  <h2 align="center">✨ Awesome A2A (Agent2Agent Protokoll) ✨</h2>
  <p align="center">
    <img src="assets/banner.png" alt="Awesome A2A Banner - Abstrakte Netzwerk- oder Verbindungsgrafik" width="600">
  </p>
  <p>
      <a href="README.md">English</a> | <a href="README_zh.md">简体中文</a> | <a href="README_ja.md">日本語</a> | <a href="README_es.md">Español</a> | <a href="README_de.md">Deutsch</a> | <a href="README_fr.md">Français</a>
      <!-- Fügen Sie hier weitere Sprachen hinzu -->
  </p>
  <p align="center">
     Eine kuratierte Liste großartiger Ressourcen, Implementierungen, Tools und Beispiele im Zusammenhang mit dem Google Agent2Agent (A2A) Protokoll für die Interoperabilität von KI-Agenten.
  </p>
  <h4 align="center">
    <a href="https://awesome.re">
      <img src="https://awesome.re/badge.svg" alt="Awesome" />
    </a>
    <a href="CONTRIBUTING.md"> <!-- Link zu Ihrer Contributing-Datei -->
      <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square" alt="PRs Willkommen" />
    </a>
  </h4>
</div>


## Inhalt

*   [🤔 Was ist A2A? (Kurz)](#-was-ist-a2a-kurz)
*   [💡 Schlüsselprinzipien](#-schlüsselprinzipien)
*   [⚙️ Wie funktioniert A2A? (Übersicht)](#️-wie-funktioniert-a2a-übersicht)
*   [🚀 Erste Schritte mit A2A](#-erste-schritte-mit-a2a)
*   [🏛️ Offizielle Ressourcen](#️-offizielle-ressourcen)
*   [📜 Spezifikation & Kernkonzepte](#-spezifikation--kernkonzepte)
*   [⚙️ Implementierungen & Bibliotheken](#️-implementierungen--bibliotheken)
    *   [Offizielle Beispiele](#offizielle-beispiele)
    *   [Framework-Integrationen (Offizielle Beispiele)](#framework-integrationen-offizielle-beispiele)
    *   [Community-Implementierungen](#community-implementierungen)
        *   [SDKs & Bibliotheken (nach Sprache)](#sdks--bibliotheken-nach-sprache)
        *   [Frameworks](#frameworks)
        *   [Plattformen & Integrierte Lösungen](#plattformen--integrierte-lösungen)
*   [🛠️ Tools & Dienstprogramme](#️-tools--dienstprogramme)
*   [📚 Tutorials & Artikel](#-tutorials--artikel)
*   [🎬 Demos & Beispiele](#-demos--beispiele)
*   [🔗 Verwandte Protokolle & Konzepte](#-verwandte-protokolle--konzepte)
*   [💬 Community](#-community)
*   [Beitragen](#beitragen)

---

## 🤔 Was ist A2A? (Kurz)

A2A (Agent2Agent) ist ein **offenes Protokoll** von Google und Partnern, das es verschiedenen **KI-Agenten** (von unterschiedlichen Anbietern/Frameworks) ermöglicht, **sicher zu kommunizieren** und **bei Aufgaben zusammenzuarbeiten**. Ziel ist es, Silos zwischen isolierten Agentensystemen aufzubrechen und komplexere, anwendungsübergreifende Automatisierungen zu ermöglichen.

**⭐ Offizielle Website:** [google.github.io/A2A](https://google.github.io/A2A) | **⭐ Offizielles GitHub:** [github.com/google/A2A](https://github.com/google/A2A) | 🌐 **Mehrsprachige Doku (EN/ZH/JA):** [agent2agent.ren](https://agent2agent.ren)

## 💡 Schlüsselprinzipien

*   **Einfach:** Nutzt bestehende Standards (HTTP, JSON-RPC, SSE).
*   **Enterprise Ready:** Fokus auf Authentifizierung, Sicherheit, Datenschutz, Monitoring.
*   **Async First:** Handhabt langlaufende Aufgaben & menschliche Eingriffe (Human-in-the-Loop).
*   **Modalitätsagnostisch:** Unterstützt Text, Dateien, Formulare, Streams usw.
*   **Opaque Execution:** Agenten interagieren, ohne interne Logik/Tools zu teilen.

## ⚙️ Wie funktioniert A2A? (Übersicht)

1.  **Discovery (Entdeckung):** Agenten veröffentlichen eine `Agent Card` (JSON), die Fähigkeiten, Endpunkt und Authentifizierungsanforderungen beschreibt.
2.  **Kommunikation:** Ein `Client`-Agent sendet eine `Task`-Anfrage (die eine `Message` mit `Parts` enthält) über HTTP/JSON-RPC 2.0 an einen `Remote Agent (Server)`.
3.  **Ausführung & Antwort:** Der Server verarbeitet die Aufgabe und aktualisiert seinen `status`. Er antwortet mit dem endgültigen Status und allen generierten `Artifacts` (Ergebnisse, die ebenfalls `Parts` enthalten).
4.  **Updates:** Bei langen Aufgaben kann der Server optional `TaskStatusUpdateEvent` oder `TaskArtifactUpdateEvent` über Server-Sent Events (SSE) streamen oder Push-Benachrichtigungen verwenden.

*Details finden Sie in der [Offiziellen Technischen Dokumentation](https://google-a2a.github.io/A2A/#/documentation).*

---

## 🚀 Erste Schritte mit A2A

Neu bei A2A? Hier ist ein empfohlener Weg:

1.  **Grundlagen verstehen:** Lesen Sie die obigen Abschnitte ([Was ist A2A?](#-was-ist-a2a-kurz), [Schlüsselprinzipien](#-schlüsselprinzipien), [Wie es funktioniert](#️-wie-funktioniert-a2a-übersicht)). Sehen Sie sich den 📰 [Ankündigungs-Blogbeitrag](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) (Englisch) an.
2.  **Kernkonzepte erkunden:** Tauchen Sie tief in die 📖 [Offizielle Technische Dokumentation](https://google-a2a.github.io/A2A/#/documentation) ein und konzentrieren Sie sich auf `Agent Card`, `Task`, `Message`, `Part` und `Artifact`.
3.  **In Aktion sehen:** Sehen Sie sich das 🎥 [Offizielle Demo-Video](https://storage.googleapis.com/gweb-developer-goog-blog-assets/original_videos/A2A_demo_v4.mp4) an und erkunden Sie den Code für die 🌐 [Multi-Agent Web App Demo](https://github.com/google-a2a/A2A/tree/v0.2.1/demo).
4.  **Beispiele ausführen:** Klonen Sie das [Offizielle Beispiel-Repo](https://github.com/google-a2a/a2a-samples) und folgen Sie den dortigen Anweisungen, um einen Client (wie die CLI) und einen Beispiel-Agenten (z. B. LangGraph oder Genkit Agent) auszuführen.
5.  **Code überprüfen:** Sehen Sie sich die `common` (Python) oder `server`/`client` (JS/TS) Bibliotheken in den offiziellen Beispielen an, um zu sehen, wie die A2A-Kommunikation implementiert ist.
6.  **Versuchen Sie zu bauen:** Passen Sie ein Beispiel an oder verwenden Sie eine Bibliothek, um Ihren eigenen einfachen A2A-Agenten oder Client zu erstellen.

---

## 🏛️ Offizielle Ressourcen

*   📄 [A2A Protokoll Website](https://google.github.io/A2A) - Die Hauptdokumentationsseite.
*   💻 [google/A2A GitHub Repository](https://github.com/google/A2A) - Quellcode für die Spezifikation, Dokumente und offizielle Beispiele.
*   📰 [Google Developers Blogbeitrag](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) - Ankündigungs-Blogbeitrag, der die Motivation und Partner erklärt (Englisch).

## 📜 Spezifikation & Kernkonzepte

*(Zusammenfassungen finden Sie oben unter [Wie funktioniert A2A?](#️-wie-funktioniert-a2a-übersicht))*

*   📖 [A2A Technische Dokumentation](https://google-a2a.github.io/A2A/#/documentation) - **(Vollständige Details)** Detaillierte Erklärung von Akteuren, Transport, Authentifizierung, Kernobjekten (Task, Artifact, Message, Part), Agent Card usw.
*   📄 [JSON Spezifikation](https://github.com/google-a2a/A2A/tree/main/specification/json) - Die rohe JSON-Schemadefinition für A2A-Strukturen.
*   💡 [Schlüsselprinzipien (Docs)](https://google-a2a.github.io/A2A/#/documentation?id=key-principles) - Link zum Abschnitt über Prinzipien in der offiziellen Dokumentation.
*   🃏 [Agent Card Spezifikation (Docs)](https://google-a2a.github.io/A2A/#/documentation?id=agent-card) - Link zum Abschnitt über Agent Card in der offiziellen Dokumentation.
*   🗺️ [Agent Discovery (Thema)](https://google-a2a.github.io/A2A/#/topics/agent_discovery.md) - Diskussion darüber, wie Clients Agent Cards finden können.
*   🔔 [Push-Benachrichtigungen (Thema)](https://google-a2a.github.io/A2A/#/topics/push_notifications.md) - Details zum Push-Benachrichtigungsmechanismus.
*   🛡️ [Enterprise Readiness (Thema)](https://google-a2a.github.io/A2A/#/topics/enterprise_ready.md) - Diskussion über Aspekte wie Sicherheit, Authentifizierung und Datenschutz.

## ⚙️ Implementierungen & Bibliotheken

#### Offizielle Beispiele

*Diese demonstrieren grundlegende A2A Client/Server-Kommunikation.*

| Sprache           | Beispielname               | Kurzbeschreibung                                              | GitHub-URL                                                                                                                                                                              |
| ----------------- | -------------------------- | ------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🔷 **TypeScript** | Genkit SDK Core            | TS SDK + CLI erstellt gemeinsam genutzten Front-/Backend-Code | [https://github.com/google-a2a/a2a-samples/tree/main/samples/js](https://github.com/google-a2a/a2a-samples/tree/main/samples/js)                                                        |
|                   | Movie Recommendation Agent | Filmempfehlungs-Chat-Agent auf Basis von Genkit               | [https://github.com/google-a2a/a2a-samples/tree/main/samples/js/src/agents/movie-agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/js/src/agents/movie-agent)                                |
|                   | TypeScript Client          | Reines Frontend-Beispiel in TS                                | [https://github.com/google-a2a/a2a-samples/tree/main/samples/js/client](https://github.com/google-a2a/a2a-samples/tree/main/samples/js/client)                                          |
|                   | Node Express Server        | A2A-HTTP-Dienst mit Node/Express                              | [https://github.com/google-a2a/a2a-samples/tree/main/samples/js/server](https://github.com/google-a2a/a2a-samples/tree/main/samples/js/server)                                          |
| ☕ **Java**        | Java Client Demo           | Java-Client-Demo (mit Streaming-Listener)                     | [https://github.com/google-a2a/a2a-samples/tree/main/samples/java/client](https://github.com/google-a2a/a2a-samples/tree/main/samples/java/client)                                      |
|                   | Java Data Models           | Vollständige POJO-Datenmodelle für das Protokoll              | [https://github.com/google-a2a/a2a-samples/tree/main/samples/java/model](https://github.com/google-a2a/a2a-samples/tree/main/samples/java/model)                                        |
|                   | Java Server Impl           | Spring Boot-basierter A2A-Server                              | [https://github.com/google-a2a/a2a-samples/tree/main/samples/java/server](https://github.com/google-a2a/a2a-samples/tree/main/samples/java/server)                                      |
| 🐍 **Python**     | CLI Quickstart             | Einzeiler-CLI zum Testen einer A2A-Schleife                   | [https://github.com/google-a2a/a2a-samples/tree/main/samples](https://github.com/google-a2a/a2a-samples/tree/main/samples)                                                              |
|                   | Host Agent Service         | Einstiegspunkt zum Hosten & Steuern nachgelagerter Agents     | [https://github.com/google-a2a/a2a-samples/tree/main/samples/host\_agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/a2a-adk-app/host_agent)                                       |
|                   | Weather Agent              | Wetter-Agent + HTTP-Server                                    | [https://github.com/google-a2a/a2a-samples/tree/main/samples/weather\_agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/a2a-adk-app/weather_agent)                                 |
|                   | Minimal MCP                | Framework-freie Multi-Agent-Koordinierung                     | [https://github.com/google-a2a/a2a-samples/tree/main/samples/a2a-mcp-without-framework](https://github.com/google-a2a/a2a-samples/tree/main/samples/a2a-mcp-without-framework)          |
|                   | Travel Agency Agents       | Mehrere Agents für Reisebüro-Szenario                         | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/a2a_mcp)                                  |
|                   | A2A Telemetry              | Sammelt und zeigt Agent-Telemetriedaten                       | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/a2a\_telemetry](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/a2a_telemetry)                   |
|                   | AG2 Mini-Demo              | Minimales A↔A-Skeleton                                        | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/ag2](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/ag2)                                        |
|                   | Analytics Workflow         | Multi-Agent-Orchestrierung für Datenanalysen                  | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/analytics](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/analytics)                            |
|                   | Autogen Integration        | Nutzt Microsoft Autogen als Ausführungsumgebung               | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/autogen](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/autogen)                                |
|                   | Azure Foundry Agent        | Beispiel mit Azure AI Foundry SDK                             | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/azureaifoundry\_sdk](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/azureaifoundry_sdk)         |
|                   | Birthday Planner           | ADK-Version: mehrstufiger Geburtstags-Planer                  | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/birthday\_planner\_adk](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/birthday_planner_adk)    |
|                   | Calendar Agent             | Kalender lesen/schreiben, Termine buchen                      | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/calendar\_agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/birthday_planner_adk/calendar_agent)                 |
|                   | CrewAI Collab              | Mehrrollen-Zusammenarbeit mit CrewAI                          | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/crewai](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/crewai)                                  |
|                   | Google ADK Demo            | Offizielles Minimal-Demo zu Google ADK                        | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/google\_adk](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/google_adk)                         |
|                   | Headless OAuth2            | OAuth2-Flow für headless Agents                               | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/headless\_agent\_auth](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/headless_agent_auth)      |
|                   | Hello World                | Empfohlenes erstes „Hello World“-Gerüst                       | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/helloworld](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/helloworld)                          |
|                   | LangGraph Dialogue         | Multi-Turn-Dialog mit LangGraph orchestrieren                 | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/langgraph](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/langgraph)                            |
|                   | LlamaIndex File QA         | Q\&A-Suche über lokale Dateien                                | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/llama\_index\_file\_chat](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/llama_index_file_chat) |
|                   | Marvin Integration         | Domänenspezifische Agents mit Marvin                          | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/marvin](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/marvin)                                  |
|                   | MindsDB Predictor          | Aufrufe an MindsDB für Vorhersage & Abfrage                   | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/mindsdb](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/mindsdb)                                |
|                   | Semantic Kernel Orch       | Orchestrierung mit Semantic Kernel                            | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/semantickernel](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/semantickernel)                  |
|                   | Travel Planner             | All-in-one-Reiseplanungs-Agent                                | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/travel\_planner\_agent](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/travel_planner_agent)    |
|                   | Veo Video Generator        | Automatische Videoerstellung via Veo API                      | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/veo\_video\_gen](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/agents/veo_video_gen)                  |
|                   | Host Push Listener         | Host-Listener zum Verteilen eingehender Tasks                 | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/hosts](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/hosts)                                    |
|                   | Multi-Agent Orchestration  | Umfassendes Beispiel für Remote-Calls & Kooperation           | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/hosts/multiagent](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/hosts/multiagent)                          |
|                   | Common Utilities           | Gemeinsame Tools (Karten-Parsing, Client-Wrapper)             | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common)                                  |
|                   | Reference Server           | Python-Referenzserver + Task-Management                       | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common/server](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common/server)                                  |
|                   | Helper Scripts             | Allgemeine Skripte für Push-Auth usw.                         | [https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common/utils](https://github.com/google-a2a/a2a-samples/tree/main/samples/python/common/utils)                                    |
| 🐹 **Go**         | Go Reference Impl          | Vollständiger A2A-Server + Client in Go                       | [https://github.com/google-a2a/a2a-samples/tree/main/samples/go](https://github.com/google-a2a/a2a-samples/tree/main/samples/go)                                                        |

> **Schnellstart**
> Für den ersten Test empfehlen wir **TypeScript `Movie Recommendation Agent`**, **Python `Hello World`** oder **Go `Go Reference Impl`** – minimale Abhängigkeiten, schnell startklar.

#### Framework-Integrationen (Offizielle Beispiele)

*Diese zeigen, wie Agenten, die mit spezifischen Frameworks erstellt wurden, eine A2A-Schnittstelle bereitstellen können.*

| Sprache    | Agent Framework     | Agent Beschreibung                     | Demonstrierte A2A-Schlüsselfunktionen    | Link                                                                           |
| :--------- | :------------------ | :--------------------------------------- | :----------------------------------------- | :----------------------------------------------------------------------------- |
| 🐍 Python  | LangGraph           | Währungsumrechnung                       | Tools, Streaming, Multi-Turn             | [Link](https://github.com/google-a2a/A2A/tree/v0.2.1/samples/python/agents/langgraph) |
| 🐍 Python  | CrewAI              | Bilderzeugung                            | Nicht-textuelle Artefakte (Dateien)    | [Link](https://github.com/google-a2a/A2A/tree/v0.2.1/samples/python/agents/crewai)   |
| 🐍 Python  | Google ADK          | Spesenabrechnung                         | Multi-Turn, Formulare (DataPart)       | [Link](https://github.com/google-a2a/A2A/tree/v0.2.1/samples/python/agents/google_adk)|
| 🚀 JS/TS   | Genkit              | Filminfo / Code-Generierung              | Tools, Artefakte (Dateien), Asynchron    | [Link](https://github.com/google-a2a/A2A/tree/v0.2.1/samples/js/src/agents)          |

#### Community-Implementierungen

##### SDKs & Bibliotheken (nach Sprache)

*   **Go**
    *   🌟 [trpc-a2a-go](https://github.com/trpc-group/trpc-a2a-go) by [@trpc-group](https://github.com/trpc-group) [![Stars](https://img.shields.io/github/stars/trpc-group/trpc-a2a-go?style=social)](https://github.com/trpc-group/trpc-a2a-go) - A2A-Implementierung in Go vom tRPC-Team mit vollständiger Client/Server-Unterstützung, Memory-Task-Management, Streaming-Antworten, Session-Management und verschiedenen Authentifizierungsmethoden (JWT, API-Schlüssel, OAuth2). Enthält umfangreiche Beispiele einschließlich Basis-Server, Streaming und Authentifizierungsimplementierungen.
    *   🌟 [a2a-go](https://github.com/a2aserver/a2a-go) von [@a2aserver](https://github.com/a2aserver) [![Stars](https://img.shields.io/github/stars/a2aserver/a2a-go?style=social)](https://github.com/a2aserver/a2a-go) - Eine Go-Bibliothek zum Erstellen von A2A-Servern, mit Beispielimplementierungen.
    *  🌟 [a2a-go](https://github.com/yeeaiclub/a2a-go) by [@yeeaiclub](https://github.com/yeeaiclub) [![Stars](https://img.shields.io/github/stars/yeeaiclub/a2a-go?style=social)](https://github.com/yeeaiclub/a2a-go) - Agent-to-Agent-Protokoll-Implementierung für Go, unterstützt vollständig alle Methoden des A2A-Protokolls und basiert auf der offiziellen Python SDK-Implementierung.
*   **Rust**
    *   🌟 [a2a-rs](https://github.com/EmilLindfors/a2a-rs) von [@EmilLindfors](https://github.com/EmilLindfors) [![Stars](https://img.shields.io/github/stars/EmilLindfors/a2a-rs?style=social)](https://github.com/EmilLindfors/a2a-rs) - Eine idiomatische Rust-Implementierung nach den Prinzipien der hexagonalen Architektur.
    *   🌟 [Agentic](https://github.com/jeremychone/rust-agentic) by [@jeremychone](https://github.com/jeremychone) [![Stars](https://img.shields.io/github/stars/jeremychone/rust-agentic?style=social)](https://github.com/jeremychone/rust-agentic) - Eine Rust-Crate, die wesentliche Bausteine für agentische Anwendungen bereitstellt, mit einer ergonomischen API für MCP- und A2A-Unterstützung. (In Entwicklung)
*   **Python**
    *   🌟 [a2a-python](https://github.com/google/a2a-python) von [@google](https://github.com/google) [![Stars](https://img.shields.io/github/stars/google/a2a-python?style=social)](https://github.com/google/a2a-python) - **Offizielles** Python SDK zur Ausführung von agentischen Anwendungen als A2A-Server gemäß dem Agent2Agent-Protokoll.
    *   🌟 [a2a_min](https://github.com/pcingola/a2a_min) von [@pcingola](https://github.com/pcingola) [![Stars](https://img.shields.io/github/stars/pcingola/a2a_min?style=social)](https://github.com/pcingola/a2a_min) - Ein minimalistisches Python-SDK für die A2A-Kommunikation.
    *   🌟 [python-a2a](https://github.com/themanojdesai/python-a2a) by [@themanojdesai](https://github.com/themanojdesai) [![Stars](https://img.shields.io/github/stars/themanojdesai/python-a2a?style=social)](https://github.com/themanojdesai/python-a2a) - Eine einfach zu bedienende Python-Bibliothek zur Implementierung des A2A-Protokolls.
    *   🌟 [A2AServer](https://github.com/johnson7788/A2AServer) by [@johnson7788](https://github.com/johnson7788) [![Stars](https://img.shields.io/github/stars/johnson7788/A2AServer?style=social)](https://github.com/johnson7788/A2AServer) - Ein Python-Server-Framework, das das A2A-Protokoll von Google implementiert und MCP integriert.
    *   🌟 [adk-modular-architecture](https://github.com/k-jarzyna/adk-modular-architecture) by [@k-jarzyna](https://github.com/k-jarzyna) [![Stars](https://img.shields.io/github/stars/k-jarzyna/adk-modular-architecture?style=social)](https://github.com/k-jarzyna/adk-modular-architecture) - Ein Python-Projekt, das eine modulare Architektur für ADK (Agent Development Kit) basierte Agenten demonstriert, unter Berücksichtigung des A2A-Protokolls.
*   **C#/.NET**
    *   🌟 [a2adotnet](https://github.com/azixaka/a2adotnet) von [@azixaka](https://github.com/azixaka) [![Stars](https://img.shields.io/github/stars/azixaka/a2adotnet?style=social)](https://github.com/azixaka/a2adotnet) - Eine C#/.NET-Implementierung des A2A-Protokolls.
    *   🌟 [a2a-net](https://github.com/neuroglia-io/a2a-net) von [@neuroglia-io](https://github.com/neuroglia-io) [![Stars](https://img.shields.io/github/stars/neuroglia-io/a2a-net?style=social)](https://github.com/neuroglia-io/a2a-net) - .NET-Implementierung des Agent2Agent (A2A) Protokolls zur Ermöglichung sicherer, interoperabler Kommunikation zwischen autonomen Agenten über Frameworks und Anbieter hinweg.
*   **JavaScript/TypeScript**
    *   🌟 [nestjs-a2a](https://github.com/thestupd/nestjs-a2a) von [@thestupd](https://github.com/thestupd) [![Stars](https://img.shields.io/github/stars/thestupd/nestjs-a2a?style=social)](https://github.com/thestupd/nestjs-a2a) - Ein Modul zur Integration des A2A-Protokolls in NestJS-Anwendungen.
    *   🌟 [Artinet SDK](https://github.com/the-artinet-project/artinet-sdk) by [@the-artinet-project](https://github.com/the-artinet-project) [![Stars](https://img.shields.io/github/stars/the-artinet-project/artinet-sdk?style=social)](https://github.com/the-artinet-project/artinet-sdk) - TypeScript (Node.js) A2A-konformer Server/Client, der die Erstellung interoperabler KI-Agenten vereinfacht, mit Fokus auf DX und Produktionsreife.
*   **Java**
    *   🌟 [a2ajava](https://github.com/vishalmysore/a2ajava) by [@vishalmysore](https://github.com/vishalmysore) [![Stars](https://img.shields.io/github/stars/vishalmysore/a2ajava?style=social)](https://github.com/vishalmysore/a2ajava) - Java A2A server/client implementation using Spring Boot with annotations. Supports WebSockets, MCP integration, and includes enterprise/Kubernetes deployment tutorials.
    *   🌟 [a2a4j](https://github.com/a2ap/a2a4j) by [@a2ap](https://github.com/a2ap) [![Stars](https://img.shields.io/github/stars/a2ap/a2a4j?style=social)](https://github.com/a2ap/a2a4j) - A2A4J ist eine umfassende Java-Implementierung des Agent2Agent-Protokolls und umfasst Server, Client, Beispiele und einen Starter – sofort einsatzbereit.

##### Frameworks

*Entwicklerfreundliche Frameworks, die speziell für die Erstellung A2A-konformer Agenten entwickelt wurden.*

*   🚀 [AgentUp](https://github.com/RedDotRocket/AgentUp) by [@RedDotRocket](https://github.com/RedDotRocket) [![Stars](https://img.shields.io/github/stars/RedDotRocket/AgentUp?style=social)](https://github.com/RedDotRocket/AgentUp) - Ein entwicklerfreundliches, Open-Source-KI-Agent-Framework, das Agenten portabel, skalierbar und sicher macht. Bietet konfigurationsgesteuerte Architektur, integrierte OAuth2/JWT/API-Schlüssel-Authentifizierung, automatische A2A-Erkennung, asynchrone Aufgabenverwaltung und unterstützt sowohl A2A- als auch MCP-Protokolle. Entwickelt von Ingenieuren, die Open-Source-Lösungen für geschäftskritische Systeme bei Google, GitHub, Nvidia, Red Hat, Shopify und mehr erstellt haben.

##### Plattformen & Integrierte Lösungen

*   🌟 [Elkar](https://github.com/elkar-ai/elkar-a2a) by [@elkar-ai](https://github.com/elkar-ai) [![Stars](https://img.shields.io/github/stars/elkar-ai/elkar-a2a?style=social)](https://github.com/elkar-ai/elkar-a2a) - Eine Open-Source Aufgabenmanagement-Schicht für KI-Agenten – basierend auf dem Agent2Agent Protokoll (A2A) von Google. Senden, verfolgen und orchestrieren Sie Aufgaben über KI-Agenten hinweg – mühelos.
*   🌟 [Aira](https://github.com/IhateCreatingUserNames2/Aira) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Aira?style=social)](https://github.com/IhateCreatingUserNames2/Aira) - Eine A2A-Netzwerkimplementierung für Hosting, Registrierung, Entdeckung und Interaktion mit Agenten. Beinhaltet Agenten-Entdeckungsmechanismen.
*   🌟 [Cognisphere](https://github.com/IhateCreatingUserNames2/Cognisphere) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Cognisphere?style=social)](https://github.com/IhateCreatingUserNames2/Cognisphere) - Ein KI-Agenten-Entwicklungsframework, das auf Googles ADK basiert und die Erstellung von Agenten potenziell für A2A-Netzwerke erleichtert.
*   🌐 [Grasp](https://github.com/aircodelabs/grasp) by [@adcentury](https://github.com/adcentury) [![Stars](https://img.shields.io/github/stars/aircodelabs/grasp?style=social)](https://github.com/aircodelabs/grasp) - Ein selbstgehosteter Browser-Agent mit integrierter Unterstützung für MCP und A2A.
*   🌟 [swissknife](https://github.com/daltonnyx/swissknife) by [@daltonnyx](https://github.com/daltonnyx) [![Stars](https://img.shields.io/github/stars/daltonnyx/swissknife?style=social)](https://github.com/daltonnyx/swissknife) - Eine Multi-Agenten-Chat-Anwendung mit MCP-Unterstützung, die darauf abzielt, Agenten über das A2A-Protokoll bereitzustellen und sich als Client mit entfernten A2A-Agenten zu verbinden.
*   🌟 [n8n-nodes-agent2agent](https://github.com/pjawz/n8n-nodes-agent2agent) by [@pjawz](https://github.com/pjawz) [![Stars](https://img.shields.io/github/stars/pjawz/n8n-nodes-agent2agent?style=social)](https://github.com/pjawz/n8n-nodes-agent2agent) - Fügt n8n-Knoten hinzu, um über das Agent2Agent (A2A)-Protokoll von Google mit KI-Agenten zu interagieren.
*   🌟 [google-calendar-agent](https://github.com/inference-gateway/google-calendar-agent) by [@inference-gateway](https://github.com/inference-gateway) [![Stars](https://img.shields.io/github/stars/inference-gateway/google-calendar-agent?style=social)](https://github.com/inference-gateway/google-calendar-agent) - Ein eigenständiger A2A-Agent, der den Google Kalender eines Benutzers verwalten kann und mit jeder OpenAI-kompatiblen API für sein LLM kompatibel ist.
*   🌟 [A2AApp](https://github.com/tanaikech/A2AApp) by [@tanaikech](https://github.com/tanaikech) [![Stars](https://img.shields.io/github/stars/tanaikech/A2AApp?style=social)](https://github.com/tanaikech/A2AApp) - Ein mit Google Apps Script erstelltes Agent2Agent (A2A)-Netzwerk, das als A2A-Server und -Client sichere, dezentrale KI-Kommunikation und -Integration in Google Workspace ermöglicht.
<!-- Fügen Sie Ihre hier hinzu! Siehe CONTRIBUTING.md -->

## 🛠️ Tools & Dienstprogramme

Dieser Abschnitt listet eigenständige Tools und Dienstprogramme für das A2A-Protokoll auf. Das Ökosystem entwickelt sich noch, und Beiträge aus der Community sind willkommen!

*   **Agent Discovery Services (Agenten-Entdeckungsdienste)**
    *   Einige plattformbasierte Implementierungen (wie [Aira](https://github.com/IhateCreatingUserNames2/Aira)) beinhalten Mechanismen zur Registrierung und Entdeckung von Agenten.
    *   *Beiträge willkommen: Eigenständige Implementierungen von Agentenverzeichnisdiensten, Suchmaschinen für Agent Cards usw.* <!-- TODO: Beiträge aus der Community für verwandte Tools sind willkommen -->
*   **A2A Validierungstool**
    *   ⚙️ [A2A Validation Tool](https://github.com/llmx-de/a2a-validation-tool) by [@llmx-de](https://github.com/llmx-de) [![Stars](https://img.shields.io/github/stars/llmx-de/a2a-validation-tool?style=social)](https://github.com/llmx-de/a2a-validation-tool) - Plattformübergreifende Desktop-App zum Testen und Validieren von A2A-Protokollimplementierungen, mit Funktionen wie Multi-Agenten-Verbindung und Sitzungsmanagement.
    *   *Beiträge willkommen: Online- oder Kommandozeilen-Validatoren zur Prüfung, ob Agent Card-, Task-/Artifact-Strukturen den A2A JSON Schema-Spezifikationen entsprechen, oder IDE-Plugins usw.* <!-- TODO: Beiträge aus der Community für verwandte Tools sind willkommen -->
*   **Monitoring/Tracing Adapter**
    *   *Beiträge willkommen: Adapter oder Bibliotheken zur Integration von A2A-Task-Flow-Daten in gängige Monitoring-Plattformen wie OpenTelemetry, Prometheus, Grafana usw.* <!-- TODO: Beiträge aus der Community für verwandte Tools sind willkommen -->
*   **Weitere Dienstprogramme**
    *   *Beiträge willkommen: z.B. Hilfsprogramme zur Erstellung von A2A-Nachrichten, Generatoren für Agent Cards, Mock A2A Server/Client usw.* <!-- TODO: Beiträge aus der Community für verwandte Tools sind willkommen -->
    *   🌟 [autoa2a](https://github.com/NapthaAI/autoa2a) by [NapthaAI](https://github.com/NapthaAI) [![Stars](https://img.shields.io/github/stars/NapthaAI/autoa2a?style=social)](https://github.com/NapthaAI/autoa2a) - Einfache Konvertierung von Agenten und Orchestratoren aus bestehenden Agenten-Frameworks in A2A-Server.

## 📚 Tutorials & Artikel

*   📄 [Offizielle A2A Konzeptübersicht (README)](https://github.com/google/A2A#conceptual-overview) - Hochrangige Erklärung im README des offiziellen Repos.
*   🚀 [Erste Schritte Anleitung (Offizielles README)](https://github.com/google/A2A#getting-started) - Links zu Dokumenten, Spezifikationen, Beispielen im README des offiziellen Repos.
*   🌐 [Agent2Agent Protokoll Dokumentationsseite](https://agent2agent.ren) - Community-getriebene Open-Source-Dokumentationsseite für das A2A-Protokoll. Erstellt mit React/TypeScript, unterstützt Englisch, Chinesisch und Japanisch. ([Quellcode](https://github.com/ai-boost/agent2agent_doc))
*   📄 [A Survey of AI Agent Protocols](https://arxiv.org/pdf/2504.16736) - Wissenschaftlicher Artikel, der bestehende Kommunikationsprotokolle für LLM-Agenten (einschließlich der Kategorie, zu der A2A gehört) untersucht, klassifiziert, deren Leistung analysiert und zukünftige Herausforderungen diskutiert.
*   📚 [A2A und MCP Tutorial](https://github.com/Tsadoq/a2a-mcp-tutorial) von [@Tsadoq](https://github.com/Tsadoq) [![Stars](https://img.shields.io/github/stars/Tsadoq/a2a-mcp-tutorial?style=social)](https://github.com/Tsadoq/a2a-mcp-tutorial) - Ein Tutorial zur Verwendung des Model Context Protocol von Anthropic und des Agent2Agent Protocol von Google.

## 🎬 Demos & Beispiele

*   🌐 [Offizielle Multi-Agent Web App (Python/Mesop)](https://github.com/google-a2a/A2A/tree/v0.2.1/demo) - Demonstriert den Orchestrator-Agenten bei der Interaktion mit mehreren Remote-Agenten, Rendern von Text, Bildern und Formularen. **Erfordert die Ausführung von Python-Code.**
*   🎥 [Offizielles Demo-Video (Abschnittslink)](https://github.com/google/A2A#see-a2a-in-action) - Link zum Video, das im README des offiziellen Repositorys eingebettet ist.
*   💻 [Agent2Agent (A2A) Samples](https://github.com/google-a2a/a2a-samples) by [@google-a2a](https://github.com/google-a2a) [![Stars](https://img.shields.io/github/stars/google-a2a/a2a-samples?style=social)](https://github.com/google-a2a/a2a-samples) - Offizielles Repository mit Codebeispielen und Demos, die das Agent2Agent (A2A) Protokoll verwenden.

## 🔗 Verwandte Protokolle & Konzepte

*   📦 [Model Context Protocol (MCP)](https://github.com/modelcontextprotocol/servers) - Ergänzendes Protokoll, das sich darauf konzentriert, Tools/Kontext *für* Agenten bereitzustellen. ([A2A und MCP Diskussion](https://google-a2a.github.io/A2A/#/topics/a2a_and_mcp.md)).
*   📞 *Function Calling / Tool Use Standards* - *Beiträge willkommen: Diskussionen über Muster, Best Practices oder relevante Standards für Function Calling/Tool-Nutzung in Verbindung mit A2A.* <!-- TODO: Beiträge aus der Community für verwandte Standards oder Diskussionen sind willkommen -->

## 💬 Community

*   🐞 [google/A2A GitHub Issues](https://github.com/google-a2a/A2A/issues) - Zum Melden von Fehlern oder Vorschlagen von Protokollverbesserungen.
*   💬 [google/A2A GitHub Discussions](https://github.com/google-a2a/A2A/discussions/) - Für allgemeine Fragen, Ideen und Community-Diskussionen über das A2A-Protokoll.
*   🔒 [Privates Feedback-Formular](https://docs.google.com/forms/d/e/1FAIpQLScS23OMSKnVFmYeqS2dP7dxY3eTyT7lmtGLUa8OJZfP4RTijQ/viewform) - Google-Formular für privates Feedback.

---

**Lassen Sie uns Awesome A2A gemeinsam nützlicher machen!**

A2A ist noch recht neu, und gute Ressourcen oder praktische Erfahrungen sind oft verstreut. Wir haben diese Liste erstellt, um die guten Dinge zu sammeln und das Finden, Lernen und Nachschlagen zu erleichtern.

Um diese Liste aktuell und qualitativ hochwertig zu halten, sind wir auf die Hilfe der Community angewiesen:

*   ⭐ **Geben Sie einen Stern (Star)**: Wenn Sie die Liste nützlich finden, ist das eine tolle Unterstützung und erleichtert das Wiederfinden.
*   ➕ **Teilen Sie Ihre Funde**: Eine großartige Bibliothek, ein Artikel, ein Tool oder eine häufige Fehlerquelle (Pitfall) entdeckt? Fügen Sie es über ein [Issue](https://github.com/ai-boost/awesome-a2a/issues) oder einen [PR](CONTRIBUTING.md) hinzu – lassen Sie uns diese Ressource gemeinsam ausbauen.
*   📣 **Weitersagen**: Informieren Sie andere, die A2A erkunden oder damit arbeiten, über diese Liste.

Vielen Dank für Ihr Interesse und Ihre Beiträge!

---

## Beitragen

Beiträge sind willkommen! 🙌 Bitte lesen Sie zuerst die [Richtlinien für Beiträge](CONTRIBUTING.md). Lassen Sie uns diese Liste gemeinsam aufbauen!
