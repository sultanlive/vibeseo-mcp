[en](README.md) • [es](README.es.md) • [de](README.de.md) • [ja](README.ja.md) • [fr](README.fr.md) • **pt** • [ru](README.ru.md) • [it](README.it.md) • [nl](README.nl.md) • [pl](README.pl.md)

# VibeSEO MCP

**Servidor Model Context Protocol para pesquisa SEO, auditorias e fluxo de conteúdo — protegido por OAuth.**

VibeSEO MCP traz trabalho SEO ao vivo direto pro seu assistente de IA. Conecte Claude, ChatGPT, Cursor, VS Code ou um cliente CLI ao VibeSEO. Depois é só pedir, em linguagem natural, pesquisa de palavras-chave, auditorias, backlinks, tendências do Search Console e ações de fluxo de conteúdo.

- **URL do servidor:** `https://mcp.vibeseo.dev/mcp`
- **Transporte:** Streamable HTTP
- **Auth:** OAuth 2.1 com PKCE, scope `mcp:tools`
- **Landing & setup:** [vibeseo.dev/mcp](https://vibeseo.dev/mcp)

## Início rápido

1. Crie uma conta gratuita VibeSEO em [vibeseo.dev](https://vibeseo.dev).
2. Abra a [página VibeSEO MCP](https://vibeseo.dev/mcp) e siga o link de instalação do seu cliente.
3. Use a instalação de um clique, o comando CLI copiado ou o snippet manual JSON/TOML.
4. Autorize via OAuth quando seu cliente abrir a tela de consentimento.
5. Peça trabalho SEO ao seu assistente em linguagem natural.

## O que você pode fazer pelo chat

- **🔍 Pesquisa de palavras-chave** — volumes, CPC, dificuldade, intenção, autocomplete, palavras-chave de perguntas, comparações e termos relacionados.
- **🌐 Análise de domínio** — overview do domínio, top keywords, top páginas, histórico de tráfego e sugestões de concorrentes.
- **🔗 Backlinks** — perfil, domínios referenciadores, anchor text e histórico de qualquer domínio.
- **🛠️ Auditorias de site** — iniciar auditorias, ler resultados de crawl, listar problemas e priorizar correções.
- **📈 Performance no GSC** — resumos do Google Search Console conectado, top queries, top páginas, tendências e diagnóstico por query.
- **🚀 Fluxo de conteúdo** — listar posts, atualizar ideias, gerar rascunhos, aprovar artigos prontos, agendar e revisar.

## Superfície de ferramentas

O servidor MCP espelha o mesmo fluxo SEO interno do VibeSEO. Categorias:

| Categoria | O que cobre |
|---|---|
| 📁 **Projects** | Criar projetos, atualizar informações do site, gerenciar concorrentes, manter o contexto da conta atualizado. |
| 🔍 **Keywords** | Métricas, batches, sugestões, autocomplete, perguntas, comparações, histórico, limpeza. |
| 🌐 **Domains** | Overview, top keywords, top páginas, histórico de tráfego, ideias de concorrentes, histórico de lookups. |
| 🔗 **Backlinks** | Perfil, domínios referenciadores, anchors, histórico de backlinks. |
| 🧯 **Audits** | Iniciar auditorias de site, ler resumos, listar problemas, inspecionar páginas crawleadas. |
| 📊 **GSC** | Propriedades conectadas, status, resumos, top queries, top páginas, tendências, detalhes por query. |
| ✍️ **Content** | Ideias, rascunhos, aprovações, agendamento, targets de publicação, publicações, scoring de keywords. |
| ⚔️ **Competitive** | Overview competitivo e análise de keyword gap entre domínios. |
| 📍 **Locations** | Países, idiomas, localizações, lookups de cidades, códigos de localização para pesquisa por mercado. |

O conjunto de ferramentas ao vivo evolui. Para a lista exata e atualizada, execute `tools/list` contra `https://mcp.vibeseo.dev/mcp`.

## Clientes suportados

Caminhos de instalação para cada um:

- **Claude** (web & desktop) — página Connectors ou `claude_desktop_config.json`
- **ChatGPT** — connector MCP customizado com OAuth
- **Cursor** — instalação de um clique via deeplink, ou `~/.cursor/mcp.json`
- **VS Code** — instalação de um clique via deeplink, ou `.vscode/mcp.json`
- **Claude Code (CLI)** — `claude mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Gemini CLI** — `gemini mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Codex CLI** — `codex mcp add vibeseo --url https://mcp.vibeseo.dev/mcp`
- **Cliente MCP HTTP genérico** — aponte pra URL e deixe completar o OAuth discovery

Instruções completas de instalação por cliente: [docs/setup.md](docs/setup.md).

## Exemplos de prompts

**Plano de keywords**
> "Encontre keywords de comparação pro meu app de invoicing que sejam realistas pra rankear."

→ VibeSEO devolve uma lista priorizada de tópicos (intenção comercial, menor dificuldade, ângulo de comparação).

**Auditoria técnica**
> "Audite meu projeto e me diga o que arrumar antes de publicar mais artigos."

→ VibeSEO converte dados de crawl em próximas ações (canônicas faltando, imagens pesadas, gaps de links internos).

**Fila de publicação**
> "Mostre posts prontos, gere o próximo rascunho e agende o mais forte."

→ VibeSEO gerencia o fluxo de conteúdo (contadores de Ready/Drafting, agenda o próximo artigo aprovado).

Mais: [docs/examples.md](docs/examples.md).

## Autorização e gate de aprovação

A auth é OAuth 2.1 com PKCE. Seu assistente recebe um token com scope `mcp:tools`, vinculado à sua conta VibeSEO. Tokens são revogáveis a qualquer momento pela [página VibeSEO MCP](https://vibeseo.dev/mcp) na seção "Connected clients" — desconectar um cliente revoga o acesso imediatamente.

**MCP pode ajudar a gerenciar o fluxo, mas o VibeSEO mantém o gate de aprovação antes do conteúdo ir ao ar.** Rascunhos e posts agendados continuam passando pelo passo de revisão padrão dentro do VibeSEO.

Detalhes do flow OAuth: [docs/oauth.md](docs/oauth.md).

## Links do projeto

- Produto: [vibeseo.dev](https://vibeseo.dev)
- Página VibeSEO MCP: [vibeseo.dev/mcp](https://vibeseo.dev/mcp)
- Servidor MCP: `https://mcp.vibeseo.dev/mcp`
- OAuth issuer: `https://api.vibeseo.dev`
- Issues: [github.com/sultanlive/vibeseo-mcp/issues](https://github.com/sultanlive/vibeseo-mcp/issues)

## Licença

MIT — veja [LICENSE](LICENSE).

---

Feito por [@sultanlive](https://github.com/sultanlive). VibeSEO é uma plataforma SEO hospedada; este repo é a documentação do servidor MCP público. O código do servidor não é open.
