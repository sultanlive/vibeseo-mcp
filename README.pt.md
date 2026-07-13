[en](README.md) • [es](README.es.md) • [de](README.de.md) • [ja](README.ja.md) • [fr](README.fr.md) • **pt** • [ru](README.ru.md) • [it](README.it.md) • [nl](README.nl.md) • [pl](README.pl.md)

# VibeSEO MCP

**Servidor Model Context Protocol para pesquisa SEO, auditorias e fluxo de conteúdo — protegido por OAuth.**

VibeSEO MCP traz trabalho SEO ao vivo direto pro seu assistente de IA. Conecte Claude, ChatGPT, Cursor, VS Code ou um cliente CLI ao VibeSEO. Depois é só pedir, em linguagem natural, pesquisa de palavras-chave, auditorias, backlinks, tendências do Search Console e ações de fluxo de conteúdo.

- **URL do servidor:** `https://mcp.vibeseo.dev/mcp`
- **Transporte:** Streamable HTTP
- **Auth:** OAuth 2.1 com PKCE, scope `mcp:tools`
- **Landing & setup:** [vibeseo.dev/mcp](https://vibeseo.dev/mcp)

## Instalação

VibeSEO MCP é um servidor **remoto, protegido por OAuth**. Adicione isso ao config MCP do seu cliente:

```json
{
  "mcpServers": {
    "vibeseo": {
      "url": "https://mcp.vibeseo.dev/mcp"
    }
  }
}
```

**Instalação de um clique:**

<a href="https://cursor.com/en/install-mcp?name=vibeseo&config=eyJuYW1lIjoidmliZXNlbyIsInR5cGUiOiJodHRwIiwidXJsIjoiaHR0cHM6Ly9tY3AudmliZXNlby5kZXYvbWNwIn0="><img src="https://vibeseo.dev/icons/cursor.svg" width="36" alt="Cursor"></a>&nbsp;&nbsp;<a href="https://insiders.vscode.dev/redirect/mcp/install?name=vibeseo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.vibeseo.dev%2Fmcp%22%7D"><img src="https://vibeseo.dev/icons/vscode.svg" width="36" alt="VS Code"></a>&nbsp;&nbsp;<a href="https://claude.ai/settings/connectors"><img src="https://vibeseo.dev/icons/claude-desktop.svg" width="36" alt="Claude"></a>&nbsp;&nbsp;<a href="https://chatgpt.com/settings/connectors"><img src="https://vibeseo.dev/icons/chatgpt-icon.svg" width="36" alt="ChatGPT"></a>

Clientes CLI (Claude Code, Gemini CLI, Codex CLI) e snippets manuais: veja [Clientes suportados](#clientes-suportados).

## Início rápido

1. Crie uma conta VibeSEO em [vibeseo.dev](https://vibeseo.dev) e comece um trial — $0 hoje, cartão necessário (veja [Planos & acesso](#planos--acesso)).
2. Abra a [página VibeSEO MCP](https://vibeseo.dev/mcp) e siga o link de instalação do seu cliente.
3. Use a instalação de um clique, o comando CLI copiado ou o snippet manual JSON/TOML.
4. Autorize via OAuth quando seu cliente abrir a tela de consentimento.
5. Peça trabalho SEO ao seu assistente em linguagem natural.

## O que você pode fazer pelo chat

- **🔍 Pesquisa de palavras-chave** — volumes, CPC, dificuldade, intenção, autocomplete, palavras-chave de perguntas, comparações e termos relacionados.
- **🌐 Análise de domínio** — overview do domínio, top keywords, top páginas, histórico de tráfego e sugestões de concorrentes.
- **🛠️ Auditorias de site** — iniciar auditorias, ler resultados de crawl, listar problemas e priorizar correções.
- **📈 Performance no GSC** — resumos do Google Search Console conectado, top queries, top páginas, tendências e diagnóstico por query.
- **🔗 Backlinks** *(Pro)* — perfil, domínios referenciadores, anchor text e histórico de qualquer domínio.
- **🚀 Fluxo de conteúdo** *(Pro)* — listar posts, atualizar ideias, gerar rascunhos, aprovar artigos prontos, agendar e revisar.

## Superfície de ferramentas

O servidor MCP espelha o mesmo fluxo SEO interno do VibeSEO. Categorias:

| Categoria | O que cobre |
|---|---|
| 📁 **Projects** | Listar projetos, ler informações de projeto e site, listar e substituir concorrentes rastreados. |
| 🔍 **Keywords** | Métricas, autocomplete, keywords relacionadas, de perguntas, preposições e comparações, histórico de lookups. |
| 🌐 **Domains** | Overview, top keywords, top páginas, histórico de tráfego, ideias de concorrentes, histórico de lookups. |
| 🧯 **Audits** | Iniciar auditorias de site, ler resumos, listar problemas, inspecionar páginas crawleadas. |
| 📊 **GSC** | Status de conexão, resumos, top queries, top páginas, tendências, detalhes por query. |
| ⚔️ **Competitive** | Overview competitivo e análise de keyword gap entre domínios. |
| 📍 **Locations** | Países, idiomas, localizações, lookups de cidades, códigos de localização para pesquisa por mercado. |
| 🔗 **Backlinks** *(Pro)* | Perfil, domínios referenciadores, anchors, histórico de backlinks. |
| ✍️ **Content** *(Pro)* | Ideias, rascunhos, aprovações, agendamento, calendário de conteúdo, publicações, scoring de keywords. |

O conjunto de ferramentas ao vivo evolui. Para a lista exata e atualizada, execute `tools/list` contra `https://mcp.vibeseo.dev/mcp`.

## Planos & acesso

As ferramentas chamam provedores de dados pagos e modelos de IA em seu nome, então precisam de uma assinatura VibeSEO ativa — um trial ou um plano pago. Não existe tier anônimo ou gratuito pra sempre.

| | Trial | SEO Researcher | Pro |
|---|---|---|---|
| **Preço** | $0 hoje, cartão necessário | $9/mês | $39/mês |
| Keywords, domains, audits, GSC, competitive, locations | ✅ | ✅ | ✅ |
| Dados de backlinks | — | — | ✅ |
| Fluxo de conteúdo com IA (ideias, rascunhos, publicação) | — | — | ✅ |
| Créditos mensais | 40 | 400 | 1500 |

O trial exige cartão, começa em $0 e pode ser cancelado a qualquer momento; ele roda nos limites do nível research e converte pro plano escolhido quando termina. Os créditos medem as chamadas que custam dinheiro (lookups de keywords, auditorias, geração por IA) — veja [vibeseo.dev/pricing](https://vibeseo.dev/pricing) pros planos atuais.

**Você nunca precisa sair do chat pra pagar.** Se você chamar uma ferramenta sem assinatura ativa, sem créditos, ou num plano que não inclui aquele recurso, o resultado da ferramenta volta com um link de checkout de um clique ou de recarga pra sua conta.

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
