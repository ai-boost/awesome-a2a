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
*   [🛠️ Tools & Dienstprogramme](#️-tools--dienstprogramme)
*   [📚 Tutorials & Artikel](#-tutorials--artikel)
*   [🎬 Demos & Beispiele](#-demos--beispiele)
*   [🔗 Verwandte Protokolle & Konzepte](#-verwandte-protokolle--konzepte)
*   [💬 Community](#-community)
*   [Beitragen](#beitragen)

---

## 🤔 Was ist A2A? (Kurz)

A2A (Agent2Agent) ist ein **offenes Protokoll** von Google und Partnern, das es verschiedenen **KI-Agenten** (von unterschiedlichen Anbietern/Frameworks) ermöglicht, **sicher zu kommunizieren** und **bei Aufgaben zusammenzuarbeiten**. Ziel ist es, Silos zwischen isolierten Agentensystemen aufzubrechen und komplexere, anwendungsübergreifende Automatisierungen zu ermöglichen.

**⭐ Offizielle Website:** [google.github.io/A2A](https://google.github.io/A2A) | **⭐ Offizielles GitHub:** [github.com/google/A2A](https://github.com/google/A2A)

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

*   🌟 _Ihre Framework/Sprache A2A Server/Client Bibliothek?_ - Fügen Sie sie hier hinzu! Siehe [CONTRIBUTING.md](CONTRIBUTING.md).
<!-- TODO: Community-Implementierungen hinzufügen -->

## 🛠️ Tools & Dienstprogramme

*   🔍 *Agent Discovery Services* - [Link] - Beschreibung (z.B. Implementierung eines 'Agent Katalogs'). <!-- TODO -->
*   ✅ *A2A Validierungstool* - [Link] - Tool zur Prüfung der Konformität eines A2A-Endpunkts. <!-- TODO -->
*   📊 *Monitoring/Tracing Adapter* - [Link] - Integrationen für Observability-Plattformen. <!-- TODO -->

## 📚 Tutorials & Artikel

*   📄 [Offizielle A2A Konzeptübersicht (README)](https://github.com/google/A2A#conceptual-overview) - Hochrangige Erklärung im README des offiziellen Repos.
*   🚀 [Erste Schritte Anleitung (Offizielles README)](https://github.com/google/A2A#getting-started) - Links zu Dokumenten, Spezifikationen, Beispielen im README des offiziellen Repos.
*   ✍️ *[Blogbeitrag/Tutorial Titel]* - [Link] - Beschreibung. <!-- TODO: Community-Artikel/Anleitungen hier hinzufügen -->

## 🎬 Demos & Beispiele

*   🌐 [Offizielle Multi-Agent Web App (Python/Mesop)](https://github.com/google/A2A/tree/main/demo) - Demonstriert den Orchestrator-Agenten bei der Interaktion mit mehreren Remote-Agenten, Rendern von Text, Bildern und Formularen. **Erfordert die Ausführung von Python-Code.**
*   🎥 [Offizielles Demo-Video (Abschnittslink)](https://github.com/google/A2A#see-a2a-in-action) - Link zum Video, das im README des offiziellen Repositorys eingebettet ist.

## 🔗 Verwandte Protokolle & Konzepte

*   📦 [Model Context Protocol (MCP)](https://github.com/modelcontextprotocol/servers) - Ergänzendes Protokoll, das sich darauf konzentriert, Tools/Kontext *für* Agenten bereitzustellen. ([A2A und MCP Diskussion](https://google.github.io/A2A/#/topics/a2a_and_mcp.md)).
*   📞 *Function Calling / Tool Use Standards* - [Link] - Relevante Standards (z. B. OpenAI Function Calling). <!-- TODO -->

## 💬 Community

*   🐞 [google/A2A GitHub Issues](https://github.com/google/A2A/issues) - Zum Melden von Fehlern oder Vorschlagen von Protokollverbesserungen.
*   💬 [google/A2A GitHub Discussions](https://github.com/google/A2A/discussions/) - Für allgemeine Fragen, Ideen und Community-Diskussionen über das A2A-Protokoll.
*   🔒 [Privates Feedback-Formular](https://docs.google.com/forms/d/e/1FAIpQLScS23OMSKnVFmYeqS2dP7dxY3eTyT7lmtGLUa8OJZfP4RTijQ/viewform) - Google-Formular für privates Feedback.

---

## Beitragen

Beiträge sind willkommen! 🙌 Bitte lesen Sie zuerst die [Richtlinien für Beiträge](CONTRIBUTING.md). Lassen Sie uns diese Liste gemeinsam aufbauen!