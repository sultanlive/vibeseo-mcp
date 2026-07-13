[en](README.md) • [es](README.es.md) • [de](README.de.md) • [ja](README.ja.md) • [fr](README.fr.md) • [pt](README.pt.md) • [ru](README.ru.md) • **it** • [nl](README.nl.md) • [pl](README.pl.md)

# VibeSEO MCP

**Server Model Context Protocol per ricerca SEO, audit e workflow di contenuto — protetto da OAuth.**

VibeSEO MCP porta il lavoro SEO live direttamente nel tuo assistente AI. Collega Claude, ChatGPT, Cursor, VS Code o un client CLI a VibeSEO. Poi chiedi in linguaggio naturale ricerca di parole chiave, audit, backlink, trend di Search Console e azioni di workflow di contenuto.

- **URL del server:** `https://mcp.vibeseo.dev/mcp`
- **Trasporto:** Streamable HTTP
- **Auth:** OAuth 2.1 con PKCE, scope `mcp:tools`
- **Landing e setup:** [vibeseo.dev/mcp](https://vibeseo.dev/mcp)

## Installazione

VibeSEO MCP è un server **remoto, sicuro con OAuth**. Aggiungi questo al config MCP del tuo client:

```json
{
  "mcpServers": {
    "vibeseo": {
      "url": "https://mcp.vibeseo.dev/mcp"
    }
  }
}
```

**Installazione one-click:**

<a href="https://cursor.com/en/install-mcp?name=vibeseo&config=eyJuYW1lIjoidmliZXNlbyIsInR5cGUiOiJodHRwIiwidXJsIjoiaHR0cHM6Ly9tY3AudmliZXNlby5kZXYvbWNwIn0="><img src="https://vibeseo.dev/icons/cursor.svg" width="36" alt="Cursor"></a>&nbsp;&nbsp;<a href="https://insiders.vscode.dev/redirect/mcp/install?name=vibeseo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.vibeseo.dev%2Fmcp%22%7D"><img src="https://vibeseo.dev/icons/vscode.svg" width="36" alt="VS Code"></a>&nbsp;&nbsp;<a href="https://claude.ai/settings/connectors"><img src="https://vibeseo.dev/icons/claude-desktop.svg" width="36" alt="Claude"></a>&nbsp;&nbsp;<a href="https://chatgpt.com/settings/connectors"><img src="https://vibeseo.dev/icons/chatgpt-icon.svg" width="36" alt="ChatGPT"></a>

Client CLI (Claude Code, Gemini CLI, Codex CLI) e snippet manuali: vedi [Client supportati](#client-supportati).

## Avvio rapido

1. Crea un account VibeSEO su [vibeseo.dev](https://vibeseo.dev) e avvia una prova — $0 oggi, carta richiesta (vedi [Piani & accesso](#piani--accesso)).
2. Apri la [pagina VibeSEO MCP](https://vibeseo.dev/mcp) e segui il link di setup per il tuo client.
3. Usa l'installazione one-click, il comando CLI copiato o lo snippet JSON/TOML manuale.
4. Autorizza con OAuth quando il client apre la schermata di consenso.
5. Chiedi al tuo assistente di fare lavoro SEO in linguaggio naturale.

## Cosa puoi fare dalla chat

- **🔍 Ricerca di parole chiave** — volumi, CPC, difficoltà, intent, idee dall'autocomplete, parole chiave-domanda, confronti e termini correlati.
- **🌐 Analisi di dominio** — panoramica del dominio, top keyword, top pagine, storico di traffico e suggerimenti di competitor.
- **🛠️ Audit di sito** — avvia audit, leggi i risultati di crawl, lista i problemi e prioritizza i fix.
- **📈 Performance GSC** — riassunti dalla Google Search Console collegata, top query, top pagine, trend e diagnostica a livello di query.
- **🔗 Backlink** *(Pro)* — profilo, domini referenti, anchor text e storico di qualsiasi dominio.
- **🚀 Workflow di contenuto** *(Pro)* — lista post, aggiorna idee, genera bozze, approva articoli pronti, programma e revisiona.

## Superficie di tool

Il server MCP rispecchia lo stesso workflow SEO interno a VibeSEO. Categorie:

| Categoria | Cosa copre |
|---|---|
| 📁 **Projects** | Elenca i progetti, leggi le info di progetto e sito, elenca e sostituisci i competitor tracciati. |
| 🔍 **Keywords** | Metriche, autocomplete, keyword correlate, di domanda, con preposizioni e di confronto, storico di lookup. |
| 🌐 **Domains** | Panoramica, top keyword, top pagine, storico di traffico, idee di competitor, storico di lookup. |
| 🧯 **Audits** | Avviare audit di sito, leggere riassunti, listare problemi, ispezionare pagine crawlate. |
| 📊 **GSC** | Stato della connessione, riassunti, top query, top pagine, trend, dettagli per query. |
| ⚔️ **Competitive** | Panoramica competitiva e analisi di keyword gap tra domini. |
| 📍 **Locations** | Paesi, lingue, localizzazioni, lookup di città, codici di localizzazione per ricerca per mercato. |
| 🔗 **Backlinks** *(Pro)* | Profilo, domini referenti, anchor, storico backlink. |
| ✍️ **Content** *(Pro)* | Idee, bozze, approvazioni, scheduling, calendario dei contenuti, pubblicazioni, scoring di keyword. |

L'insieme di tool live evolve. Per la lista esatta e aggiornata, esegui `tools/list` contro `https://mcp.vibeseo.dev/mcp`.

## Piani & accesso

I tool chiamano provider di dati a pagamento e modelli AI per tuo conto, quindi richiedono un abbonamento VibeSEO attivo — una prova o un piano a pagamento. Non esiste un livello anonimo o gratuito per sempre.

| | Prova | SEO Researcher | Pro |
|---|---|---|---|
| **Prezzo** | $0 oggi, carta richiesta | $9/mese | $39/mese |
| Keyword, domini, audit, GSC, competitive, localizzazioni | ✅ | ✅ | ✅ |
| Dati sui backlink | — | — | ✅ |
| Workflow di contenuto AI (idee, bozze, pubblicazione) | — | — | ✅ |
| Crediti mensili | 40 | 400 | 1500 |

La prova richiede la carta, parte da $0 ed è annullabile in qualsiasi momento; gira ai limiti del livello research e si converte nel piano scelto quando termina. I crediti misurano le chiamate che hanno un costo (lookup di keyword, audit, generazione AI) — vedi [vibeseo.dev/pricing](https://vibeseo.dev/pricing) per i piani attuali.

**Non devi mai uscire dalla chat per pagare.** Se chiami un tool senza un abbonamento attivo, senza crediti, o su un piano che non lo include, il risultato del tool torna con un link di checkout one-click o di ricarica per il tuo account.

## Client supportati

Percorsi di installazione per ciascuno:

- **Claude** (web e desktop) — pagina Connectors o `claude_desktop_config.json`
- **ChatGPT** — connector MCP custom con OAuth
- **Cursor** — installazione one-click via deeplink, o `~/.cursor/mcp.json`
- **VS Code** — installazione one-click via deeplink, o `.vscode/mcp.json`
- **Claude Code (CLI)** — `claude mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Gemini CLI** — `gemini mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Codex CLI** — `codex mcp add vibeseo --url https://mcp.vibeseo.dev/mcp`
- **Client MCP HTTP generico** — punta all'URL e lascia che completi l'OAuth discovery

Istruzioni complete di installazione per client: [docs/setup.md](docs/setup.md).

## Esempi di prompt

**Piano di keyword**
> «Trova keyword di confronto per la mia app di invoicing che siano realistiche da rankare.»

→ VibeSEO restituisce una lista di topic priorizzati (intent commerciale, difficoltà più bassa, angolo di confronto).

**Audit tecnico**
> «Audita il mio progetto e dimmi cosa fixare prima di pubblicare altri articoli.»

→ VibeSEO trasforma i dati di crawl in prossime azioni (canonical mancanti, immagini troppo pesanti, gap di link interni).

**Coda di pubblicazione**
> «Mostra i post pronti, genera la prossima bozza e schedula quello più forte.»

→ VibeSEO gestisce il workflow di contenuto (contatori di Ready/Drafting, schedula il prossimo articolo approvato).

Altro: [docs/examples.md](docs/examples.md).

## Autorizzazione e approval gate

Auth è OAuth 2.1 con PKCE. Il tuo assistente ottiene un token con scope `mcp:tools`, legato al tuo account VibeSEO. I token sono revocabili in qualsiasi momento dalla [pagina VibeSEO MCP](https://vibeseo.dev/mcp) sotto «Connected clients» — disconnettere un client revoca l'accesso immediatamente.

**MCP può aiutare a gestire il workflow, ma VibeSEO mantiene l'approval gate prima che il contenuto vada live.** Bozze e post schedulati passano comunque dallo step di review standard dentro VibeSEO.

Dettagli dell'OAuth flow: [docs/oauth.md](docs/oauth.md).

## Link del progetto

- Prodotto: [vibeseo.dev](https://vibeseo.dev)
- Pagina VibeSEO MCP: [vibeseo.dev/mcp](https://vibeseo.dev/mcp)
- Server MCP: `https://mcp.vibeseo.dev/mcp`
- OAuth issuer: `https://api.vibeseo.dev`
- Issues: [github.com/sultanlive/vibeseo-mcp/issues](https://github.com/sultanlive/vibeseo-mcp/issues)

## Licenza

MIT — vedi [LICENSE](LICENSE).

---

Fatto da [@sultanlive](https://github.com/sultanlive). VibeSEO è una piattaforma SEO hosted; questo repo è la documentazione del suo server MCP pubblico. Il sorgente del server non è open.
