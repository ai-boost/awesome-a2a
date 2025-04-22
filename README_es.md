<div align="center">
  <h2 align="center">✨ Awesome A2A (Protocolo Agent2Agent) ✨</h2>
  <p align="center">
    <img src="assets/banner.png" alt="Banner de Awesome A2A - Gráfico abstracto de red o conexión" width="600">
  </p>
  <p>
      <a href="README.md">English</a> | <a href="README_zh.md">简体中文</a> | <a href="README_ja.md">日本語</a> | <a href="README_es.md">Español</a> | <a href="README_de.md">Deutsch</a> | <a href="README_fr.md">Français</a>
      <!-- Añade otros idiomas aquí -->
  </p>
  <p align="center">
     Una lista curada de recursos, implementaciones, herramientas y ejemplos impresionantes relacionados con el Protocolo Google Agent2Agent (A2A) para la interoperabilidad de agentes de IA.
  </p>
  <h4 align="center">
    <a href="https://awesome.re">
      <img src="https://awesome.re/badge.svg" alt="Awesome" />
    </a>
    <a href="CONTRIBUTING.md"> <!-- Enlace a tu archivo de contribución -->
      <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square" alt="PRs Bienvenidos" />
    </a>
  </h4>
</div>


## Contenido

*   [🤔 ¿Qué es A2A? (Brevemente)](#-qué-es-a2a-brevemente)
*   [💡 Principios Clave](#-principios-clave)
*   [⚙️ ¿Cómo funciona A2A? (Alto Nivel)](#️-cómo-funciona-a2a-alto-nivel)
*   [🚀 Empezando con A2A](#-empezando-con-a2a)
*   [🏛️ Recursos Oficiales](#️-recursos-oficiales)
*   [📜 Especificación y Conceptos Centrales](#-especificación-y-conceptos-centrales)
*   [⚙️ Implementaciones y Bibliotecas](#️-implementaciones-y-bibliotecas)
    *   [Ejemplos Oficiales](#ejemplos-oficiales)
    *   [Integraciones de Frameworks (Ejemplos Oficiales)](#integraciones-de-frameworks-ejemplos-oficiales)
    *   [Implementaciones de la Comunidad](#implementaciones-de-la-comunidad)
*   [🛠️ Herramientas y Utilidades](#️-herramientas-y-utilidades)
*   [📚 Tutoriales y Artículos](#-tutoriales-y-artículos)
*   [🎬 Demos y Ejemplos](#-demos-y-ejemplos)
*   [🔗 Protocolos y Conceptos Relacionados](#-protocolos-y-conceptos-relacionados)
*   [💬 Comunidad](#-comunidad)
*   [Contribuir](#contribuir)

---

## 🤔 ¿Qué es A2A? (Brevemente)

A2A (Agent2Agent) es un **protocolo abierto** de Google y socios que permite a diferentes **agentes de IA** (de varios proveedores/frameworks) **comunicarse de forma segura** y **colaborar en tareas**. Su objetivo es romper los silos entre sistemas de agentes aislados, permitiendo una automatización más compleja entre aplicaciones.

**⭐ Sitio Web Oficial:** [google.github.io/A2A](https://google.github.io/A2A) | **⭐ GitHub Oficial:** [github.com/google/A2A](https://github.com/google/A2A) | 🌐 **Docs Multilingües (EN/ZH/JA):** [agent2agent.ren](https://agent2agent.ren)

## 💡 Principios Clave

*   **Simple:** Utiliza estándares existentes (HTTP, JSON-RPC, SSE).
*   **Listo para Empresas (Enterprise Ready):** Se enfoca en Autenticación, Seguridad, Privacidad, Monitorización.
*   **Asíncrono Primero (Async First):** Maneja tareas de larga duración y la intervención humana (human-in-the-loop).
*   **Agnóstico a la Modalidad (Modality Agnostic):** Soporta Texto, Archivos, Formularios, Streams, etc.
*   **Ejecución Opaca (Opaque Execution):** Los agentes interactúan sin compartir lógica/herramientas internas.

## ⚙️ ¿Cómo funciona A2A? (Alto Nivel)

1.  **Descubrimiento (Discovery):** Los agentes publican una `Agent Card` (JSON) describiendo capacidades, endpoint y necesidades de autenticación.
2.  **Comunicación:** Un agente `Cliente` envía una solicitud `Task` (conteniendo un `Message` con `Parts`) a un `Agente Remoto (Servidor)` usando HTTP/JSON-RPC 2.0.
3.  **Ejecución y Respuesta:** El Servidor procesa la tarea, actualizando su `status`. Responde con el estado final y cualquier `Artifact` generado (resultados, también conteniendo `Parts`).
4.  **Actualizaciones:** Para tareas largas, el Servidor puede opcionalmente transmitir `TaskStatusUpdateEvent` o `TaskArtifactUpdateEvent` vía Server-Sent Events (SSE) o usar Notificaciones Push.

*Para detalles, consulta la [Documentación Técnica Oficial](https://google.github.io/A2A/#/documentation).*

---

## 🚀 Empezando con A2A

¿Nuevo en A2A? Aquí tienes una ruta sugerida:

1.  **Entiende lo Básico:** Lee las secciones anteriores ([¿Qué es A2A?](#-qué-es-a2a-brevemente), [Principios Clave](#-principios-clave), [Cómo funciona](#️-cómo-funciona-a2a-alto-nivel)). Revisa la 📰 [Entrada del Blog del Anuncio](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) (en inglés).
2.  **Explora Conceptos Centrales:** Sumérgete en la 📖 [Documentación Técnica Oficial](https://google.github.io/A2A/#/documentation), enfocándote en `Agent Card`, `Task`, `Message`, `Part`, y `Artifact`.
3.  **Velo en Acción:** Mira el 🎥 [Video Demo Oficial](https://storage.googleapis.com/gweb-developer-goog-blog-assets/original_videos/A2A_demo_v4.mp4) y explora el código de la 🌐 [Demo Web Multi-Agente](https://github.com/google/A2A/tree/main/demo).
4.  **Ejecuta los Ejemplos:** Clona el [Repo Oficial](https://github.com/google/A2A) y sigue las instrucciones en `/samples` para ejecutar un cliente (como el CLI) y un agente de ejemplo (ej., agente LangGraph o Genkit). Consulta las tablas de [Ejemplos Oficiales](#ejemplos-oficiales) abajo para los enlaces.
5.  **Revisa el Código:** Mira las bibliotecas `common` (Python) o `server`/`client` (JS/TS) en los ejemplos oficiales para ver cómo se implementa la comunicación A2A.
6.  **Intenta Construir:** Adapta un ejemplo o usa una biblioteca para crear tu propio agente o cliente A2A básico.

---

## 🏛️ Recursos Oficiales

*   📄 [Sitio Web del Protocolo A2A](https://google.github.io/A2A) - El sitio principal de documentación.
*   💻 [Repositorio GitHub google/A2A](https://github.com/google/A2A) - Código fuente de la especificación, documentos y ejemplos oficiales.
*   📰 [Entrada del Blog de Google Developers](https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/) - Entrada del blog del anuncio explicando la motivación y los socios (en inglés).

## 📜 Especificación y Conceptos Centrales

*(Consulta [¿Cómo funciona A2A?](#️-cómo-funciona-a2a-alto-nivel) arriba para resúmenes)*

*   📖 [Documentación Técnica de A2A](https://google.github.io/A2A/#/documentation) - **(Detalles Completos)** Explicación detallada de actores, transporte, autenticación, objetos centrales (Task, Artifact, Message, Part), Agent Card, etc.
*   📄 [Especificación JSON](https://github.com/google/A2A/tree/main/specification/json) - La definición cruda del esquema JSON para las estructuras A2A.
*   💡 [Principios Clave (Docs)](https://google.github.io/A2A/#/documentation?id=key-principles) - Enlace a la sección de principios en los documentos oficiales.
*   🃏 [Especificación Agent Card (Docs)](https://google.github.io/A2A/#/documentation?id=agent-card) - Enlace a la sección de Agent Card en los documentos oficiales.
*   🗺️ [Descubrimiento de Agentes (Tema)](https://google.github.io/A2A/#/topics/agent_discovery.md) - Discusión sobre cómo los clientes pueden encontrar Agent Cards.
*   🔔 [Notificaciones Push (Tema)](https://google.github.io/A2A/#/topics/push_notifications.md) - Detalles sobre el mecanismo de notificación push.
*   🛡️ [Listo para Empresas (Tema)](https://google.github.io/A2A/#/topics/enterprise_ready.md) - Discusión sobre aspectos de seguridad, autenticación y privacidad.

## ⚙️ Implementaciones y Bibliotecas

#### Ejemplos Oficiales

*Estos demuestran la comunicación básica cliente/servidor A2A.*

| Idioma     | Tipo                | Framework   | Descripción                                      | Enlace                                                                            |
| :--------- | :------------------ | :---------- | :----------------------------------------------- | :-------------------------------------------------------------------------------- |
| 🐍 Python  | Biblioteca Común    | -           | Manejo central de HTTP, JSON-RPC, SSE            | [Enlace](https://github.com/google/A2A/tree/main/samples/python/common)             |
| 🐍 Python  | Host (Cliente)      | CLI         | Ejemplo de cliente de línea de comandos          | [Enlace](https://github.com/google/A2A/tree/main/samples/python/hosts/cli)          |
| 🐍 Python  | Host (Agente)       | ADK         | Agente orquestador delegando a agentes A2A     | [Enlace](https://github.com/google/A2A/tree/main/samples/python/hosts/multiagent)   |
| 🚀 JS/TS   | Biblioteca Servidor | Express     | Implementación central del servidor              | [Enlace](https://github.com/google/A2A/tree/main/samples/js/src/server)             |
| 🚀 JS/TS   | Biblioteca Cliente  | -           | Implementación del cliente                       | [Enlace](https://github.com/google/A2A/tree/main/samples/js/src/client)             |
| 🚀 JS/TS   | Host (Cliente)      | CLI         | Ejemplo de cliente de línea de comandos          | [Enlace](https://github.com/google/A2A/blob/main/samples/js/src/cli.ts)             |

#### Integraciones de Frameworks (Ejemplos Oficiales)

*Estos muestran cómo los agentes construidos con frameworks específicos pueden exponer una interfaz A2A.*

| Idioma     | Framework de Agente | Descripción del Agente                 | Características Clave de A2A Demostradas | Enlace                                                                           |
| :--------- | :------------------ | :--------------------------------------- | :--------------------------------------- | :----------------------------------------------------------------------------- |
| 🐍 Python  | LangGraph           | Conversión de moneda                   | Herramientas, Streaming, Multi-turno     | [Enlace](https://github.com/google/A2A/tree/main/samples/python/agents/langgraph) |
| 🐍 Python  | CrewAI              | Generación de imágenes                 | Artefactos no textuales (Archivos)     | [Enlace](https://github.com/google/A2A/tree/main/samples/python/agents/crewai)   |
| 🐍 Python  | Google ADK          | Reembolso de gastos                    | Multi-turno, Formularios (DataPart)    | [Enlace](https://github.com/google/A2A/tree/main/samples/python/agents/google_adk)|
| 🚀 JS/TS   | Genkit              | Info de películas / Generación de código | Herramientas, Artefactos (Archivos), Async | [Enlace](https://github.com/google/A2A/tree/main/samples/js/src/agents)          |

#### Implementaciones de la Comunidad

*   🌟 [trpc-a2a-go](https://github.com/trpc-group/trpc-a2a-go) por [@trpc-group](https://github.com/trpc-group) [![Stars](https://img.shields.io/github/stars/trpc-group/trpc-a2a-go?style=social)](https://github.com/trpc-group/trpc-a2a-go) - Implementación A2A en Go desarrollada por el equipo tRPC, ofrece soporte completo de cliente/servidor, gestión de tareas en memoria, respuestas en streaming, gestión de sesiones y múltiples métodos de autenticación (JWT, clave API, OAuth2). Incluye ejemplos completos de servidor básico, streaming e implementaciones de autenticación.
*   🌟 [a2a-go](https://github.com/a2aserver/a2a-go) por [@a2aserver](https://github.com/a2aserver) [![Stars](https://img.shields.io/github/stars/a2aserver/a2a-go?style=social)](https://github.com/a2aserver/a2a-go) - Una biblioteca Go para construir servidores A2A, con implementaciones de ejemplo.
*   🌟 [a2a-rs](https://github.com/EmilLindfors/a2a-rs) por [@EmilLindfors](https://github.com/EmilLindfors) [![Stars](https://img.shields.io/github/stars/EmilLindfors/a2a-rs?style=social)](https://github.com/EmilLindfors/a2a-rs) - Una implementación idiomática en Rust que sigue los principios de la arquitectura hexagonal.
*   🌟 [a2a_min](https://github.com/pcingola/a2a_min) por [@pcingola](https://github.com/pcingola) [![Stars](https://img.shields.io/github/stars/pcingola/a2a_min?style=social)](https://github.com/pcingola/a2a_min) - Un SDK minimalista de Python para la comunicación A2A.
*   🌟 [a2adotnet](https://github.com/azixaka/a2adotnet) por [@azixaka](https://github.com/azixaka) [![Stars](https://img.shields.io/github/stars/azixaka/a2adotnet?style=social)](https://github.com/azixaka/a2adotnet) - Una implementación en C#/.NET del protocolo A2A.
*   🌟 [nestjs-a2a](https://github.com/thestupd/nestjs-a2a) por [@thestupd](https://github.com/thestupd) [![Stars](https://img.shields.io/github/stars/thestupd/nestjs-a2a?style=social)](https://github.com/thestupd/nestjs-a2a) - Un módulo para integrar el protocolo A2A en aplicaciones NestJS.
*   🌟 [python-a2a](https://github.com/themanojdesai/python-a2a) by [@themanojdesai](https://github.com/themanojdesai) [![Stars](https://img.shields.io/github/stars/themanojdesai/python-a2a?style=social)](https://github.com/themanojdesai/python-a2a) - Una biblioteca Python fácil de usar para implementar el protocolo A2A.
*   🌟 [Aira](https://github.com/IhateCreatingUserNames2/Aira) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Aira?style=social)](https://github.com/IhateCreatingUserNames2/Aira) - Una implementación de red A2A para alojar, registrar, descubrir e interactuar con agentes.
*   🌟 [Cognisphere](https://github.com/IhateCreatingUserNames2/Cognisphere) by [@IhateCreatingUserNames2](https://github.com/IhateCreatingUserNames2) [![Stars](https://img.shields.io/github/stars/IhateCreatingUserNames2/Cognisphere?style=social)](https://github.com/IhateCreatingUserNames2/Cognisphere) - Un framework de desarrollo de agentes de IA construido sobre el ADK de Google, facilitando la creación de agentes potencialmente para redes A2A.
*   🌐 [Grasp](https://github.com/aircodelabs/grasp) by [@adcentury](https://github.com/adcentury) [![Stars](https://img.shields.io/github/stars/aircodelabs/grasp?style=social)](https://github.com/aircodelabs/grasp) - Un agente de navegador autoalojado con soporte nativo para MCP y A2A.
<!-- ¡Añade la tuya aquí! Consulta CONTRIBUTING.md -->

## 🛠️ Herramientas y Utilidades

*   🔍 *Servicios de Descubrimiento de Agentes* - [Enlace] - Descripción (ej., implementación de un 'Catálogo de Agentes'). <!-- TODO -->
*   ✅ *Herramienta de Validación A2A* - [Enlace] - Herramienta para verificar la conformidad de un endpoint A2A. <!-- TODO -->
*   📊 *Adaptadores de Monitorización/Trazabilidad* - [Enlace] - Integraciones para plataformas de observabilidad. <!-- TODO -->

## 📚 Tutoriales y Artículos

*   📄 [Descripción Conceptual Oficial de A2A (README)](https://github.com/google/A2A#conceptual-overview) - Explicación de alto nivel en el README del repo oficial.
*   🚀 [Guía de Inicio Rápido (README Oficial)](https://github.com/google/A2A#getting-started) - Enlaces a documentos, especificaciones, ejemplos en el README del repo oficial.
*   🌐 [Sitio de Documentación del Protocolo Agent2Agent](https://agent2agent.ren) - Sitio de documentación de código abierto impulsado por la comunidad para el protocolo A2A. Construido con React/TypeScript, soporta inglés, chino y japonés. ([Código Fuente](https://github.com/ai-boost/agent2agent_doc))
*   ✍️ *[Título del Artículo/Tutorial]* - [Enlace] - Descripción. <!-- TODO: Añadir artículos/guías de la comunidad aquí -->

## 🎬 Demos y Ejemplos

*   🌐 [Demo Web Multi-Agente Oficial (Python/Mesop)](https://github.com/google/A2A/tree/main/demo) - Demuestra el agente orquestador interactuando con múltiples agentes remotos, renderizando texto, imágenes y formularios. **Requiere ejecutar código Python.**
*   🎥 [Video Demo Oficial (Enlace de Sección)](https://github.com/google/A2A#see-a2a-in-action) - Enlace al video incrustado en el README del repositorio oficial.

## 🔗 Protocolos y Conceptos Relacionados

*   📦 [Model Context Protocol (MCP)](https://github.com/modelcontextprotocol/servers) - Protocolo complementario enfocado en proporcionar herramientas/contexto *a* los agentes. ([Discusión A2A y MCP](https://google.github.io/A2A/#/topics/a2a_and_mcp.md)).
*   📞 *Estándares de Llamada a Función / Uso de Herramientas* - [Enlace] - Estándares relevantes (ej., llamada a función de OpenAI). <!-- TODO -->

## 💬 Comunidad

*   🐞 [Issues GitHub de google/A2A](https://github.com/google/A2A/issues) - Para reportar bugs o sugerir mejoras al protocolo.
*   💬 [Discussions GitHub de google/A2A](https://github.com/google/A2A/discussions/) - Para preguntas generales, ideas y discusiones de la comunidad sobre el protocolo A2A.
*   🔒 [Formulario de Feedback Privado](https://docs.google.com/forms/d/e/1FAIpQLScS23OMSKnVFmYeqS2dP7dxY3eTyT7lmtGLUa8OJZfP4RTijQ/viewform) - Formulario de Google para feedback privado.

---

**¡Hagamos que Awesome A2A sea más útil juntos!**

A2A todavía es algo nuevo, y los recursos buenos o la experiencia práctica pueden estar dispersos. Creamos esta lista para reunir lo bueno en un solo lugar, facilitando la búsqueda, el aprendizaje y la consulta.

Mantener esta lista actualizada y de alta calidad depende de la ayuda de toda la comunidad:

*   ⭐ **Dale una estrella (Star)**: Si te parece útil, es una forma de apoyar y te facilita volver a encontrarla.
*   ➕ **Comparte lo que encuentres**: ¿Una buena librería, artículo, herramienta o incluso un error común (pitfall)? Añádelo mediante un [Issue](https://github.com/ai-boost/awesome-a2a/issues) o [PR](CONTRIBUTING.md). ¡Construyámosla juntos!
*   📣 **Corre la voz**: Hazle saber a otros amigos que estén explorando o trabajando con A2A sobre esta lista.

¡Gracias por tu interés y tus contribuciones!

---

## Contribuir

¡Las contribuciones son bienvenidas! 🙌 Por favor, lee primero las [directrices de contribución](CONTRIBUTING.md). ¡Construyamos esta lista juntos!
