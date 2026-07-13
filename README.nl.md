[en](README.md) • [es](README.es.md) • [de](README.de.md) • [ja](README.ja.md) • [fr](README.fr.md) • [pt](README.pt.md) • [ru](README.ru.md) • [it](README.it.md) • **nl** • [pl](README.pl.md)

# VibeSEO MCP

**Model Context Protocol-server voor SEO-onderzoek, audits en content-workflow — beveiligd met OAuth.**

VibeSEO MCP brengt live SEO-werk rechtstreeks in je AI-assistent. Verbind Claude, ChatGPT, Cursor, VS Code of een CLI-client met VibeSEO. Vraag dan in natuurlijke taal om zoekwoordonderzoek, audits, backlinks, Search Console-trends en content-workflow-acties.

- **Server-URL:** `https://mcp.vibeseo.dev/mcp`
- **Transport:** Streamable HTTP
- **Auth:** OAuth 2.1 met PKCE, scope `mcp:tools`
- **Landing & setup:** [vibeseo.dev/mcp](https://vibeseo.dev/mcp)

## Installatie

VibeSEO MCP is een **remote, OAuth-beveiligde** server. Voeg dit toe aan de MCP-config van je client:

```json
{
  "mcpServers": {
    "vibeseo": {
      "url": "https://mcp.vibeseo.dev/mcp"
    }
  }
}
```

**Één-klik-installatie:**

<a href="https://cursor.com/en/install-mcp?name=vibeseo&config=eyJuYW1lIjoidmliZXNlbyIsInR5cGUiOiJodHRwIiwidXJsIjoiaHR0cHM6Ly9tY3AudmliZXNlby5kZXYvbWNwIn0="><img src="https://vibeseo.dev/icons/cursor.svg" width="36" alt="Cursor"></a>&nbsp;&nbsp;<a href="https://insiders.vscode.dev/redirect/mcp/install?name=vibeseo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.vibeseo.dev%2Fmcp%22%7D"><img src="https://vibeseo.dev/icons/vscode.svg" width="36" alt="VS Code"></a>&nbsp;&nbsp;<a href="https://claude.ai/settings/connectors"><img src="https://vibeseo.dev/icons/claude-desktop.svg" width="36" alt="Claude"></a>&nbsp;&nbsp;<a href="https://chatgpt.com/settings/connectors"><img src="https://vibeseo.dev/icons/chatgpt-icon.svg" width="36" alt="ChatGPT"></a>

CLI-clients (Claude Code, Gemini CLI, Codex CLI) en handmatige snippets: zie [Ondersteunde clients](#ondersteunde-clients).

## Snelle start

1. Maak een VibeSEO-account op [vibeseo.dev](https://vibeseo.dev) en start een proefperiode — $0 vandaag, creditcard vereist (zie [Abonnementen & toegang](#abonnementen--toegang)).
2. Open de [VibeSEO MCP-pagina](https://vibeseo.dev/mcp) en volg de setup-link voor jouw client.
3. Gebruik de één-klik-installatie, het gekopieerde CLI-commando of het handmatige JSON/TOML-snippet.
4. Autoriseer via OAuth wanneer je client het toestemmingsscherm opent.
5. Vraag je assistent om SEO-werk in natuurlijke taal.

## Wat je vanuit de chat kunt doen

- **🔍 Zoekwoordonderzoek** — volumes, CPC, moeilijkheid, intent, autocomplete-ideeën, vraag-zoekwoorden, vergelijkingen en gerelateerde termen.
- **🌐 Domeinanalyse** — domeinoverzicht, top-zoekwoorden, top-pagina's, verkeerhistorie en concurrent-suggesties.
- **🛠️ Site-audits** — start audits, lees crawl-resultaten, lijst issues op en prioriteer fixes.
- **📈 GSC-performance** — overzichten van gekoppelde Google Search Console, top-queries, top-pagina's, trends en diagnostiek op queryniveau.
- **🔗 Backlinks** *(Pro)* — profiel, verwijzende domeinen, anchor text en historie van elk domein.
- **🚀 Content-workflow** *(Pro)* — lijst posts, ververs ideeën, genereer drafts, keur goed, plan in en review.

## Tool-oppervlak

De MCP-server is een spiegel van dezelfde SEO-workflow binnen VibeSEO. Categorieën:

| Categorie | Wat het dekt |
|---|---|
| 📁 **Projects** | Projecten opsommen, project- en site-informatie lezen, gevolgde concurrenten opsommen en vervangen. |
| 🔍 **Keywords** | Metrics, autocomplete, gerelateerde, vraag-, voorzetsel- en vergelijkings-zoekwoorden, lookup-historie. |
| 🌐 **Domains** | Overzicht, top-zoekwoorden, top-pagina's, verkeerhistorie, concurrent-ideeën, lookup-historie. |
| 🧯 **Audits** | Site-audits starten, samenvattingen lezen, issues lijsten, gecrawlde pagina's inspecteren. |
| 📊 **GSC** | Verbindingsstatus, samenvattingen, top-queries, top-pagina's, trends, query-details. |
| ⚔️ **Competitive** | Concurrentie-overzicht en keyword-gap-analyse tussen domeinen. |
| 📍 **Locations** | Landen, talen, locaties, stad-lookups, locatiecodes voor marktspecifiek onderzoek. |
| 🔗 **Backlinks** *(Pro)* | Profiel, verwijzende domeinen, anchors, backlink-historie. |
| ✍️ **Content** *(Pro)* | Ideeën, drafts, goedkeuringen, scheduling, content-kalender, publicaties, keyword-scoring. |

De live tool-set evolueert. Voor de exacte, actuele lijst: run `tools/list` tegen `https://mcp.vibeseo.dev/mcp`.

## Abonnementen & toegang

De tools roepen namens jou betaalde dataproviders en AI-modellen aan, dus ze vereisen een actief VibeSEO-abonnement — een proefperiode of een betaald plan. Er is geen anonieme of gratis-voor-altijd laag.

| | Trial | SEO Researcher | Pro |
|---|---|---|---|
| **Prijs** | $0 vandaag, creditcard vereist | $9/mnd | $39/mnd |
| Keywords, domains, audits, GSC, competitive, locations | ✅ | ✅ | ✅ |
| Backlink-data | — | — | ✅ |
| AI-content-workflow (ideeën, drafts, publiceren) | — | — | ✅ |
| Maandelijkse credits | 40 | 400 | 1500 |

De proefperiode is creditcard-verplicht, start op $0 en kan op elk moment worden opgezegd; ze draait op research-niveau-limieten en zet zich om naar het door jou gekozen plan wanneer ze eindigt. Credits meten de calls die geld kosten (keyword-lookups, audits, AI-generatie) — zie [vibeseo.dev/pricing](https://vibeseo.dev/pricing) voor de actuele plannen.

**Je hoeft de chat nooit te verlaten om te betalen.** Als je een tool aanroept zonder actief abonnement, zonder credits, of op een plan dat het niet omvat, komt het tool-resultaat terug met een één-klik-checkout- of top-up-link voor je account.

## Ondersteunde clients

Installatiepaden voor elk:

- **Claude** (web & desktop) — Connectors-pagina of `claude_desktop_config.json`
- **ChatGPT** — custom MCP-connector met OAuth
- **Cursor** — één-klik-installatie via deeplink, of `~/.cursor/mcp.json`
- **VS Code** — één-klik-installatie via deeplink, of `.vscode/mcp.json`
- **Claude Code (CLI)** — `claude mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Gemini CLI** — `gemini mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Codex CLI** — `codex mcp add vibeseo --url https://mcp.vibeseo.dev/mcp`
- **Generieke HTTP MCP-client** — wijs naar de URL en laat OAuth-discovery z'n werk doen

Volledige installatie-instructies per client: [docs/setup.md](docs/setup.md).

## Voorbeeldprompts

**Keyword-plan**
> "Vind vergelijkings-keywords voor mijn invoicing-app die realistisch te ranken zijn."

→ VibeSEO geeft een geprioriteerde topiclijst terug (commerciële intent, lagere moeilijkheid, vergelijkings-angle).

**Technische audit**
> "Audit mijn project en zeg me wat ik moet fixen voor ik meer artikelen publiceer."

→ VibeSEO zet crawl-data om in concrete vervolgstappen (ontbrekende canonicals, te zware afbeeldingen, gaten in interne linking).

**Publish-queue**
> "Toon ready posts, genereer de volgende draft en plan de sterkste in."

→ VibeSEO beheert de content-workflow (tellers van Ready/Drafting, plant het volgende goedgekeurde artikel in).

Meer: [docs/examples.md](docs/examples.md).

## Autorisatie en approval gate

Auth is OAuth 2.1 met PKCE. Je assistent krijgt een token met scope `mcp:tools`, gekoppeld aan je VibeSEO-account. Tokens zijn op elk moment intrekbaar via de [VibeSEO MCP-pagina](https://vibeseo.dev/mcp) onder "Connected clients" — een client disconnecten trekt de toegang direct in.

**MCP kan helpen de workflow te beheren, maar VibeSEO houdt de approval gate vóór content live gaat.** Drafts en geplande posts blijven door de standaard review-stap binnen VibeSEO lopen.

OAuth-flow-details: [docs/oauth.md](docs/oauth.md).

## Project-links

- Product: [vibeseo.dev](https://vibeseo.dev)
- VibeSEO MCP-pagina: [vibeseo.dev/mcp](https://vibeseo.dev/mcp)
- MCP-server: `https://mcp.vibeseo.dev/mcp`
- OAuth issuer: `https://api.vibeseo.dev`
- Issues: [github.com/sultanlive/vibeseo-mcp/issues](https://github.com/sultanlive/vibeseo-mcp/issues)

## Licentie

MIT — zie [LICENSE](LICENSE).

---

Gemaakt door [@sultanlive](https://github.com/sultanlive). VibeSEO is een gehost SEO-platform; deze repo is documentatie voor de publieke MCP-server. De server-source is niet open.
