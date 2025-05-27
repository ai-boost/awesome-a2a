<div align="center">
  <h2 align="center">✨ Awesome A2A (Protocole Agent2Agent) ✨</h2>
  <p align="center">
    <img src="assets/banner.png" alt="Bannière Awesome A2A - Graphique abstrait de réseau ou de connexion" width="600">
  </p>
  <p>
      <a href="README.md">English</a> | <a href="README_zh.md">简体中文</a> | <a href="README_ja.md">日本語</a> | <a href="README_es.md">Español</a> | <a href="README_de.md">Deutsch</a> | <a href="README_fr.md">Français</a>
      <!-- Ajoutez d'autres langues ici -->
  </p>
  <p align="center">
     Une liste organisée de ressources, implémentations, outils et exemples géniaux liés au protocole Google Agent2Agent (A2A) pour l'interopérabilité des agents IA.
  </p>
  <h4 align="center">
    <a href="https://awesome.re">
      <img src="https://awesome.re/badge.svg" alt="Awesome" />
    </a>
    <a href="CONTRIBUTING.md"> <!-- Lien vers votre fichier de contribution -->
      <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square" alt="PRs Bienvenues" />
    </a>
  </h4>
</div>


## Table des matières

*   [🤔 Qu'est-ce que l'A2A ? (Brièvement)](#-quest-ce-que-la2a--brièvement)
*   [💡 Principes Clés](#-principes-clés)
*   [⚙️ Comment fonctionne l'A2A ? (Haut Niveau)](#️-comment-fonctionne-la2a--haut-niveau)
*   [🚀 Démarrer avec A2A](#-démarrer-avec-a2a)
*   [🏛️ Ressources Officielles](#️-ressources-officielles)
*   [📜 Spécification & Concepts Fondamentaux](#-spécification--concepts-fondamentaux)
*   [⚙️ Implémentations & Bibliothèques](#️-implémentations--bibliothèques)
    *   [Exemples Officiels](#exemples-officiels)
    *   [Intégrations de Frameworks (Exemples Officiels)](#intégrations-de-frameworks-exemples-officiels)
    *   [Implémentations Communautaires](#implémentations-communautaires)
        *   [SDK et Bibliothèques (par langue)](#sdk-et-bibliothèques-par-langue)
        *   [Plateformes et Solutions Intégrées](#plateformes-et-solutions-intégrées)
*   [🛠️ Outils & Utilitaires](#️-outils--utilitaires)
*   [📚 Tutoriels & Articles](#-tutoriels--articles)
*   [🎬 Démos & Exemples](#-démos--exemples)
*   [🔗 Protocoles & Concepts Connexes](#-protocoles--concepts-connexes)
*   [💬 Communauté](#-communauté)
*   [Contribuer](#contribuer)

---

## 🤔 Qu'est-ce que l'A2A ? (Brièvement)

A2A (Agent2Agent) est un **protocole ouvert** de Google et de ses partenaires permettant à différents **agents IA** (provenant de divers fournisseurs/frameworks) de **communiquer en toute sécurité** et de **collaborer sur des tâches**. Il vise à briser les silos entre les systèmes d'agents isolés, permettant une automatisation inter-applications plus complexe.

**⭐ Site Web Officiel :** [google.github.io/A2A](https://google.github.io/A2A) | **⭐ GitHub Officiel :** [github.com/google/A2A](https://github.com/google/A2A) | 🌐 **Docs Multilingues (EN/ZH/JA) :** [agent2agent.ren](https://agent2agent.ren)

## 💡 Principes Clés

*   **Simple :** Utilise des standards existants (HTTP, JSON-RPC, SSE).
*   **Prêt pour l'Entreprise (Enterprise Ready) :** Met l'accent sur l'Authentification, la Sécurité, la Confidentialité, la Supervision.
*   **Asynchrone d'Abord (Async First) :** Gère les tâches longues et l'intervention humaine (human-in-the-loop).
*   **Indépendant de la Modalité (Modality Agnostic) :** Prend en charge le Texte, les Fichiers, les Formulaires, les Flux (Streams), etc.
*   **Exécution Opaque :** Les agents interagissent sans partager leur logique/outils internes.

## ⚙️ Comment fonctionne l'A2A ? (Haut Niveau)

1.  **Découverte (Discovery) :** Les agents publient une `Agent Card` (JSON) décrivant leurs capacités, leur point d'accès (endpoint) et leurs besoins d'authentification.
2.  **Communication :** Un agent `Client` envoie une requête `Task` (contenant un `Message` avec des `Parts`) à un `Agent Distant (Serveur)` en utilisant HTTP/JSON-RPC 2.0.
3.  **Exécution & Réponse :** Le Serveur traite la tâche, mettant à jour son `status`. Il répond avec le statut final et tous les `Artifacts` générés (résultats, contenant également des `Parts`).
4.  **Mises à jour :** Pour les tâches longues, le Serveur peut éventuellement diffuser en continu `TaskStatusUpdateEvent` ou `TaskArtifactUpdateEvent` via Server-Sent Events (SSE) ou utiliser des Notifications Push.

*Pour plus de détails, consultez la [Documentation Technique Officielle](https://google.github.io/A2A/#/documentation).*

---

## 🚀 Démarrer avec A2A

Nouveau sur A2A ? Voici un parcours suggéré :

1.  **Comprendre les Bases :** Lisez les sections ci-dessus ([Qu'est-ce que l'A2A ?](#-quest-ce-que-la2a--brièvement), [Principes Clés](#-principes-clés), [Comment ça marche](#️-comment-fonctionne-la2a--haut-niveau)). Consultez le 📰 [Billet de Blog d'Annonce](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) (en anglais).
2.  **Explorer les Concepts Fondamentaux :** Plongez dans la 📖 [Documentation Technique Officielle](https://google.github.io/A2A/#/documentation), en vous concentrant sur `Agent Card`, `Task`, `Message`, `Part`, et `Artifact`.
3.  **Voir en Action :** Regardez la 🎥 [Vidéo de Démo Officielle](https://storage.googleapis.com/gweb-developer-goog-blog-assets/original_videos/A2A_demo_v4.mp4) et explorez le code de la 🌐 [Démo Web Multi-Agent](https://github.com/google/A2A/tree/main/demo).
4.  **Exécuter les Exemples :** Clonez le [Repo Officiel](https://github.com/google/A2A) et suivez les instructions dans `/samples` pour exécuter un client (comme le CLI) et un agent d'exemple (par ex., agent LangGraph ou Genkit). Consultez les tableaux des [Exemples Officiels](#exemples-officiels) ci-dessous pour les liens.
5.  **Examiner le Code :** Regardez les bibliothèques `common` (Python) ou `server`/`client` (JS/TS) dans les exemples officiels pour voir comment la communication A2A est implémentée.
6.  **Essayer de Construire :** Adaptez un exemple ou utilisez une bibliothèque pour créer votre propre agent ou client A2A de base.

---

## 🏛️ Ressources Officielles

*   📄 [Site Web du Protocole A2A](https://google.github.io/A2A) - Le site principal de la documentation.
*   💻 [Dépôt GitHub google/A2A](https://github.com/google/A2A) - Code source de la spécification, de la documentation et des exemples officiels.
*   📰 [Billet de Blog Google Developers](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) - Billet de blog d'annonce expliquant la motivation et les partenaires (en anglais).

## 📜 Spécification & Concepts Fondamentaux

*(Voir [Comment fonctionne l'A2A ?](#️-comment-fonctionne-la2a--haut-niveau) ci-dessus pour des résumés)*

*   📖 [Documentation Technique A2A](https://google.github.io/A2A/#/documentation) - **(Détails Complets)** Explication détaillée des acteurs, du transport, de l'authentification, des objets fondamentaux (Task, Artifact, Message, Part), de l'Agent Card, etc.
*   📄 [Spécification JSON](https://github.com/google/A2A/tree/main/specification/json) - La définition brute du schéma JSON pour les structures A2A.
*   💡 [Principes Clés (Docs)](https://google.github.io/A2A/#/documentation?id=key-principles) - Lien vers la section des principes dans la documentation officielle.
*   🃏 [Spécification Agent Card (Docs)](https://google.github.io/A2A/#/documentation?id=agent-card) - Lien vers la section Agent Card dans la documentation officielle.
*   🗺️ [Découverte d'Agents (Sujet)](https://google.github.io/A2A/#/topics/agent_discovery.md) - Discussion sur la manière dont les clients peuvent trouver des Agent Cards.
*   🔔 [Notifications Push (Sujet)](https://google.github.io/A2A/#/topics/push_notifications.md) - Détails sur le mécanisme de notification push.
*   🛡️ [Prêt pour l'Entreprise (Sujet)](https://google.github.io/A2A/#/topics/enterprise_ready.md) - Discussion sur les aspects de sécurité, d'authentification et de confidentialité.

## ⚙️ Implémentations & Bibliothèques

#### Exemples Officiels

*Ceux-ci démontrent la communication client/serveur A2A de base.*

| Langage    | Type                 | Framework   | Description                                      | Lien                                                                              |
| :--------- | :------------------- | :---------- | :----------------------------------------------- | :-------------------------------------------------------------------------------- |
| 🐍 Python  | Bibliothèque Commune | -           | Gestion centrale HTTP, JSON-RPC, SSE           | [Lien](https://github.com/google/A2A/tree/main/samples/python/common)             |
| 🐍 Python  | Hôte (Client)        | CLI         | Exemple de client en ligne de commande           | [Lien](https://github.com/google/A2A/tree/main/samples/python/hosts/cli)          |
| 🐍 Python  | Hôte (Agent)         | ADK         | Agent orchestrateur déléguant aux agents A2A     | [Lien](https://github.com/google/A2A/tree/main/samples/python/hosts/multiagent)   |
| 🚀 JS/TS   | Bibliothèque Serveur | Express     | Implémentation centrale du serveur               | [Lien](https://github.com/google/A2A/tree/main/samples/js/src/server)             |
| 🚀 JS/TS   | Bibliothèque Client  | -           | Implémentation du client                         | [Lien](https://github.com/google/A2A/tree/main/samples/js/src/client)             |
| 🚀 JS/TS   | Hôte (Client)        | CLI         | Exemple de client en ligne de commande           | [Lien](https://github.com/google/A2A/blob/main/samples/js/src/cli.ts)             |

#### Intégrations de Frameworks (Exemples Officiels)

*Ceux-ci montrent comment les agents construits avec des frameworks spécifiques peuvent exposer une interface A2A.*

| Langage    | Framework Agent     | Description de l'Agent                 | Fonctionnalités A2A Clés Démontrées     | Lien                                                                           |
| :--------- | :------------------ | :--------------------------------------- | :---------------------------------------- | :----------------------------------------------------------------------------- |
| 🐍 Python  | LangGraph           | Conversion de devises                  | Outils, Streaming, Multi-tours          | [Lien](https://github.com/google/A2A/tree/main/samples/python/agents/langgraph) |
| 🐍 Python  | CrewAI              | Génération d'images                    | Artefacts non textuels (Fichiers)       | [Lien](https://github.com/google/A2A/tree/main/samples/python/agents/crewai)   |
| 🐍 Python  | Google ADK          | Remboursement de frais                 | Multi-tours, Formulaires (DataPart)     | [Lien](https://github.com/google/A2A/tree/main/samples/python/agents/google_adk)|
| 🚀 JS/TS   | Genkit              | Infos films / Génération de code       | Outils, Artefacts (Fichiers), Asynchrone | [Lien](https://github.com/google/A2A/tree/main/samples/js/src/agents)          |

#### Implémentations Communautaires

##### SDK et Bibliothèques (par langue)

*   **Go**
    *   🌟 [trpc-a2a-go](https://github.com/trpc-group/trpc-a2a-go) par [@trpc-group](https://github.com/trpc-group) [![Stars](https://img.shields.io/github/stars/trpc-group/trpc-a2a-go?style=social)](https://github.com/trpc-group/trpc-a2a-go) - Implémentation A2A en Go développée par l'équipe tRPC, offrant un support client/serveur complet, gestion des tâches en mémoire, réponses en streaming, gestion de session et plusieurs méthodes d'authentification (JWT, clé API, OAuth2). Inclut de nombreux exemples, notamment de serveur de base, streaming et implémentations d'authentification.
    *   🌟 [a2a-go](https://github.com/a2aserver/a2a-go) par [@a2aserver](https://github.com/a2aserver) [![Stars](https://img.shields.io/github/stars/a2aserver/a2a-go?style=social)](https://github.com/a2aserver/a2a-go) - Une bibliothèque Go pour construire des serveurs A2A, avec des exemples d'implémentation.
*   **Rust**
    *   🌟 [a2a-rs](https://github.com/EmilLindfors/a2a-rs) par [@EmilLindfors](https://github.com/EmilLindfors) [![Stars](https://img.shields.io/github/stars/EmilLindfors/a2a-rs?style=social)](https://github.com/EmilLindfors/a2a-rs) - Une implémentation idiomatique en Rust suivant les principes de l'architecture hexagonale.
    *   🌟 [Agentic](https://github.com/jeremychone/rust-agentic) by [@jeremychone](https://github.com/jeremychone) [![Stars](https://img.shields.io/github/stars/jeremychone/rust-agentic?style=social)](https://github.com/jeremychone/rust-agentic) - Une crate Rust fournissant des blocs de construction essentiels pour les applications agentiques, avec une API ergonomique pour le support MCP et A2A. (En cours de développement)
*   **Python**
    *   🌟 [a2a-python](https://github.com/google/a2a-python) par [@google](https://github.com/google) [![Stars](https://img.shields.io/github/stars/google/a2a-python?style=social)](https://github.com/google/a2a-python) - SDK Python **officiel** pour exécuter des applications agentiques en tant que serveurs A2A suivant le protocole Agent2Agent.
    *   🌟 [a2a_min](https://github.com/pcingola/a2a_min) par [@pcingola](https://github.com/pcingola) [![Stars](https://img.shields.io/github/stars/pcingola/a2a_min?style=social)](https://github.com/pcingola/a2a_min) - Un SDK Python minimaliste pour la communication A2A.
    *   🌟 [python-a2a](https://github.com/themanojdesai/python-a2a) by [@themanojdesai](https://github.com/themanojdesai) [![Stars](https://img.shields.io/github/stars/themanojdesai/python-a2a?style=social)](https://github.com/themanojdesai/python-a2a) - Une bibliothèque Python facile à utiliser pour implémenter le protocole A2A.
    *   🌟 [A2AServer](https://github.com/johnson7788/A2AServer) by [@johnson7788](https://github.com/johnson7788) [![Stars](https://img.shields.io/github/stars/johnson7788/A2AServer?style=social)](https://github.com/johnson7788/A2AServer) - Un framework serveur Python implémentant le protocole A2A de Google avec intégration MCP.
*   **C#/.NET**
    *   🌟 [a2adotnet](https://github.com/azixaka/a2adotnet) par [@azixaka](https://github.com/azixaka) [![Stars](https://img.shields.io/github/stars/azixaka/a2adotnet?style=social)](https://github.com/azixaka/a2adotnet) - Une implémentation C#/.NET du protocole A2A.
    *   🌟 [a2a-net](https://github.com/neuroglia-io/a2a-net) par [@neuroglia-io](https://github.com/neuroglia-io) [![Stars](https://img.shields.io/github/stars/neuroglia-io/a2a-net?style=social)](https://github.com/neuroglia-io/a2a-net) - Implémentation .NET du protocole Agent2Agent (A2A) pour permettre une communication sécurisée et interopérable entre agents autonomes à travers différents frameworks et fournisseurs.
*   **JavaScript/TypeScript**
    *   🌟 [nestjs-a2a](https://github.com/thestupd/nestjs-a2a) par [@thestupd](https://github.com/thestupd) [![Stars](https://img.shields.io/github/stars/thestupd/nestjs-a2a?style=social)](https://github.com/thestupd/nestjs-a2a) - Un module pour intégrer le protocole A2A dans les applications NestJS.
    *   🌟 [Artinet SDK](https://github.com/the-artinet-project/artinet-sdk) by [@the-artinet-project](https://github.com/the-artinet-project) [![Stars](https://img.shields.io/github/stars/the-artinet-project/artinet-sdk?style=social)](https://github.com/the-artinet-project/artinet-sdk) - Serveur/client A2A conforme en TypeScript (Node.js) simplifiant la création d'agents IA interopérables, axé sur l'DX et la préparation à la production.
*   **Java**
    *   🌟 [a2ajava](https://github.com/vishalmysore/a2ajava) by [@vishalmysore](https://github.com/vishalmysore) [![Stars](https://img.shields.io/github/stars/vishalmysore/a2ajava?style=social)](https://github.com/vishalmysore/a2ajava) - Java A2A server/client implementation using Spring Boot with annotations. Supports WebSockets, MCP integration, and includes enterprise/Kubernetes deployment tutorials.

##### Plateformes et Solutions Intégrées

*   🌟 [Elkar](https://github.com/elkar-ai/elkar-a2a) by [@elkar-ai](https://github.com/elkar-ai) [![Stars](https://img.shields.io/github/stars/elkar-ai/elkar-a2a?style=social)](https://github.com/elkar-ai/elkar-a2a) - Une couche open-source de gestion des tâches pour les agents IA — basée sur le protocole Agent2Agent (A2A) de Google. Envoyez, suivez et orchestrez les tâches entre les agents IA — sans effort.
*   🌟 [Aira](https://github.com/IhateCreatingUserNames2/Aira) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Aira?style=social)](https://github.com/IhateCreatingUserNames2/Aira) - Une implémentation de réseau A2A pour l'hébergement, l'enregistrement, la découverte et l'interaction avec les agents. Inclut des mécanismes de découverte d'agents.
*   🌟 [Cognisphere](https://github.com/IhateCreatingUserNames2/Cognisphere) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Cognisphere?style=social)](https://github.com/IhateCreatingUserNames2/Cognisphere) - Un framework de développement d'agents IA basé sur l'ADK de Google, facilitant la création d'agents potentiellement pour les réseaux A2A.
*   🌐 [Grasp](https://github.com/aircodelabs/grasp) by [@adcentury](https://github.com/adcentury) [![Stars](https://img.shields.io/github/stars/aircodelabs/grasp?style=social)](https://github.com/aircodelabs/grasp) - Un agent de navigation auto-hébergé avec prise en charge native de MCP et A2A.
*   🌟 [swissknife](https://github.com/daltonnyx/swissknife) by [@daltonnyx](https://github.com/daltonnyx) [![Stars](https://img.shields.io/github/stars/daltonnyx/swissknife?style=social)](https://github.com/daltonnyx/swissknife) - Une application de chat multi-agents avec prise en charge MCP, visant à exposer des agents via le protocole A2A et à se connecter à des agents A2A distants en tant que client.
<!-- Ajoutez la vôtre ici ! Voir CONTRIBUTING.md -->

## 🛠️ Outils & Utilitaires

Cette section vise à lister les outils et utilitaires autonomes liés au protocole A2A. L'écosystème est encore en développement, et les contributions de la communauté sont les bienvenues !

*   **Services de Découverte d'Agents**
    *   Certaines implémentations au niveau plateforme (comme [Aira](https://github.com/IhateCreatingUserNames2/Aira)) incluent des mécanismes d'enregistrement et de découverte d'agents dans leurs fonctionnalités.
    *   *Contributions communautaires bienvenues : Implémentations de services d'annuaire d'agents autonomes, moteurs de recherche d'Agent Cards, etc.* <!-- TODO : Les contributions de la communauté pour les outils associés sont les bienvenues -->
*   **Outil de Validation A2A**
    *   ⚙️ [A2A Validation Tool](https://github.com/llmx-de/a2a-validation-tool) by [@llmx-de](https://github.com/llmx-de) [![Stars](https://img.shields.io/github/stars/llmx-de/a2a-validation-tool?style=social)](https://github.com/llmx-de/a2a-validation-tool) - Application de bureau multiplateforme pour tester et valider les implémentations du protocole A2A, avec des fonctionnalités telles que la connexion multi-agents et la gestion de session.
    *   *Contributions communautaires bienvenues : Validateurs en ligne ou en ligne de commande pour vérifier si les structures Agent Card, Task/Artifact sont conformes aux spécifications JSON Schema A2A, ou plugins IDE, etc.* <!-- TODO : Les contributions de la communauté pour les outils associés sont les bienvenues -->
*   **Adaptateurs de Supervision/Traçage**
    *   *Contributions communautaires bienvenues : Adaptateurs ou bibliothèques pour intégrer les données de flux de tâches A2A dans les plateformes de supervision courantes comme OpenTelemetry, Prometheus, Grafana, etc.* <!-- TODO : Les contributions de la communauté pour les outils associés sont les bienvenues -->
*   **Autres Utilitaires**
    *   *Contributions communautaires bienvenues : par ex., outils d'aide à la construction de messages A2A, générateurs d'Agent Cards, Mock A2A Server/Client, etc.* <!-- TODO : Les contributions de la communauté pour les outils associés sont les bienvenues -->

## 📚 Tutoriels & Articles

*   📄 [Aperçu Conceptuel Officiel A2A (README)](https://github.com/google/A2A#conceptual-overview) - Explication de haut niveau dans le README du dépôt officiel.
*   🚀 [Guide de Démarrage Rapide (README Officiel)](https://github.com/google/A2A#getting-started) - Liens vers la documentation, la spécification, les exemples dans le README du dépôt officiel.
*   🌐 [Site de Documentation du Protocole Agent2Agent](https://agent2agent.ren) - Site de documentation open-source communautaire pour le protocole A2A. Construit avec React/TypeScript, prend en charge l'anglais, le chinois et le japonais. ([Code Source](https://github.com/ai-boost/agent2agent_doc))
*   📄 [A Survey of AI Agent Protocols](https://arxiv.org/pdf/2504.16736) - Article académique examinant les protocoles de communication existants pour les agents LLM (y compris la catégorie dont A2A fait partie), les classifiant, analysant leurs performances et discutant des défis futurs.
*   📚 [Tutoriel A2A et MCP](https://github.com/Tsadoq/a2a-mcp-tutorial) par [@Tsadoq](https://github.com/Tsadoq) [![Stars](https://img.shields.io/github/stars/Tsadoq/a2a-mcp-tutorial?style=social)](https://github.com/Tsadoq/a2a-mcp-tutorial) - Un tutoriel sur comment utiliser le Model Context Protocol d'Anthropic et le Agent2Agent Protocol de Google.

## 🎬 Démos & Exemples

*   🌐 [Démo Web Multi-Agent Officielle (Python/Mesop)](https://github.com/google/A2A/tree/main/demo) - Démontre l'agent orchestrateur interagissant avec plusieurs agents distants, affichant du texte, des images et des formulaires. **Nécessite l'exécution de code Python.**
*   🎥 [Vidéo de Démo Officielle (Lien Section)](https://github.com/google/A2A#see-a2a-in-action) - Lien vers la vidéo intégrée dans le README du dépôt officiel.

## 🔗 Protocoles & Concepts Connexes

*   📦 [Model Context Protocol (MCP)](https://github.com/modelcontextprotocol/servers) - Protocole complémentaire axé sur la fourniture d'outils/contexte *aux* agents. ([Discussion A2A et MCP](https://google.github.io/A2A/#/topics/a2a_and_mcp.md)).
*   📞 *Standards d'Appel de Fonction / Utilisation d'Outils* - *Contributions communautaires bienvenues : Discussion sur les modèles, les meilleures pratiques ou les normes pertinentes pour l'appel de fonctions/l'utilisation d'outils conjointement avec A2A.* <!-- TODO : Les contributions de la communauté pour les normes ou discussions associées sont les bienvenues -->

## 💬 Communauté

*   🐞 [Issues GitHub google/A2A](https://github.com/google/A2A/issues) - Pour signaler des bugs ou suggérer des améliorations du protocole.
*   💬 [Discussions GitHub google/A2A](https://github.com/google/A2A/discussions/) - Pour les questions générales, les idées et les discussions communautaires sur le protocole A2A.
*   🔒 [Formulaire de Feedback Privé](https://docs.google.com/forms/d/e/1FAIpQLScS23OMSKnVFmYeqS2dP7dxY3eTyT7lmtGLUa8OJZfP4RTijQ/viewform) - Formulaire Google pour un feedback privé.

---

**Rendons Awesome A2A plus utile, ensemble !**

A2A est encore assez nouveau, et les bonnes ressources ou les retours d'expérience pratiques peuvent être dispersés. Nous avons créé cette liste pour rassembler les meilleures trouvailles et faciliter la recherche, l'apprentissage et la consultation.

Maintenir cette liste à jour et de haute qualité dépend de l'aide de toute la communauté :

*   ⭐ **Mettez une étoile (Star)** : Si vous la trouvez utile, c'est un excellent moyen de montrer votre soutien et cela facilite sa consultation ultérieure.
*   ➕ **Partagez vos découvertes** : Une super bibliothèque, un article, un outil, ou même un écueil fréquent ? Ajoutez-le via une [Issue](https://github.com/ai-boost/awesome-a2a/issues) ou un [PR](CONTRIBUTING.md) – construisons cette ressource ensemble.
*   📣 **Faites passer le mot** : Informez les autres qui explorent ou travaillent avec A2A de l'existence de cette liste.

Merci pour votre intérêt et vos contributions !

---

## Contribuer

Les contributions sont les bienvenues ! 🙌 Veuillez d'abord lire les [directives de contribution](CONTRIBUTING.md). Construisons cette liste ensemble !
