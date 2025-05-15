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

*Details finden Sie in der [Offiziellen Technischen Dokumentation](https://google.github.io/A2A/#/documentation).*

---

## 🚀 Erste Schritte mit A2A

Neu bei A2A? Hier ist ein empfohlener Weg:

1.  **Grundlagen verstehen:** Lesen Sie die obigen Abschnitte ([Was ist A2A?](#-was-ist-a2a-kurz), [Schlüsselprinzipien](#-schlüsselprinzipien), [Wie es funktioniert](#️-wie-funktioniert-a2a-übersicht)). Sehen Sie sich den 📰 [Ankündigungs-Blogbeitrag](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) (Englisch) an.
2.  **Kernkonzepte erkunden:** Tauchen Sie tief in die 📖 [Offizielle Technische Dokumentation](https://google.github.io/A2A/#/documentation) ein und konzentrieren Sie sich auf `Agent Card`, `Task`, `Message`, `Part` und `Artifact`.
3.  **In Aktion sehen:** Sehen Sie sich das 🎥 [Offizielle Demo-Video](https://storage.googleapis.com/gweb-developer-goog-blog-assets/original_videos/A2A_demo_v4.mp4) an und erkunden Sie den Code für die 🌐 [Multi-Agent Web App Demo](https://github.com/google/A2A/tree/main/demo).
4.  **Beispiele ausführen:** Klonen Sie das [Offizielle Repo](https://github.com/google/A2A) und folgen Sie den Anweisungen in `/samples`, um einen Client (wie die CLI) und einen Beispiel-Agenten (z. B. LangGraph oder Genkit Agent) auszuführen. Links finden Sie in den Tabellen der [Offiziellen Beispiele](#offizielle-beispiele) unten.
5.  **Code überprüfen:** Sehen Sie sich die `common` (Python) oder `server`/`client` (JS/TS) Bibliotheken in den offiziellen Beispielen an, um zu sehen, wie die A2A-Kommunikation implementiert ist.
6.  **Versuchen Sie zu bauen:** Passen Sie ein Beispiel an oder verwenden Sie eine Bibliothek, um Ihren eigenen einfachen A2A-Agenten oder Client zu erstellen.

---

## 🏛️ Offizielle Ressourcen

*   📄 [A2A Protokoll Website](https://google.github.io/A2A) - Die Hauptdokumentationsseite.
*   💻 [google/A2A GitHub Repository](https://github.com/google/A2A) - Quellcode für die Spezifikation, Dokumente und offizielle Beispiele.
*   📰 [Google Developers Blogbeitrag](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) - Ankündigungs-Blogbeitrag, der die Motivation und Partner erklärt (Englisch).

## 📜 Spezifikation & Kernkonzepte

*(Zusammenfassungen finden Sie oben unter [Wie funktioniert A2A?](#️-wie-funktioniert-a2a-übersicht))*

*   📖 [A2A Technische Dokumentation](https://google.github.io/A2A/#/documentation) - **(Vollständige Details)** Detaillierte Erklärung von Akteuren, Transport, Authentifizierung, Kernobjekten (Task, Artifact, Message, Part), Agent Card usw.
*   📄 [JSON Spezifikation](https://github.com/google/A2A/tree/main/specification/json) - Die rohe JSON-Schemadefinition für A2A-Strukturen.
*   💡 [Schlüsselprinzipien (Docs)](https://google.github.io/A2A/#/documentation?id=key-principles) - Link zum Abschnitt über Prinzipien in der offiziellen Dokumentation.
*   🃏 [Agent Card Spezifikation (Docs)](https://google.github.io/A2A/#/documentation?id=agent-card) - Link zum Abschnitt über Agent Card in der offiziellen Dokumentation.
*   🗺️ [Agent Discovery (Thema)](https://google.github.io/A2A/#/topics/agent_discovery.md) - Diskussion darüber, wie Clients Agent Cards finden können.
*   🔔 [Push-Benachrichtigungen (Thema)](https://google.github.io/A2A/#/topics/push_notifications.md) - Details zum Push-Benachrichtigungsmechanismus.
*   🛡️ [Enterprise Readiness (Thema)](https://google.github.io/A2A/#/topics/enterprise_ready.md) - Diskussion über Aspekte wie Sicherheit, Authentifizierung und Datenschutz.

## ⚙️ Implementierungen & Bibliotheken

#### Offizielle Beispiele

*Diese demonstrieren grundlegende A2A Client/Server-Kommunikation.*

| Sprache    | Typ                 | Framework   | Beschreibung                                | Link                                                                              |
| :--------- | :------------------ | :---------- | :------------------------------------------ | :-------------------------------------------------------------------------------- |
| 🐍 Python  | Common Library      | -           | Kernbehandlung von HTTP, JSON-RPC, SSE      | [Link](https://github.com/google/A2A/tree/main/samples/python/common)             |
| 🐍 Python  | Host (Client)       | CLI         | Beispiel für einen Befehlszeilen-Client       | [Link](https://github.com/google/A2A/tree/main/samples/python/hosts/cli)          |
| 🐍 Python  | Host (Agent)        | ADK         | Orchestrator-Agent, der an A2A-Agenten delegiert | [Link](https://github.com/google/A2A/tree/main/samples/python/hosts/multiagent)   |
| 🚀 JS/TS   | Server Library      | Express     | Kernimplementierung des Servers             | [Link](https://github.com/google/A2A/tree/main/samples/js/src/server)             |
| 🚀 JS/TS   | Client Library      | -           | Client-Implementierung                      | [Link](https://github.com/google/A2A/tree/main/samples/js/src/client)             |
| 🚀 JS/TS   | Host (Client)       | CLI         | Beispiel für einen Befehlszeilen-Client       | [Link](https://github.com/google/A2A/blob/main/samples/js/src/cli.ts)             |

#### Framework-Integrationen (Offizielle Beispiele)

*Diese zeigen, wie Agenten, die mit spezifischen Frameworks erstellt wurden, eine A2A-Schnittstelle bereitstellen können.*

| Sprache    | Agent Framework     | Agent Beschreibung                     | Demonstrierte A2A-Schlüsselfunktionen    | Link                                                                           |
| :--------- | :------------------ | :--------------------------------------- | :----------------------------------------- | :----------------------------------------------------------------------------- |
| 🐍 Python  | LangGraph           | Währungsumrechnung                       | Tools, Streaming, Multi-Turn             | [Link](https://github.com/google/A2A/tree/main/samples/python/agents/langgraph) |
| 🐍 Python  | CrewAI              | Bilderzeugung                            | Nicht-textuelle Artefakte (Dateien)    | [Link](https://github.com/google/A2A/tree/main/samples/python/agents/crewai)   |
| 🐍 Python  | Google ADK          | Spesenabrechnung                         | Multi-Turn, Formulare (DataPart)       | [Link](https://github.com/google/A2A/tree/main/samples/python/agents/google_adk)|
| 🚀 JS/TS   | Genkit              | Filminfo / Code-Generierung              | Tools, Artefakte (Dateien), Asynchron    | [Link](https://github.com/google/A2A/tree/main/samples/js/src/agents)          |

#### Community-Implementierungen

##### SDKs & Bibliotheken (nach Sprache)

*   **Go**
    *   🌟 [trpc-a2a-go](https://github.com/trpc-group/trpc-a2a-go) by [@trpc-group](https://github.com/trpc-group) [![Stars](https://img.shields.io/github/stars/trpc-group/trpc-a2a-go?style=social)](https://github.com/trpc-group/trpc-a2a-go) - A2A-Implementierung in Go vom tRPC-Team mit vollständiger Client/Server-Unterstützung, Memory-Task-Management, Streaming-Antworten, Session-Management und verschiedenen Authentifizierungsmethoden (JWT, API-Schlüssel, OAuth2). Enthält umfangreiche Beispiele einschließlich Basis-Server, Streaming und Authentifizierungsimplementierungen.
    *   🌟 [a2a-go](https://github.com/a2aserver/a2a-go) von [@a2aserver](https://github.com/a2aserver) [![Stars](https://img.shields.io/github/stars/a2aserver/a2a-go?style=social)](https://github.com/a2aserver/a2a-go) - Eine Go-Bibliothek zum Erstellen von A2A-Servern, mit Beispielimplementierungen.
*   **Rust**
    *   🌟 [a2a-rs](https://github.com/EmilLindfors/a2a-rs) von [@EmilLindfors](https://github.com/EmilLindfors) [![Stars](https://img.shields.io/github/stars/EmilLindfors/a2a-rs?style=social)](https://github.com/EmilLindfors/a2a-rs) - Eine idiomatische Rust-Implementierung nach den Prinzipien der hexagonalen Architektur.
    *   🌟 [Agentic](https://github.com/jeremychone/rust-agentic) by [@jeremychone](https://github.com/jeremychone) [![Stars](https://img.shields.io/github/stars/jeremychone/rust-agentic?style=social)](https://github.com/jeremychone/rust-agentic) - Eine Rust-Crate, die wesentliche Bausteine für agentische Anwendungen bereitstellt, mit einer ergonomischen API für MCP- und A2A-Unterstützung. (In Entwicklung)
*   **Python**
    *   🌟 [a2a_min](https://github.com/pcingola/a2a_min) von [@pcingola](https://github.com/pcingola) [![Stars](https://img.shields.io/github/stars/pcingola/a2a_min?style=social)](https://github.com/pcingola/a2a_min) - Ein minimalistisches Python-SDK für die A2A-Kommunikation.
    *   🌟 [python-a2a](https://github.com/themanojdesai/python-a2a) by [@themanojdesai](https://github.com/themanojdesai) [![Stars](https://img.shields.io/github/stars/themanojdesai/python-a2a?style=social)](https://github.com/themanojdesai/python-a2a) - Eine einfach zu bedienende Python-Bibliothek zur Implementierung des A2A-Protokolls.
*   **C#/.NET**
    *   🌟 [a2adotnet](https://github.com/azixaka/a2adotnet) von [@azixaka](https://github.com/azixaka) [![Stars](https://img.shields.io/github/stars/azixaka/a2adotnet?style=social)](https://github.com/azixaka/a2adotnet) - Eine C#/.NET-Implementierung des A2A-Protokolls.
*   **JavaScript/TypeScript**
    *   🌟 [nestjs-a2a](https://github.com/thestupd/nestjs-a2a) von [@thestupd](https://github.com/thestupd) [![Stars](https://img.shields.io/github/stars/thestupd/nestjs-a2a?style=social)](https://github.com/thestupd/nestjs-a2a) - Ein Modul zur Integration des A2A-Protokolls in NestJS-Anwendungen.
    *   🌟 [Artinet SDK](https://github.com/the-artinet-project/artinet-sdk) by [@the-artinet-project](https://github.com/the-artinet-project) - Ein Agent2Agent (A2A) Protokoll-konformer Server und Client in TypeScript für node.js, der die Erstellung interoperabler KI-Agenten vereinfacht. Erweitert Googles Beispiele erheblich und bietet eine produktionsreife Lösung mit Fokus auf Entwicklererfahrung, Zuverlässigkeit und umfassende Funktionen. [Erfahren Sie mehr beim Artinet-Projekt](https://www.artinet.com/).
*   **Java**
    *   🌟 [a2ajava](https://github.com/vishalmysore/a2ajava) by [@vishalmysore](https://github.com/vishalmysore) [![Stars](https://img.shields.io/github/stars/vishalmysore/a2ajava?style=social)](https://github.com/vishalmysore/a2ajava) - Java A2A server/client implementation using Spring Boot with annotations. Supports WebSockets, MCP integration, and includes enterprise/Kubernetes deployment tutorials.

##### Plattformen & Integrierte Lösungen

*   🌟 [Elkar](https://github.com/elkar-ai/elkar-a2a) by [@elkar-ai](https://github.com/elkar-ai) [![Stars](https://img.shields.io/github/stars/elkar-ai/elkar-a2a?style=social)](https://github.com/elkar-ai/elkar-a2a) - Eine Open-Source Aufgabenmanagement-Schicht für KI-Agenten – basierend auf dem Agent2Agent Protokoll (A2A) von Google. Senden, verfolgen und orchestrieren Sie Aufgaben über KI-Agenten hinweg – mühelos.
*   🌟 [Aira](https://github.com/IhateCreatingUserNames2/Aira) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Aira?style=social)](https://github.com/IhateCreatingUserNames2/Aira) - Eine A2A-Netzwerkimplementierung für Hosting, Registrierung, Entdeckung und Interaktion mit Agenten. Beinhaltet Agenten-Entdeckungsmechanismen.
*   🌟 [Cognisphere](https://github.com/IhateCreatingUserNames2/Cognisphere) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Cognisphere?style=social)](https://github.com/IhateCreatingUserNames2/Cognisphere) - Ein KI-Agenten-Entwicklungsframework, das auf Googles ADK basiert und die Erstellung von Agenten potenziell für A2A-Netzwerke erleichtert.
*   🌐 [Grasp](https://github.com/aircodelabs/grasp) by [@adcentury](https://github.com/adcentury) [![Stars](https://img.shields.io/github/stars/aircodelabs/grasp?style=social)](https://github.com/aircodelabs/grasp) - Ein selbstgehosteter Browser-Agent mit integrierter Unterstützung für MCP und A2A.
*   🌟 [swissknife](https://github.com/daltonnyx/swissknife) by [@daltonnyx](https://github.com/daltonnyx) [![Stars](https://img.shields.io/github/stars/daltonnyx/swissknife?style=social)](https://github.com/daltonnyx/swissknife) - Eine Multi-Agenten-Chat-Anwendung mit MCP-Unterstützung, die darauf abzielt, Agenten über das A2A-Protokoll bereitzustellen und sich als Client mit entfernten A2A-Agenten zu verbinden.
<!-- Fügen Sie Ihre hier hinzu! Siehe CONTRIBUTING.md -->

## 🛠️ Tools & Dienstprogramme

Dieser Abschnitt listet eigenständige Tools und Dienstprogramme für das A2A-Protokoll auf. Das Ökosystem entwickelt sich noch, und Beiträge aus der Community sind willkommen!

*   **Agent Discovery Services (Agenten-Entdeckungsdienste)**
    *   Einige plattformbasierte Implementierungen (wie [Aira](https://github.com/IhateCreatingUserNames2/Aira)) beinhalten Mechanismen zur Registrierung und Entdeckung von Agenten.
    *   *Beiträge willkommen: Eigenständige Implementierungen von Agentenverzeichnisdiensten, Suchmaschinen für Agent Cards usw.* <!-- TODO: Beiträge aus der Community für verwandte Tools sind willkommen -->
*   **A2A Validierungstool**
    *   ⚙️ [A2A Validation Tool](https://github.com/llmx-de/a2a-validation-tool) by [@llmx-de](https://github.com/llmx-de) - Eine Desktop-Anwendung zum Testen und Validieren von A2A-Protokollimplementierungen. Sie unterstützt Multi-Agenten-Verbindungen, Agent Card-Inspektion, Streaming, Sitzungsmanagement, Dateianhänge, JSON-Visualisierung, Konfigurationsimport/-export und ist plattformübergreifend.
    *   *Beiträge willkommen: Online- oder Kommandozeilen-Validatoren zur Prüfung, ob Agent Card-, Task-/Artifact-Strukturen den A2A JSON Schema-Spezifikationen entsprechen, oder IDE-Plugins usw.* <!-- TODO: Beiträge aus der Community für verwandte Tools sind willkommen -->
*   **Monitoring/Tracing Adapter**
    *   *Beiträge willkommen: Adapter oder Bibliotheken zur Integration von A2A-Task-Flow-Daten in gängige Monitoring-Plattformen wie OpenTelemetry, Prometheus, Grafana usw.* <!-- TODO: Beiträge aus der Community für verwandte Tools sind willkommen -->
*   **Weitere Dienstprogramme**
    *   *Beiträge willkommen: z.B. Hilfsprogramme zur Erstellung von A2A-Nachrichten, Generatoren für Agent Cards, Mock A2A Server/Client usw.* <!-- TODO: Beiträge aus der Community für verwandte Tools sind willkommen -->

## 📚 Tutorials & Artikel

*   📄 [Offizielle A2A Konzeptübersicht (README)](https://github.com/google/A2A#conceptual-overview) - Hochrangige Erklärung im README des offiziellen Repos.
*   🚀 [Erste Schritte Anleitung (Offizielles README)](https://github.com/google/A2A#getting-started) - Links zu Dokumenten, Spezifikationen, Beispielen im README des offiziellen Repos.
*   🌐 [Agent2Agent Protokoll Dokumentationsseite](https://agent2agent.ren) - Community-getriebene Open-Source-Dokumentationsseite für das A2A-Protokoll. Erstellt mit React/TypeScript, unterstützt Englisch, Chinesisch und Japanisch. ([Quellcode](https://github.com/ai-boost/agent2agent_doc))
*   📄 [A Survey of AI Agent Protocols](https://arxiv.org/pdf/2504.16736) - Wissenschaftlicher Artikel, der bestehende Kommunikationsprotokolle für LLM-Agenten (einschließlich der Kategorie, zu der A2A gehört) untersucht, klassifiziert, deren Leistung analysiert und zukünftige Herausforderungen diskutiert.

## 🎬 Demos & Beispiele

*   🌐 [Offizielle Multi-Agent Web App (Python/Mesop)](https://github.com/google/A2A/tree/main/demo) - Demonstriert den Orchestrator-Agenten bei der Interaktion mit mehreren Remote-Agenten, Rendern von Text, Bildern und Formularen. **Erfordert die Ausführung von Python-Code.**
*   🎥 [Offizielles Demo-Video (Abschnittslink)](https://github.com/google/A2A#see-a2a-in-action) - Link zum Video, das im README des offiziellen Repositorys eingebettet ist.

## 🔗 Verwandte Protokolle & Konzepte

*   📦 [Model Context Protocol (MCP)](https://github.com/modelcontextprotocol/servers) - Ergänzendes Protokoll, das sich darauf konzentriert, Tools/Kontext *für* Agenten bereitzustellen. ([A2A und MCP Diskussion](https://google.github.io/A2A/#/topics/a2a_and_mcp.md)).
*   📞 *Function Calling / Tool Use Standards* - *Beiträge willkommen: Diskussionen über Muster, Best Practices oder relevante Standards für Function Calling/Tool-Nutzung in Verbindung mit A2A.* <!-- TODO: Beiträge aus der Community für verwandte Standards oder Diskussionen sind willkommen -->

## 💬 Community

*   🐞 [google/A2A GitHub Issues](https://github.com/google/A2A/issues) - Zum Melden von Fehlern oder Vorschlagen von Protokollverbesserungen.
*   💬 [google/A2A GitHub Discussions](https://github.com/google/A2A/discussions/) - Für allgemeine Fragen, Ideen und Community-Diskussionen über das A2A-Protokoll.
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
