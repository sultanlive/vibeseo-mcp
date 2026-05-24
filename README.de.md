[en](README.md) • [es](README.es.md) • **de** • [ja](README.ja.md) • [fr](README.fr.md) • [pt](README.pt.md) • [ru](README.ru.md) • [it](README.it.md) • [nl](README.nl.md) • [pl](README.pl.md)

# VibeSEO MCP

**Model-Context-Protocol-Server für SEO-Recherche, Audits und Content-Workflow — abgesichert über OAuth.**

VibeSEO MCP bringt live laufende SEO-Arbeit direkt in deinen KI-Assistenten. Verbinde Claude, ChatGPT, Cursor, VS Code oder einen CLI-Client mit VibeSEO. Frag dann in natürlicher Sprache nach Keyword-Recherche, Audits, Backlinks, Search-Console-Trends und Content-Workflow-Aktionen.

- **Server-URL:** `https://mcp.vibeseo.dev/mcp`
- **Transport:** Streamable HTTP
- **Auth:** OAuth 2.1 mit PKCE, Scope `mcp:tools`
- **Landing & Setup:** [vibeseo.dev/mcp](https://vibeseo.dev/mcp)

## Quick Start

1. Erstelle einen kostenlosen VibeSEO-Account auf [vibeseo.dev](https://vibeseo.dev).
2. Öffne die [VibeSEO-MCP-Seite](https://vibeseo.dev/mcp) und folge dem Setup-Link für deinen Client.
3. Nutze den Ein-Klick-Install, den kopierten CLI-Befehl oder das manuelle JSON/TOML-Snippet.
4. Autorisiere via OAuth, wenn dein Client den Consent-Screen öffnet.
5. Frag deinen Assistenten in natürlicher Sprache nach SEO-Arbeit.

## Was du im Chat machen kannst

- **🔍 Keyword-Recherche** — Volumen, CPC, Schwierigkeit, Intent, Autocomplete-Ideen, Fragen-Keywords, Vergleiche und verwandte Begriffe.
- **🌐 Domain-Analyse** — Domain-Übersicht, Top-Keywords, Top-Seiten, Traffic-Historie und Wettbewerbsvorschläge.
- **🔗 Backlinks** — Profil, verweisende Domains, Anchor Text und Historie jeder Domain.
- **🛠️ Site-Audits** — Audits starten, Crawl-Ergebnisse lesen, Issues auflisten und Fixes priorisieren.
- **📈 GSC-Performance** — Zusammenfassungen aus verbundener Google Search Console, Top-Queries, Top-Seiten, Trends und Query-Level-Diagnostik.
- **🚀 Content-Workflow** — Posts auflisten, Ideen aktualisieren, Drafts generieren, freigeben, einplanen und reviewen.

## Tool-Oberfläche

Der MCP-Server spiegelt denselben SEO-Workflow, der in VibeSEO selbst läuft. Kategorien:

| Kategorie | Was sie abdeckt |
|---|---|
| 📁 **Projects** | Projekte anlegen, Site-Infos pflegen, Wettbewerber verwalten, Account-Kontext aktuell halten. |
| 🔍 **Keywords** | Metriken, Batches, Vorschläge, Autocomplete, Fragen, Vergleiche, Historie, Cleanup. |
| 🌐 **Domains** | Übersicht, Top-Keywords, Top-Seiten, Traffic-Historie, Wettbewerber-Ideen, Lookup-Historie. |
| 🔗 **Backlinks** | Profil, verweisende Domains, Anchors, Backlink-Historie. |
| 🧯 **Audits** | Site-Audits starten, Zusammenfassungen lesen, Issues auflisten, gecrawlte Seiten inspizieren. |
| 📊 **GSC** | Verbundene Properties, Status, Zusammenfassungen, Top-Queries, Top-Seiten, Trends, Query-Details. |
| ✍️ **Content** | Ideen, Drafts, Freigaben, Scheduling, Publishing-Targets, Veröffentlichungen, Keyword-Scoring. |
| ⚔️ **Competitive** | Wettbewerbs-Übersicht und Keyword-Gap-Analyse zwischen Domains. |
| 📍 **Locations** | Länder, Sprachen, Standorte, City-Lookups, Location-Codes für marktspezifische Recherche. |

Das Live-Toolset entwickelt sich weiter. Für die exakte, aktuelle Liste führe `tools/list` gegen `https://mcp.vibeseo.dev/mcp` aus.

## Unterstützte Clients

Setup-Pfade für jeden:

- **Claude** (Web & Desktop) — Connectors-Seite oder `claude_desktop_config.json`
- **ChatGPT** — Custom MCP Connector mit OAuth
- **Cursor** — Ein-Klick-Install via Deeplink, oder `~/.cursor/mcp.json`
- **VS Code** — Ein-Klick-Install via Deeplink, oder `.vscode/mcp.json`
- **Claude Code (CLI)** — `claude mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Gemini CLI** — `gemini mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Codex CLI** — `codex mcp add vibeseo --url https://mcp.vibeseo.dev/mcp`
- **Generischer HTTP-MCP-Client** — auf die URL zeigen lassen und OAuth-Discovery durchlaufen lassen

Vollständige Installationsanleitungen pro Client: [docs/setup.md](docs/setup.md).

## Beispiel-Prompts

**Keyword-Plan**
> „Finde Vergleichs-Keywords für meine Invoicing-App, die realistisch rankbar sind."

→ VibeSEO liefert eine priorisierte Themenliste (kommerzieller Intent, geringere Schwierigkeit, Vergleichs-Angle).

**Technisches Audit**
> „Audite mein Projekt und sag mir, was zu fixen ist, bevor ich weitere Artikel veröffentliche."

→ VibeSEO macht aus Crawl-Daten konkrete nächste Schritte (fehlende Canonicals, zu große Bilder, interne Verlinkungslücken).

**Publish-Queue**
> „Zeig fertige Posts, generiere den nächsten Draft und plane den stärksten ein."

→ VibeSEO verwaltet den Content-Workflow (Anzahl Ready/Drafting, plant den nächsten freigegebenen Artikel).

Mehr: [docs/examples.md](docs/examples.md).

## Authorization und Approval Gate

Auth ist OAuth 2.1 mit PKCE. Dein Assistent bekommt ein Token mit Scope `mcp:tools`, gebunden an deinen VibeSEO-Account. Tokens sind jederzeit über die [VibeSEO-MCP-Seite](https://vibeseo.dev/mcp) unter „Connected clients" widerrufbar — einen Client zu disconnecten entzieht den Zugriff sofort.

**MCP kann den Workflow managen helfen, aber VibeSEO behält das Approval Gate, bevor Content live geht.** Drafts und geplante Posts laufen weiterhin durch den Standard-Review-Step innerhalb von VibeSEO.

OAuth-Flow-Details: [docs/oauth.md](docs/oauth.md).

## Projekt-Links

- Produkt: [vibeseo.dev](https://vibeseo.dev)
- VibeSEO-MCP-Seite: [vibeseo.dev/mcp](https://vibeseo.dev/mcp)
- MCP-Server: `https://mcp.vibeseo.dev/mcp`
- OAuth-Issuer: `https://api.vibeseo.dev`
- Issues: [github.com/sultanlive/vibeseo-mcp/issues](https://github.com/sultanlive/vibeseo-mcp/issues)

## Lizenz

MIT — siehe [LICENSE](LICENSE).

---

Gebaut von [@sultanlive](https://github.com/sultanlive). VibeSEO ist eine gehostete SEO-Plattform; dieses Repo ist die Doku zum öffentlichen MCP-Server. Der Server-Code ist nicht open.
