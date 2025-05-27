<div align="center">
  <h2 align="center">✨ Awesome A2A (Agent2Agent プロトコル) ✨</h2>
  <p align="center">
    <img src="assets/banner.png" alt="Awesome A2A バナー - 抽象的なネットワークまたは接続のグラフィック" width="600">
  </p>
  <p>
      <a href="README.md">English</a> | <a href="README_zh.md">简体中文</a> | <a href="README_ja.md">日本語</a> | <a href="README_es.md">Español</a> | <a href="README_de.md">Deutsch</a> | <a href="README_fr.md">Français</a>
      <!-- 他の言語リンクをここに追加します。例: | <a href="README_de.md">Deutsch</a> -->
  </p>
  <p align="center">
     Google Agent2Agent (A2A) プロトコルに関連する素晴らしいリソース、実装、ツール、および例のキュレーションリストです。AIエージェントの相互運用性を目的としています。
  </p>
  <h4 align="center">
    <a href="https://awesome.re">
      <img src="https://awesome.re/badge.svg" alt="Awesome" />
    </a>
    <a href="CONTRIBUTING.md"> <!-- コントリビュートファイルへのリンク -->
      <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square" alt="PRs Welcome" />
    </a>
  </h4>
</div>

---

## 目次

*   [🤔 A2Aとは？ (概要)](#-a2aとは-概要)
*   [💡 主要原則](#-主要原則)
*   [⚙️ A2Aの仕組み (ハイレベル)](#️-a2aの仕組み-ハイレベル)
*   [🚀 A2Aを始める](#-a2aを始める)
*   [🏛️ 公式リソース](#️-公式リソース)
*   [📜 仕様とコアコンセプト](#-仕様とコアコンセプト)
*   [⚙️ 実装とライブラリ](#️-実装とライブラリ)
    *   [公式サンプル](#公式サンプル)
    *   [フレームワーク統合 (公式サンプル)](#フレームワーク統合-公式サンプル)
    *   [コミュニティ実装](#コミュニティ実装)
        *   [SDKとライブラリ (言語別)](#sdkとライブラリ-言語別)
        *   [プラットフォームと統合ソリューション](#プラットフォームと統合ソリューション)
*   [🛠️ ツールとユーティリティ](#️-ツールとユーティリティ)
*   [📚 チュートリアルと記事](#-チュートリアルと記事)
*   [🎬 デモと例](#-デモと例)
*   [🔗 関連プロトコルとコンセプト](#-関連プロトコルとコンセプト)
*   [💬 コミュニティ](#-コミュニティ)
*   [コントリビュート](#コントリビュート)

---

## 🤔 A2Aとは？ (概要)

A2A (Agent2Agent) は、Google とパートナー企業による**オープンプロトコル**であり、さまざまな**AIエージェント**（異なるベンダー/フレームワークのもの）が**安全に通信**し、**タスクで協力**することを可能にします。隔離されたエージェントシステム間のサイロを打破し、より複雑なクロスアプリケーションの自動化を実現することを目指しています。

**⭐ 公式ウェブサイト:** [google.github.io/A2A](https://google.github.io/A2A) | **⭐ 公式 GitHub:** [github.com/google/A2A](https://github.com/google/A2A) | 🌐 **多言語ドキュメント (英/中/日):** [agent2agent.ren](https://agent2agent.ren)

## 💡 主要原則

*   **シンプル (Simple):** 既存の標準 (HTTP, JSON-RPC, SSE) を利用。
*   **エンタープライズ対応 (Enterprise Ready):** 認証、セキュリティ、プライバシー、モニタリングに焦点を当てる。
*   **非同期ファースト (Async First):** 長時間実行タスクや人間参加型ループを処理。
*   **モダリティ非依存 (Modality Agnostic):** テキスト、ファイル、フォーム、ストリームなどをサポート。
*   **不透明な実行 (Opaque Execution):** エージェントは内部ロジック/ツールを共有せずに相互作用。

## ⚙️ A2Aの仕組み (ハイレベル)

1.  **発見 (Discovery):** エージェントは、機能、エンドポイント、認証要件を記述した `Agent Card` (JSON) を公開します。
2.  **通信 (Communication):** `クライアント` エージェントは、HTTP/JSON-RPC 2.0 を使用して `リモートエージェント (サーバー)` に `Task` リクエスト（`Parts` を含む `Message` を格納）を送信します。
3.  **実行と応答 (Execution & Response):** サーバーはタスクを処理し、`status` を更新します。最終的なステータスと生成された `Artifacts` (結果、`Parts` も含む) で応答します。
4.  **更新 (Updates):** 長時間タスクの場合、サーバーはオプションで Server-Sent Events (SSE) 経由で `TaskStatusUpdateEvent` または `TaskArtifactUpdateEvent` をストリーミングするか、プッシュ通知を使用できます。

*詳細は [公式技術ドキュメント](https://google.github.io/A2A/#/documentation) を参照してください。*

---

## 🚀 A2Aを始める

A2Aは初めてですか？推奨される学習パスは次のとおりです：

1.  **基本を理解する：** 上記のセクション ([A2Aとは？](#-a2aとは-概要), [主要原則](#-主要原則), [仕組み](#️-a2aの仕組み-ハイレベル)) を読む。📰 [公式発表ブログ投稿](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) (英語) を確認する。
2.  **コアコンセプトを探る：** 📖 [公式技術ドキュメント](https://google.github.io/A2A/#/documentation) に深く入り込み、`Agent Card`、`Task`、`Message`、`Part`、`Artifact` に焦点を当てる。
3.  **動作を見る：** 🎥 [公式デモビデオ](https://storage.googleapis.com/gweb-developer-goog-blog-assets/original_videos/A2A_demo_v4.mp4) を視聴し、🌐 [マルチエージェント Web アプリデモ](https://github.com/google/A2A/tree/main/demo) のコードを探索する。
4.  **サンプルを実行する：** [公式リポジトリ](https://github.com/google/A2A) をクローンし、`/samples` の指示に従ってクライアント (CLI など) とサンプルエージェント (例: LangGraph または Genkit エージェント) を実行する。リンクについては、下の [公式サンプル](#公式サンプル) の表を参照。
5.  **コードを確認する：** 公式サンプルの `common` (Python) または `server`/`client` (JS/TS) ライブラリを見て、A2A 通信がどのように実装されているかを確認する。
6.  **構築してみる：** サンプルを適応させるか、ライブラリを使用して独自の基本的な A2A エージェントまたはクライアントを作成する。

---

## 🏛️ 公式リソース

*   📄 [A2A プロトコル ウェブサイト](https://google.github.io/A2A) - メインのドキュメントサイト。
*   💻 [google/A2A GitHub リポジトリ](https://github.com/google/A2A) - 仕様、ドキュメント、公式サンプルのソースコード。
*   📰 [Google Developers Blog 投稿](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) - 動機とパートナーを説明する発表ブログ投稿 (英語)。

## 📜 仕様とコアコンセプト

*(概要については、上記の [A2Aの仕組み](#️-a2aの仕組み-ハイレベル) を参照)*

*   📖 [A2A 技術ドキュメント](https://google.github.io/A2A/#/documentation) - **(詳細)** アクター、トランスポート、認証、コアオブジェクト (Task, Artifact, Message, Part)、Agent Card などの詳細な説明。
*   📄 [JSON 仕様](https://github.com/google/A2A/tree/main/specification/json) - A2A 構造の生の JSON スキーマ定義。
*   💡 [主要原則 (ドキュメント)](https://google.github.io/A2A/#/documentation?id=key-principles) - 公式ドキュメントの原則セクションへのリンク。
*   🃏 [Agent Card 仕様 (ドキュメント)](https://google.github.io/A2A/#/documentation?id=agent-card) - 公式ドキュメントの Agent Card セクションへのリンク。
*   🗺️ [エージェント発見 (トピック)](https://google.github.io/A2A/#/topics/agent_discovery.md) - クライアントが Agent Card を見つける方法についての議論。
*   🔔 [プッシュ通知 (トピック)](https://google.github.io/A2A/#/topics/push_notifications.md) - プッシュ通知メカニズムの詳細。
*   🛡️ [エンタープライズ対応 (トピック)](https://google.github.io/A2A/#/topics/enterprise_ready.md) - セキュリティ、認証、プライバシーの側面に関する議論。

## ⚙️ 実装とライブラリ

#### 公式サンプル

*これらは基本的な A2A クライアント/サーバー通信を示します。*

| 言語       | タイプ           | フレームワーク | 説明                                         | リンク                                                                            |
| :--------- | :--------------- | :------------- | :------------------------------------------- | :-------------------------------------------------------------------------------- |
| 🐍 Python  | 共通ライブラリ   | -              | コア HTTP, JSON-RPC, SSE ハンドリング        | [リンク](https://github.com/google/A2A/tree/main/samples/python/common)             |
| 🐍 Python  | ホスト (クライアント) | CLI          | コマンドラインクライアントの例                 | [リンク](https://github.com/google/A2A/tree/main/samples/python/hosts/cli)          |
| 🐍 Python  | ホスト (エージェント) | ADK          | 他の A2A エージェントに委任するオーケストレータエージェント | [リンク](https://github.com/google/A2A/tree/main/samples/python/hosts/multiagent)   |
| 🚀 JS/TS   | サーバーライブラリ | Express      | コアサーバー実装                             | [リンク](https://github.com/google/A2A/tree/main/samples/js/src/server)             |
| 🚀 JS/TS   | クライアントライブラリ | -            | クライアント実装                             | [リンク](https://github.com/google/A2A/tree/main/samples/js/src/client)             |
| 🚀 JS/TS   | ホスト (クライアント) | CLI          | コマンドラインクライアントの例                 | [リンク](https://github.com/google/A2A/blob/main/samples/js/src/cli.ts)             |

#### フレームワーク統合 (公式サンプル)

*これらは、特定のフレームワークで構築されたエージェントが A2A インターフェースをどのように公開できるかを示します。*

| 言語       | Agent フレームワーク | Agent 説明                           | 主要な A2A 機能のデモ                | リンク                                                                           |
| :--------- | :----------------- | :----------------------------------- | :----------------------------------- | :----------------------------------------------------------------------------- |
| 🐍 Python  | LangGraph          | 通貨換算                             | ツール、ストリーミング、マルチターン | [リンク](https://github.com/google/A2A/tree/main/samples/python/agents/langgraph) |
| 🐍 Python  | CrewAI             | 画像生成                             | 非テキスト Artifacts (ファイル)      | [リンク](https://github.com/google/A2A/tree/main/samples/python/agents/crewai)   |
| 🐍 Python  | Google ADK         | 経費精算                             | マルチターン、フォーム (DataPart)    | [リンク](https://github.com/google/A2A/tree/main/samples/python/agents/google_adk)|
| 🚀 JS/TS   | Genkit             | 映画情報 / コード生成                | ツール、Artifacts (ファイル)、非同期 | [リンク](https://github.com/google/A2A/tree/main/samples/js/src/agents)          |

#### コミュニティ実装

##### SDKとライブラリ (言語別)

*   **Go**
    *   🌟 [trpc-a2a-go](https://github.com/trpc-group/trpc-a2a-go) by [@trpc-group](https://github.com/trpc-group) [![Stars](https://img.shields.io/github/stars/trpc-group/trpc-a2a-go?style=social)](https://github.com/trpc-group/trpc-a2a-go) - tRPC チームによる Go 言語の A2A 実装。完全なクライアント/サーバーサポート、メモリタスク管理、ストリーミングレスポンス、セッション管理、および複数の認証方法（JWT、API キー、OAuth2）を提供。基本サーバー、ストリーミング、認証実装を含む豊富なサンプルを含みます。
    *   🌟 [a2a-go](https://github.com/a2aserver/a2a-go) by [@a2aserver](https://github.com/a2aserver) [![Stars](https://img.shields.io/github/stars/a2aserver/a2a-go?style=social)](https://github.com/a2aserver/a2a-go) - A2A サーバーを構築するための Go ライブラリと実装例。
*   **Rust**
    *   🌟 [a2a-rs](https://github.com/EmilLindfors/a2a-rs) by [@EmilLindfors](https://github.com/EmilLindfors) [![Stars](https://img.shields.io/github/stars/EmilLindfors/a2a-rs?style=social)](https://github.com/EmilLindfors/a2a-rs) - Rust の慣用的なプラクティスとヘキサゴナルアーキテクチャの原則に従った Rust 実装。
    *   🌟 [Agentic](https://github.com/jeremychone/rust-agentic) by [@jeremychone](https://github.com/jeremychone) [![Stars](https://img.shields.io/github/stars/jeremychone/rust-agentic?style=social)](https://github.com/jeremychone/rust-agentic) - MCP および A2A サポートのための人間工学に基づいた API を備え、エージェントアプリケーション開発に不可欠な構成要素を提供する Rust クレート。(開発中)
*   **Python**
    *   🌟 [a2a-python](https://github.com/google/a2a-python) by [@google](https://github.com/google) [![Stars](https://img.shields.io/github/stars/google/a2a-python?style=social)](https://github.com/google/a2a-python) - **公式** Python SDK。A2A プロトコルに従うエージェントアプリケーションの実行を支援。
    *   🌟 [a2a_min](https://github.com/pcingola/a2a_min) by [@pcingola](https://github.com/pcingola) [![Stars](https://img.shields.io/github/stars/pcingola/a2a_min?style=social)](https://github.com/pcingola/a2a_min) - A2A 通信のための最小限の Python SDK。
    *   🌟 [python-a2a](https://github.com/themanojdesai/python-a2a) by [@themanojdesai](https://github.com/themanojdesai) [![Stars](https://img.shields.io/github/stars/themanojdesai/python-a2a?style=social)](https://github.com/themanojdesai/python-a2a) - 実装が簡単な A2A プロトコル用 Python ライブラリ。
    *   🌟 [A2AServer](https://github.com/johnson7788/A2AServer) by [@johnson7788](https://github.com/johnson7788) [![Stars](https://img.shields.io/github/stars/johnson7788/A2AServer?style=social)](https://github.com/johnson7788/A2AServer) - Google の A2A プロトコルを実装し、MCP 統合を備えた Python サーバーフレームワーク。
*   **C#/.NET**
    *   🌟 [a2adotnet](https://github.com/azixaka/a2adotnet) by [@azixaka](https://github.com/azixaka) [![Stars](https://img.shields.io/github/stars/azixaka/a2adotnet?style=social)](https://github.com/azixaka/a2adotnet) - A2A プロトコルの C#/.NET 実装。
    *   🌟 [a2a-net](https://github.com/neuroglia-io/a2a-net) by [@neuroglia-io](https://github.com/neuroglia-io) [![Stars](https://img.shields.io/github/stars/neuroglia-io/a2a-net?style=social)](https://github.com/neuroglia-io/a2a-net) - フレームワークやベンダーを超えた自律エージェント間の安全で相互運用可能な通信を可能にする Agent2Agent (A2A) プロトコルの .NET 実装。
*   **JavaScript/TypeScript**
    *   🌟 [nestjs-a2a](https://github.com/thestupd/nestjs-a2a) by [@thestupd](https://github.com/thestupd) [![Stars](https://img.shields.io/github/stars/thestupd/nestjs-a2a?style=social)](https://github.com/thestupd/nestjs-a2a) - NestJS アプリケーションに A2A プロトコルを統合するためのモジュール。
    *   🌟 [Artinet SDK](https://github.com/the-artinet-project/artinet-sdk) by [@the-artinet-project](https://github.com/the-artinet-project) [![Stars](https://img.shields.io/github/stars/the-artinet-project/artinet-sdk?style=social)](https://github.com/the-artinet-project/artinet-sdk) - TypeScript (Node.js) A2A 準拠サーバー/クライアント。相互運用可能な AI エージェント作成を簡素化し、DX と本番運用性を重視。
*   **Java**
    *   🌟 [a2ajava](https://github.com/vishalmysore/a2ajava) by [@vishalmysore](https://github.com/vishalmysore) [![Stars](https://img.shields.io/github/stars/vishalmysore/a2ajava?style=social)](https://github.com/vishalmysore/a2ajava) - Java A2A server/client implementation using Spring Boot with annotations. Supports WebSockets, MCP integration, and includes enterprise/Kubernetes deployment tutorials.

##### プラットフォームと統合ソリューション

*   🌟 [Elkar](https://github.com/elkar-ai/elkar-a2a) by [@elkar-ai](https://github.com/elkar-ai) [![Stars](https://img.shields.io/github/stars/elkar-ai/elkar-a2a?style=social)](https://github.com/elkar-ai/elkar-a2a) - Google の Agent2Agent プロトコル (A2A) に基づく、AI エージェント向けのオープンソースのタスク管理レイヤー。AI エージェント間でタスクを簡単に送受信、追跡、調整します。
*   🌟 [Aira](https://github.com/IhateCreatingUserNames2/Aira) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Aira?style=social)](https://github.com/IhateCreatingUserNames2/Aira) - エージェントのホスティング、登録、発見、および対話のための A2A ネットワーク実装。エージェント発見メカニズムを含みます。
*   🌟 [Cognisphere](https://github.com/IhateCreatingUserNames2/Cognisphere) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Cognisphere?style=social)](https://github.com/IhateCreatingUserNames2/Cognisphere) - Google ADK 上に構築された AI エージェント開発フレームワーク、A2A ネットワーク用エージェント作成を促進。
*   🌐 [Grasp](https://github.com/aircodelabs/grasp) by [@adcentury](https://github.com/adcentury) [![Stars](https://img.shields.io/github/stars/aircodelabs/grasp?style=social)](https://github.com/aircodelabs/grasp) - MCPとA2Aをネイティブにサポートする、エージェント駆動のセルフホスト型ブラウザ。
*   🌟 [swissknife](https://github.com/daltonnyx/swissknife) by [@daltonnyx](https://github.com/daltonnyx) [![Stars](https://img.shields.io/github/stars/daltonnyx/swissknife?style=social)](https://github.com/daltonnyx/swissknife) - MCPをサポートするマルチエージェントチャットアプリケーション。A2Aプロトコル経由でエージェントを公開し、クライアントとしてリモートA2Aエージェントに接続することを目指しています。
<!-- あなたの実装をここに追加してください！CONTRIBUTING.md を参照してください。 -->

## 🛠️ ツールとユーティリティ

このセクションでは、A2A プロトコルに関連するスタンドアロンのツールやユーティリティをリストアップすることを目的としています。エコシステムはまだ発展途上であり、コミュニティからの貢献を歓迎します！

*   **エージェント発見サービス (Agent Discovery Services)**
    *   一部のプラットフォームレベルの実装（[Aira](https://github.com/IhateCreatingUserNames2/Aira) など）には、エージェントの登録と発見のメカニズムが機能に含まれています。
    *   *コミュニティからの貢献を歓迎します：スタンドアロンのエージェントディレクトリサービスの実装、Agent Card 検索エンジンなど。* <!-- TODO: 関連ツールのコミュニティ貢献を歓迎します -->
*   **A2A 検証ツール (A2A Validation Tool)**
    *   ⚙️ [A2A Validation Tool](https://github.com/llmx-de/a2a-validation-tool) by [@llmx-de](https://github.com/llmx-de) [![Stars](https://img.shields.io/github/stars/llmx-de/a2a-validation-tool?style=social)](https://github.com/llmx-de/a2a-validation-tool) - A2A プロトコル実装のテストと検証を行うためのクロスプラットフォームデスクトップアプリ。マルチエージェント接続やセッション管理などの機能を備えています。
    *   *コミュニティからの貢献を歓迎します：Agent Card、Task/Artifact 構造が A2A JSON スキーマ仕様に準拠しているかどうかを確認するためのオンラインまたはコマンドラインバリデータ、IDE プラグインなど。* <!-- TODO: 関連ツールのコミュニティ貢献を歓迎します -->
*   **モニタリング/トレース アダプター (Monitoring/Tracing Adapters)**
    *   *コミュニティからの貢献を歓迎します：A2A タスクフローデータを OpenTelemetry、Prometheus、Grafana などの主要な監視プラットフォームに統合するためのアダプタやライブラリ。* <!-- TODO: 関連ツールのコミュニティ貢献を歓迎します -->
*   **その他のユーティリティ (Other Utilities)**
    *   *コミュニティからの貢献を歓迎します：例えば、A2A メッセージ構築ヘルパーツール、Agent Card ジェネレータ、Mock A2A Server/Client など。* <!-- TODO: 関連ツールのコミュニティ貢献を歓迎します -->

## 📚 チュートリアルと記事

*   📄 [公式 A2A コンセプト概要 (README)](https://github.com/google/A2A#conceptual-overview) - 公式リポジトリの README でのハイレベルな説明。
*   🚀 [入門ガイド (公式 README)](https://github.com/google/A2A#getting-started) - 公式リポジトリの README 内のドキュメント、仕様、サンプルへのリンク。
*   🌐 [Agent2Agent プロトコル ドキュメントサイト](https://agent2agent.ren) - コミュニティ主導のオープンソース A2A プロトコル ドキュメントサイト。React/TypeScript で構築され、英語、中国語、日本語をサポート。([ソースコード](https://github.com/ai-boost/agent2agent_doc))
*   📄 [A Survey of AI Agent Protocols](https://arxiv.org/pdf/2504.16736) - 既存のLLMエージェント通信プロトコル（A2Aが属するカテゴリを含む）を調査し、分類、パフォーマンス分析、将来の課題について議論した学術論文。
*   📚 [A2A と MCP チュートリアル](https://github.com/Tsadoq/a2a-mcp-tutorial) by [@Tsadoq](https://github.com/Tsadoq) [![Stars](https://img.shields.io/github/stars/Tsadoq/a2a-mcp-tutorial?style=social)](https://github.com/Tsadoq/a2a-mcp-tutorial) - Anthropic の Model Context Protocol と Google の Agent2Agent Protocol の使い方に関するチュートリアル。

## 🎬 デモと例

*   🌐 [公式マルチエージェント Web アプリ (Python/Mesop)](https://github.com/google/A2A/tree/main/demo) - オーケストレータエージェントが複数のリモートエージェントと対話し、テキスト、画像、フォームをレンダリングするデモ。**Python コードの実行が必要です。**
*   🎥 [公式デモビデオ (セクションリンク)](https://github.com/google/A2A#see-a2a-in-action) - 公式リポジトリの README に埋め込まれたビデオへのリンク。

## 🔗 関連プロトコルとコンセプト

*   📦 [Model Context Protocol (MCP)](https://github.com/modelcontextprotocol/servers) - エージェント*に*ツール/コンテキストを提供することに焦点を当てた補完的なプロトコル。 ([A2A と MCP の議論](https://google.github.io/A2A/#/topics/a2a_and_mcp.md)).
*   📞 *関数呼び出し / ツール使用標準* - *コミュニティからの貢献を歓迎します：A2A と連携した関数呼び出し/ツール使用のパターン、ベストプラクティス、または関連標準に関する議論。* <!-- TODO: 関連する標準や議論に関するコミュニティの貢献を歓迎します -->

## 💬 コミュニティ

*   🐞 [google/A2A GitHub Issues](https://github.com/google/A2A/issues) - バグ報告やプロトコルの改善提案用。
*   💬 [google/A2A GitHub Discussions](https://github.com/google/A2A/discussions/) - A2A プロトコルに関する一般的な質問、アイデア、コミュニティの議論のため。
*   🔒 [プライベートフィードバックフォーム](https://docs.google.com/forms/d/e/1FAIpQLScS23OMSKnVFmYeqS2dP7dxY3eTyT7lmtGLUa8OJZfP4RTijQ/viewform) - プライベートなフィードバックのための Google フォーム。

---

**一緒に Awesome A2A をもっと役立つものにしましょう！**

A2A はまだ新しく、関連リソースや実践的な知見は分散しがちです。このリストは、良い情報を集約し、皆さんが簡単に見つけ、学び、参照できるように作成しました。

このリストの質を高く保つためには、コミュニティ一人ひとりの協力が不可欠です：

*   ⭐ **Star を付ける**: 役立つと思ったら、ぜひ。サポートになり、後で見つけやすくもなります。
*   ➕ **発見を共有**: 良いライブラリ、記事、ツール、あるいはハマった点などを見つけたら？ [Issue](https://github.com/ai-boost/awesome-a2a/issues) や [PR](CONTRIBUTING.md) で追加して、一緒に改善しましょう。
*   📣 **他の人に教える**: A2A を調査・利用している他の友人に、この場所を知らせましょう。

ご関心とご協力に感謝します！

---

## コントリビュート

コントリビューションは大歓迎です！ 🙌 最初に [コントリビューションガイドライン](CONTRIBUTING.md) をお読みください。一緒にこのリストを作り上げましょう！
