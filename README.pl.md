[en](README.md) • [es](README.es.md) • [de](README.de.md) • [ja](README.ja.md) • [fr](README.fr.md) • [pt](README.pt.md) • [ru](README.ru.md) • [it](README.it.md) • [nl](README.nl.md) • **pl**

# VibeSEO MCP

**Serwer Model Context Protocol do badań SEO, audytów i workflow treści — zabezpieczony przez OAuth.**

VibeSEO MCP wprowadza pracę SEO na żywo prosto do Twojego asystenta AI. Podłącz Claude, ChatGPT, Cursor, VS Code lub klient CLI do VibeSEO. Następnie pytaj w naturalnym języku o analizę słów kluczowych, audyty, backlinki, trendy z Search Console i akcje workflow treści.

- **URL serwera:** `https://mcp.vibeseo.dev/mcp`
- **Transport:** Streamable HTTP
- **Auth:** OAuth 2.1 z PKCE, scope `mcp:tools`
- **Landing i setup:** [vibeseo.dev/mcp](https://vibeseo.dev/mcp)

## Szybki start

1. Załóż darmowe konto VibeSEO na [vibeseo.dev](https://vibeseo.dev).
2. Otwórz [stronę VibeSEO MCP](https://vibeseo.dev/mcp) i przejdź do linka instalacji dla swojego klienta.
3. Skorzystaj z instalacji one-click, skopiowanej komendy CLI lub ręcznego snippetu JSON/TOML.
4. Autoryzuj przez OAuth, gdy klient otworzy ekran zgody.
5. Pytaj asystenta o pracę SEO w naturalnym języku.

## Co możesz robić z poziomu czatu

- **🔍 Analiza słów kluczowych** — wolumeny, CPC, trudność, intencja, autouzupełnianie, słowa kluczowe-pytania, porównania i powiązane terminy.
- **🌐 Analiza domeny** — przegląd domeny, top słowa kluczowe, top strony, historia ruchu i sugestie konkurentów.
- **🔗 Backlinki** — profil, domeny odsyłające, anchor text i historia dowolnej domeny.
- **🛠️ Audyty strony** — uruchamiaj audyty, czytaj wyniki crawla, listuj problemy i priorytetyzuj poprawki.
- **📈 Performance w GSC** — podsumowania z podłączonej Google Search Console, top zapytania, top strony, trendy i diagnostyka per zapytanie.
- **🚀 Workflow treści** — listuj posty, odświeżaj pomysły, generuj szkice, zatwierdzaj gotowe artykuły, planuj i rewjuj.

## Powierzchnia narzędzi

Serwer MCP odzwierciedla ten sam workflow SEO co wewnątrz VibeSEO. Kategorie:

| Kategoria | Co pokrywa |
|---|---|
| 📁 **Projects** | Tworzenie projektów, aktualizacja informacji o stronie, zarządzanie konkurencją, utrzymywanie kontekstu konta na bieżąco. |
| 🔍 **Keywords** | Metryki, batche, sugestie, autouzupełnianie, pytania, porównania, historia, cleanup. |
| 🌐 **Domains** | Przegląd, top słowa kluczowe, top strony, historia ruchu, pomysły konkurencji, historia lookupów. |
| 🔗 **Backlinks** | Profil, domeny odsyłające, anchory, historia backlinków. |
| 🧯 **Audits** | Uruchamianie audytów strony, czytanie podsumowań, listowanie problemów, inspekcja przecrawlowanych stron. |
| 📊 **GSC** | Podłączone properties, status, podsumowania, top zapytania, top strony, trendy, szczegóły per zapytanie. |
| ✍️ **Content** | Pomysły, szkice, zatwierdzenia, planowanie, targety publikacji, publikacje, scoring słów kluczowych. |
| ⚔️ **Competitive** | Przegląd konkurencyjny i analiza keyword gap między domenami. |
| 📍 **Locations** | Kraje, języki, lokalizacje, lookup miast, kody lokalizacji do badań per rynek. |

Zestaw narzędzi na żywo ewoluuje. Po dokładną, aktualną listę — wykonaj `tools/list` na `https://mcp.vibeseo.dev/mcp`.

## Wspierane klienty

Ścieżki instalacji dla każdego:

- **Claude** (web i desktop) — strona Connectors lub `claude_desktop_config.json`
- **ChatGPT** — własny MCP connector z OAuth
- **Cursor** — instalacja one-click przez deeplink, lub `~/.cursor/mcp.json`
- **VS Code** — instalacja one-click przez deeplink, lub `.vscode/mcp.json`
- **Claude Code (CLI)** — `claude mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Gemini CLI** — `gemini mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Codex CLI** — `codex mcp add vibeseo --url https://mcp.vibeseo.dev/mcp`
- **Ogólny klient HTTP MCP** — wskaż URL i pozwól ukończyć OAuth discovery

Pełne instrukcje instalacji per klient: [docs/setup.md](docs/setup.md).

## Przykładowe prompty

**Plan słów kluczowych**
> „Znajdź porównawcze słowa kluczowe dla mojej aplikacji do fakturowania, które realistycznie da się wypozycjonować."

→ VibeSEO zwraca priorytetową listę tematów (intencja komercyjna, niższa trudność, kąt porównawczy).

**Audyt techniczny**
> „Zaudytuj mój projekt i powiedz, co naprawić przed publikacją kolejnych artykułów."

→ VibeSEO zamienia dane z crawla w konkretne następne akcje (brakujące canonicale, zbyt ciężkie obrazy, luki w linkowaniu wewnętrznym).

**Kolejka publikacji**
> „Pokaż gotowe posty, wygeneruj następny szkic i zaplanuj najmocniejszy."

→ VibeSEO zarządza workflow treści (liczniki Ready/Drafting, planuje następny zatwierdzony artykuł).

Więcej: [docs/examples.md](docs/examples.md).

## Autoryzacja i approval gate

Auth to OAuth 2.1 z PKCE. Twój asystent dostaje token o scope `mcp:tools`, powiązany z Twoim kontem VibeSEO. Tokeny można w każdej chwili odwołać ze [strony VibeSEO MCP](https://vibeseo.dev/mcp) w sekcji „Connected clients" — odłączenie klienta natychmiast odbiera mu dostęp.

**MCP może pomóc zarządzać workflow, ale VibeSEO trzyma approval gate zanim treść trafi na żywo.** Szkice i zaplanowane posty nadal przechodzą przez standardowy krok review w VibeSEO.

Szczegóły OAuth flow: [docs/oauth.md](docs/oauth.md).

## Linki projektu

- Produkt: [vibeseo.dev](https://vibeseo.dev)
- Strona VibeSEO MCP: [vibeseo.dev/mcp](https://vibeseo.dev/mcp)
- Serwer MCP: `https://mcp.vibeseo.dev/mcp`
- OAuth issuer: `https://api.vibeseo.dev`
- Issues: [github.com/sultanlive/vibeseo-mcp/issues](https://github.com/sultanlive/vibeseo-mcp/issues)

## Licencja

MIT — patrz [LICENSE](LICENSE).

---

Stworzone przez [@sultanlive](https://github.com/sultanlive). VibeSEO to hostowana platforma SEO; to repo to dokumentacja jej publicznego serwera MCP. Kod źródłowy serwera nie jest open.
