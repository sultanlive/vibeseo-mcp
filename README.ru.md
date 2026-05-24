[en](README.md) • [es](README.es.md) • [de](README.de.md) • [ja](README.ja.md) • [fr](README.fr.md) • [pt](README.pt.md) • **ru** • [it](README.it.md) • [nl](README.nl.md) • [pl](README.pl.md)

# VibeSEO MCP

**Сервер Model Context Protocol для SEO-исследований, аудитов и контент-воркфлоу — защищён OAuth.**

VibeSEO MCP приносит живую SEO-работу прямо в ваш AI-ассистент. Подключите Claude, ChatGPT, Cursor, VS Code или CLI-клиент к VibeSEO. Затем на естественном языке запрашивайте исследование ключевых слов, аудиты, обратные ссылки, тренды Search Console и действия по контент-воркфлоу.

- **URL сервера:** `https://mcp.vibeseo.dev/mcp`
- **Транспорт:** Streamable HTTP
- **Auth:** OAuth 2.1 с PKCE, scope `mcp:tools`
- **Лендинг и setup:** [vibeseo.dev/mcp](https://vibeseo.dev/mcp)

## Установка

VibeSEO MCP — это **удалённый, защищённый OAuth** сервер. Добавьте это в MCP-конфиг вашего клиента:

```json
{
  "mcpServers": {
    "vibeseo": {
      "url": "https://mcp.vibeseo.dev/mcp"
    }
  }
}
```

**Установка в один клик:**

<a href="https://cursor.com/en/install-mcp?name=vibeseo&config=eyJuYW1lIjoidmliZXNlbyIsInR5cGUiOiJodHRwIiwidXJsIjoiaHR0cHM6Ly9tY3AudmliZXNlby5kZXYvbWNwIn0="><img src="https://vibeseo.dev/icons/cursor.svg" width="36" alt="Cursor"></a>&nbsp;&nbsp;<a href="https://insiders.vscode.dev/redirect/mcp/install?name=vibeseo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.vibeseo.dev%2Fmcp%22%7D"><img src="https://vibeseo.dev/icons/vscode.svg" width="36" alt="VS Code"></a>&nbsp;&nbsp;<a href="https://claude.ai/settings/connectors"><img src="https://vibeseo.dev/icons/claude-desktop.svg" width="36" alt="Claude"></a>&nbsp;&nbsp;<a href="https://chatgpt.com/settings/connectors"><img src="https://vibeseo.dev/icons/chatgpt-icon.svg" width="36" alt="ChatGPT"></a>

CLI-клиенты (Claude Code, Gemini CLI, Codex CLI) и ручные сниппеты: см. [Поддерживаемые клиенты](#поддерживаемые-клиенты).

## Быстрый старт

1. Создайте бесплатный аккаунт VibeSEO на [vibeseo.dev](https://vibeseo.dev).
2. Откройте [страницу VibeSEO MCP](https://vibeseo.dev/mcp) и пройдите по ссылке установки для вашего клиента.
3. Воспользуйтесь one-click установкой, скопированной CLI-командой или ручным JSON/TOML-сниппетом.
4. Авторизуйтесь через OAuth, когда клиент откроет экран согласия.
5. Просите ассистента сделать SEO-работу на естественном языке.

## Что можно делать прямо из чата

- **🔍 Исследование ключевых слов** — объёмы, CPC, сложность, интент, идеи из автокомплита, ключи-вопросы, сравнения и связанные термины.
- **🌐 Анализ домена** — обзор домена, топ ключевых слов, топ страниц, история трафика и предложения по конкурентам.
- **🔗 Обратные ссылки** — профиль, ссылающиеся домены, анкорный текст и история любого домена.
- **🛠️ Аудиты сайта** — запуск аудитов, чтение результатов краулинга, список проблем и приоритизация фиксов.
- **📈 Performance в GSC** — сводки из подключённого Google Search Console, топ-запросы, топ-страницы, тренды и диагностика на уровне запросов.
- **🚀 Контент-воркфлоу** — список постов, обновление идей, генерация черновиков, утверждение готовых статей, расписание и ревью.

## Поверхность инструментов

MCP-сервер отражает тот же SEO-воркфлоу, что и внутри VibeSEO. Категории:

| Категория | Что покрывает |
|---|---|
| 📁 **Projects** | Создание проектов, обновление информации о сайте, управление конкурентами, поддержание контекста аккаунта актуальным. |
| 🔍 **Keywords** | Метрики, батчи, подсказки, автокомплит, вопросы, сравнения, история, cleanup. |
| 🌐 **Domains** | Обзор, топ ключевых слов, топ страниц, история трафика, идеи конкурентов, история lookups. |
| 🔗 **Backlinks** | Профиль, ссылающиеся домены, анкоры, история обратных ссылок. |
| 🧯 **Audits** | Запуск аудитов сайта, чтение сводок, список проблем, инспекция краулированных страниц. |
| 📊 **GSC** | Подключённые properties, статус, сводки, топ-запросы, топ-страницы, тренды, детали по запросам. |
| ✍️ **Content** | Идеи, черновики, утверждения, расписание, publishing targets, публикации, скоринг ключевых слов. |
| ⚔️ **Competitive** | Конкурентный обзор и анализ keyword gap между доменами. |
| 📍 **Locations** | Страны, языки, локации, lookup'ы городов, location-коды для исследований по конкретным рынкам. |

Живой набор инструментов эволюционирует. Точный, актуальный список — запросите `tools/list` к `https://mcp.vibeseo.dev/mcp`.

## Поддерживаемые клиенты

Пути установки для каждого:

- **Claude** (web и desktop) — страница Connectors или `claude_desktop_config.json`
- **ChatGPT** — кастомный MCP-коннектор с OAuth
- **Cursor** — one-click установка через deeplink, или `~/.cursor/mcp.json`
- **VS Code** — one-click установка через deeplink, или `.vscode/mcp.json`
- **Claude Code (CLI)** — `claude mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Gemini CLI** — `gemini mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Codex CLI** — `codex mcp add vibeseo --url https://mcp.vibeseo.dev/mcp`
- **Произвольный HTTP MCP-клиент** — укажите URL, дайте ему завершить OAuth discovery

Полные инструкции по установке для каждого клиента: [docs/setup.md](docs/setup.md).

## Примеры промптов

**План ключевых слов**
> «Найди сравнительные ключевые слова для моего invoicing-приложения, которые реалистично ранжировать.»

→ VibeSEO возвращает приоритизированный список тем (коммерческий интент, низкая сложность, угол сравнения).

**Технический аудит**
> «Сделай аудит моего проекта и скажи, что починить перед публикацией новых статей.»

→ VibeSEO превращает данные краулинга в конкретные следующие шаги (отсутствующие canonical, слишком тяжёлые картинки, дыры во внутренней перелинковке).

**Очередь публикации**
> «Покажи готовые посты, сгенерируй следующий черновик и поставь в расписание самый сильный.»

→ VibeSEO управляет контент-воркфлоу (счётчики Ready/Drafting, ставит в расписание следующую утверждённую статью).

Ещё: [docs/examples.md](docs/examples.md).

## Авторизация и approval gate

Auth — OAuth 2.1 с PKCE. Ассистент получает токен со scope `mcp:tools`, привязанный к вашему аккаунту VibeSEO. Токены отзываются в любой момент со [страницы VibeSEO MCP](https://vibeseo.dev/mcp) в разделе «Connected clients» — отключение клиента моментально отзывает его доступ.

**MCP помогает управлять воркфлоу, но approval gate перед публикацией контента остаётся за VibeSEO.** Черновики и запланированные посты всё равно проходят стандартный шаг ревью внутри VibeSEO.

Детали OAuth-флоу: [docs/oauth.md](docs/oauth.md).

## Ссылки проекта

- Продукт: [vibeseo.dev](https://vibeseo.dev)
- Страница VibeSEO MCP: [vibeseo.dev/mcp](https://vibeseo.dev/mcp)
- MCP-сервер: `https://mcp.vibeseo.dev/mcp`
- OAuth issuer: `https://api.vibeseo.dev`
- Issues: [github.com/sultanlive/vibeseo-mcp/issues](https://github.com/sultanlive/vibeseo-mcp/issues)

## Лицензия

MIT — см. [LICENSE](LICENSE).

---

Сделано [@sultanlive](https://github.com/sultanlive). VibeSEO — хостинговая SEO-платформа; этот репозиторий — документация её публичного MCP-сервера. Сорсы сервера не открыты.
