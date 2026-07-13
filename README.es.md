[en](README.md) • **es** • [de](README.de.md) • [ja](README.ja.md) • [fr](README.fr.md) • [pt](README.pt.md) • [ru](README.ru.md) • [it](README.it.md) • [nl](README.nl.md) • [pl](README.pl.md)

# VibeSEO MCP

**Servidor Model Context Protocol para investigación SEO, auditorías y flujo de trabajo de contenido — protegido por OAuth.**

VibeSEO MCP lleva el trabajo SEO en vivo a tu asistente de IA. Conecta Claude, ChatGPT, Cursor, VS Code o un cliente CLI con VibeSEO. Luego pide investigación de palabras clave, auditorías, backlinks, tendencias de Search Console y acciones del flujo de contenido en lenguaje natural.

- **URL del servidor:** `https://mcp.vibeseo.dev/mcp`
- **Transporte:** Streamable HTTP
- **Auth:** OAuth 2.1 con PKCE, scope `mcp:tools`
- **Landing y setup:** [vibeseo.dev/mcp](https://vibeseo.dev/mcp)

## Instalación

VibeSEO MCP es un servidor **remoto, seguro con OAuth**. Añade esto al config MCP de tu cliente:

```json
{
  "mcpServers": {
    "vibeseo": {
      "url": "https://mcp.vibeseo.dev/mcp"
    }
  }
}
```

**Instalación en un clic:**

<a href="https://cursor.com/en/install-mcp?name=vibeseo&config=eyJuYW1lIjoidmliZXNlbyIsInR5cGUiOiJodHRwIiwidXJsIjoiaHR0cHM6Ly9tY3AudmliZXNlby5kZXYvbWNwIn0="><img src="https://vibeseo.dev/icons/cursor.svg" width="36" alt="Cursor"></a>&nbsp;&nbsp;<a href="https://insiders.vscode.dev/redirect/mcp/install?name=vibeseo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.vibeseo.dev%2Fmcp%22%7D"><img src="https://vibeseo.dev/icons/vscode.svg" width="36" alt="VS Code"></a>&nbsp;&nbsp;<a href="https://claude.ai/settings/connectors"><img src="https://vibeseo.dev/icons/claude-desktop.svg" width="36" alt="Claude"></a>&nbsp;&nbsp;<a href="https://chatgpt.com/settings/connectors"><img src="https://vibeseo.dev/icons/chatgpt-icon.svg" width="36" alt="ChatGPT"></a>

Clientes CLI (Claude Code, Gemini CLI, Codex CLI) y snippets manuales: ver [Clientes soportados](#clientes-soportados).

## Empezar rápido

1. Crea una cuenta de VibeSEO en [vibeseo.dev](https://vibeseo.dev) y empieza una prueba — $0 hoy, tarjeta requerida (ver [Planes y acceso](#planes-y-acceso)).
2. Abre la [página de VibeSEO MCP](https://vibeseo.dev/mcp) y sigue el enlace de instalación para tu cliente.
3. Usa la instalación en un clic, el comando CLI copiado o el snippet manual de JSON/TOML.
4. Autoriza con OAuth cuando tu cliente abra la pantalla de consentimiento.
5. Pide trabajo SEO a tu asistente en lenguaje natural.

## Qué puedes hacer desde el chat

- **🔍 Investigación de palabras clave** — volúmenes, CPC, dificultad, intención, ideas de autocompletar, keywords-pregunta, comparaciones y términos relacionados.
- **🌐 Análisis de dominio** — overview de dominio, top keywords, top páginas, histórico de tráfico y sugerencias de competidores.
- **🛠️ Auditorías de sitio** — lanzar auditorías, leer resultados de crawl, listar issues y priorizar arreglos.
- **📈 Performance en GSC** — resúmenes de la Google Search Console conectada, top queries, top páginas, tendencias y diagnóstico a nivel de query.
- **🔗 Backlinks** *(Pro)* — perfil, dominios referentes, anchor text e histórico de cualquier dominio.
- **🚀 Flujo de contenido** *(Pro)* — listar posts, refrescar ideas, generar drafts, aprobar artículos listos, programar y revisar.

## Superficie de herramientas

El servidor MCP refleja el mismo flujo SEO que vive dentro de VibeSEO. Categorías:

| Categoría | Qué cubre |
|---|---|
| 📁 **Projects** | Listar proyectos, leer información del proyecto y del sitio, listar y reemplazar competidores rastreados. |
| 🔍 **Keywords** | Métricas, autocomplete, keywords relacionadas, de pregunta, de preposición y de comparación, historial de lookups. |
| 🌐 **Domains** | Overview, top keywords, top páginas, histórico de tráfico, ideas de competidores, historial de lookups. |
| 🧯 **Audits** | Lanzar auditorías de sitio, leer resúmenes, listar issues, inspeccionar páginas crawleadas. |
| 📊 **GSC** | Estado de conexión, resúmenes, top queries, top páginas, tendencias, detalles por query. |
| ⚔️ **Competitive** | Overview competitivo y análisis de keyword gap entre dominios. |
| 📍 **Locations** | Países, idiomas, ubicaciones, lookups de ciudades, códigos de ubicación para research por mercado. |
| 🔗 **Backlinks** *(Pro)* | Perfil, dominios referentes, anchors, histórico de backlinks. |
| ✍️ **Content** *(Pro)* | Ideas, drafts, aprobaciones, scheduling, calendario de contenido, publicaciones, scoring de keywords. |

El conjunto de herramientas en vivo evoluciona. Para la lista exacta y actualizada, ejecuta `tools/list` contra `https://mcp.vibeseo.dev/mcp`.

## Planes y acceso

Las herramientas llaman a proveedores de datos de pago y modelos de IA en tu nombre, así que necesitan una suscripción activa de VibeSEO — una prueba o un plan de pago. No hay nivel anónimo ni gratuito para siempre.

| | Prueba | SEO Researcher | Pro |
|---|---|---|---|
| **Precio** | $0 hoy, tarjeta requerida | $9/mes | $39/mes |
| Keywords, dominios, auditorías, GSC, competitivo, ubicaciones | ✅ | ✅ | ✅ |
| Datos de backlinks | — | — | ✅ |
| Flujo de contenido con IA (ideas, drafts, publicación) | — | — | ✅ |
| Créditos mensuales | 40 | 400 | 1500 |

La prueba requiere tarjeta, empieza en $0 y se puede cancelar en cualquier momento; funciona con los límites del nivel de investigación y se convierte al plan que elegiste cuando termina. Los créditos miden las llamadas que cuestan dinero (lookups de keywords, auditorías, generación con IA) — ver [vibeseo.dev/pricing](https://vibeseo.dev/pricing) para los planes actuales.

**Nunca tienes que salir del chat para pagar.** Si llamas a una herramienta sin una suscripción activa, sin créditos, o en un plan que no la incluye, el resultado de la herramienta vuelve con un enlace de pago o de recarga en un clic para tu cuenta.

## Clientes soportados

Rutas de instalación para cada uno:

- **Claude** (web y desktop) — página Connectors o `claude_desktop_config.json`
- **ChatGPT** — connector MCP personalizado con OAuth
- **Cursor** — instalación en un clic vía deeplink, o `~/.cursor/mcp.json`
- **VS Code** — instalación en un clic vía deeplink, o `.vscode/mcp.json`
- **Claude Code (CLI)** — `claude mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Gemini CLI** — `gemini mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Codex CLI** — `codex mcp add vibeseo --url https://mcp.vibeseo.dev/mcp`
- **Cliente MCP HTTP genérico** — apunta a la URL y deja que complete el OAuth discovery

Instrucciones completas de instalación por cliente: [docs/setup.md](docs/setup.md).

## Ejemplos de prompts

**Plan de keywords**
> "Encuentra keywords de comparación para mi app de invoicing que sean realistas de rankear."

→ VibeSEO devuelve una lista priorizada de temas (intención comercial, dificultad baja, ángulo de comparación).

**Auditoría técnica**
> "Audita mi proyecto y dime qué arreglar antes de publicar más artículos."

→ VibeSEO convierte datos de crawl en próximas acciones (canónicas faltantes, imágenes pesadas, gaps de enlaces internos).

**Cola de publicación**
> "Muestra los posts listos, genera el próximo draft y programa el más fuerte."

→ VibeSEO gestiona el flujo de contenido (conteo de Ready/Drafting, programa el próximo artículo aprobado).

Más: [docs/examples.md](docs/examples.md).

## Autorización y gate de aprobación

La auth es OAuth 2.1 con PKCE. Tu asistente obtiene un token con scope `mcp:tools`, vinculado a tu cuenta de VibeSEO. Los tokens se pueden revocar en cualquier momento desde la [página de VibeSEO MCP](https://vibeseo.dev/mcp) bajo "Connected clients" — desconectar un cliente revoca su acceso inmediatamente.

**MCP puede ayudar a gestionar el flujo, pero VibeSEO mantiene el gate de aprobación antes de que el contenido se publique.** Los drafts y posts programados siguen pasando por el paso de review estándar dentro de VibeSEO.

Detalles del flow OAuth: [docs/oauth.md](docs/oauth.md).

## Enlaces del proyecto

- Producto: [vibeseo.dev](https://vibeseo.dev)
- Página de VibeSEO MCP: [vibeseo.dev/mcp](https://vibeseo.dev/mcp)
- Servidor MCP: `https://mcp.vibeseo.dev/mcp`
- OAuth issuer: `https://api.vibeseo.dev`
- Issues: [github.com/sultanlive/vibeseo-mcp/issues](https://github.com/sultanlive/vibeseo-mcp/issues)

## Licencia

MIT — ver [LICENSE](LICENSE).

---

Hecho por [@sultanlive](https://github.com/sultanlive). VibeSEO es una plataforma SEO hospedada; este repo es la documentación de su servidor MCP público. El código del servidor no es open.
