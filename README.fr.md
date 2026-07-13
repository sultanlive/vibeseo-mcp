[en](README.md) • [es](README.es.md) • [de](README.de.md) • [ja](README.ja.md) • **fr** • [pt](README.pt.md) • [ru](README.ru.md) • [it](README.it.md) • [nl](README.nl.md) • [pl](README.pl.md)

# VibeSEO MCP

**Serveur Model Context Protocol pour la recherche SEO, les audits et le workflow de contenu — sécurisé par OAuth.**

VibeSEO MCP apporte le travail SEO live directement dans votre assistant IA. Connectez Claude, ChatGPT, Cursor, VS Code ou un client CLI à VibeSEO. Demandez ensuite en langage naturel de la recherche de mots-clés, des audits, des backlinks, des tendances Search Console et des actions de workflow de contenu.

- **URL du serveur :** `https://mcp.vibeseo.dev/mcp`
- **Transport :** Streamable HTTP
- **Auth :** OAuth 2.1 avec PKCE, scope `mcp:tools`
- **Landing & setup :** [vibeseo.dev/mcp](https://vibeseo.dev/mcp)

## Installation

VibeSEO MCP est un serveur **distant, sécurisé par OAuth**. Ajoutez ceci à la config MCP de votre client :

```json
{
  "mcpServers": {
    "vibeseo": {
      "url": "https://mcp.vibeseo.dev/mcp"
    }
  }
}
```

**Installation en un clic :**

<a href="https://cursor.com/en/install-mcp?name=vibeseo&config=eyJuYW1lIjoidmliZXNlbyIsInR5cGUiOiJodHRwIiwidXJsIjoiaHR0cHM6Ly9tY3AudmliZXNlby5kZXYvbWNwIn0="><img src="https://vibeseo.dev/icons/cursor.svg" width="36" alt="Cursor"></a>&nbsp;&nbsp;<a href="https://insiders.vscode.dev/redirect/mcp/install?name=vibeseo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.vibeseo.dev%2Fmcp%22%7D"><img src="https://vibeseo.dev/icons/vscode.svg" width="36" alt="VS Code"></a>&nbsp;&nbsp;<a href="https://claude.ai/settings/connectors"><img src="https://vibeseo.dev/icons/claude-desktop.svg" width="36" alt="Claude"></a>&nbsp;&nbsp;<a href="https://chatgpt.com/settings/connectors"><img src="https://vibeseo.dev/icons/chatgpt-icon.svg" width="36" alt="ChatGPT"></a>

Clients CLI (Claude Code, Gemini CLI, Codex CLI) et snippets manuels : voir [Clients supportés](#clients-supportés).

## Démarrage rapide

1. Créez un compte VibeSEO sur [vibeseo.dev](https://vibeseo.dev) et démarrez un essai — $0 aujourd'hui, carte requise (voir [Offres & accès](#offres--accès)).
2. Ouvrez la [page VibeSEO MCP](https://vibeseo.dev/mcp) et suivez le lien d'installation pour votre client.
3. Utilisez l'installation en un clic, la commande CLI copiée ou le snippet JSON/TOML manuel.
4. Autorisez via OAuth quand votre client ouvre l'écran de consentement.
5. Demandez du travail SEO à votre assistant en langage naturel.

## Ce que vous pouvez faire depuis le chat

- **🔍 Recherche de mots-clés** — volumes, CPC, difficulté, intention, idées d'autocomplete, mots-clés-question, comparaisons et termes liés.
- **🌐 Analyse de domaine** — vue d'ensemble, top mots-clés, top pages, historique de trafic et suggestions de concurrents.
- **🛠️ Audits de site** — lancer des audits, lire les résultats de crawl, lister les problèmes et prioriser les corrections.
- **📈 Performance GSC** — résumés de la Google Search Console connectée, top requêtes, top pages, tendances et diagnostic au niveau requête.
- **🔗 Backlinks** *(Pro)* — profil, domaines référents, ancres et historique de n'importe quel domaine.
- **🚀 Workflow de contenu** *(Pro)* — lister les posts, rafraîchir les idées, générer des brouillons, approuver, programmer et reviewer.

## Surface d'outils

Le serveur MCP reflète le même workflow SEO interne à VibeSEO. Catégories :

| Catégorie | Ce qu'elle couvre |
|---|---|
| 📁 **Projects** | Lister les projets, lire les infos du projet et du site, lister et remplacer les concurrents suivis. |
| 🔍 **Keywords** | Métriques, autocomplete, mots-clés liés, mots-clés-question, mots-clés de préposition et de comparaison, historique de lookups. |
| 🌐 **Domains** | Vue d'ensemble, top mots-clés, top pages, historique de trafic, idées de concurrents, historique de lookups. |
| 🧯 **Audits** | Lancer des audits de site, lire les résumés, lister les problèmes, inspecter les pages crawlées. |
| 📊 **GSC** | Statut de connexion, résumés, top requêtes, top pages, tendances, détails par requête. |
| ⚔️ **Competitive** | Vue d'ensemble concurrentielle et analyse de gap de mots-clés entre domaines. |
| 📍 **Locations** | Pays, langues, localisations, lookups de villes, codes de localisation pour de la recherche par marché. |
| 🔗 **Backlinks** *(Pro)* | Profil, domaines référents, ancres, historique de backlinks. |
| ✍️ **Content** *(Pro)* | Idées, brouillons, approbations, programmation, calendrier de contenu, publications, scoring de mots-clés. |

L'ensemble d'outils live évolue. Pour la liste exacte et à jour, exécutez `tools/list` contre `https://mcp.vibeseo.dev/mcp`.

## Offres & accès

Les outils appellent des fournisseurs de données payants et des modèles d'IA en votre nom ; ils nécessitent donc un abonnement VibeSEO actif — un essai ou un plan payant. Il n'existe pas de palier anonyme ou gratuit à vie.

| | Essai | SEO Researcher | Pro |
|---|---|---|---|
| **Prix** | $0 aujourd'hui, carte requise | $9/mois | $39/mois |
| Mots-clés, domaines, audits, GSC, concurrentiel, localisations | ✅ | ✅ | ✅ |
| Données de backlinks | — | — | ✅ |
| Workflow de contenu IA (idées, brouillons, publication) | — | — | ✅ |
| Crédits mensuels | 40 | 400 | 1500 |

L'essai nécessite une carte, démarre à $0, et peut être annulé à tout moment ; il tourne aux limites du niveau recherche et bascule vers le plan choisi à son terme. Les crédits mesurent les appels qui coûtent de l'argent (recherches de mots-clés, audits, génération IA) — voir [vibeseo.dev/pricing](https://vibeseo.dev/pricing) pour les plans actuels.

**Vous n'avez jamais besoin de quitter le chat pour payer.** Si vous appelez un outil sans abonnement actif, à court de crédits, ou sur un plan qui ne l'inclut pas, le résultat de l'outil renvoie un lien de paiement en un clic ou de recharge de crédits pour votre compte.

## Clients supportés

Chemins d'installation pour chacun :

- **Claude** (web & desktop) — page Connectors ou `claude_desktop_config.json`
- **ChatGPT** — connector MCP personnalisé avec OAuth
- **Cursor** — installation en un clic via deeplink, ou `~/.cursor/mcp.json`
- **VS Code** — installation en un clic via deeplink, ou `.vscode/mcp.json`
- **Claude Code (CLI)** — `claude mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Gemini CLI** — `gemini mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Codex CLI** — `codex mcp add vibeseo --url https://mcp.vibeseo.dev/mcp`
- **Client MCP HTTP générique** — pointer sur l'URL, laisser faire l'OAuth discovery

Instructions d'installation complètes par client : [docs/setup.md](docs/setup.md).

## Exemples de prompts

**Plan de mots-clés**
> « Trouve-moi des mots-clés de comparaison pour mon app d'invoicing, réalistes à ranker. »

→ VibeSEO renvoie une liste de sujets priorisés (intention commerciale, difficulté basse, angle comparaison).

**Audit technique**
> « Audite mon projet et dis-moi ce qu'il faut corriger avant de publier plus d'articles. »

→ VibeSEO transforme les données de crawl en prochaines actions (canoniques manquantes, images trop lourdes, lacunes de liens internes).

**Queue de publication**
> « Montre-moi les posts prêts, génère le prochain brouillon et programme le plus fort. »

→ VibeSEO gère le workflow de contenu (compteurs Ready/Drafting, programme le prochain article approuvé).

Plus : [docs/examples.md](docs/examples.md).

## Autorisation et gate d'approbation

L'auth est OAuth 2.1 avec PKCE. Votre assistant reçoit un token au scope `mcp:tools`, lié à votre compte VibeSEO. Les tokens sont révocables à tout moment depuis la [page VibeSEO MCP](https://vibeseo.dev/mcp) sous « Connected clients » — déconnecter un client révoque son accès immédiatement.

**MCP peut aider à gérer le workflow, mais VibeSEO garde le gate d'approbation avant la mise en ligne du contenu.** Les brouillons et posts programmés passent toujours par l'étape de review standard à l'intérieur de VibeSEO.

Détails du flow OAuth : [docs/oauth.md](docs/oauth.md).

## Liens du projet

- Produit : [vibeseo.dev](https://vibeseo.dev)
- Page VibeSEO MCP : [vibeseo.dev/mcp](https://vibeseo.dev/mcp)
- Serveur MCP : `https://mcp.vibeseo.dev/mcp`
- Issuer OAuth : `https://api.vibeseo.dev`
- Issues : [github.com/sultanlive/vibeseo-mcp/issues](https://github.com/sultanlive/vibeseo-mcp/issues)

## Licence

MIT — voir [LICENSE](LICENSE).

---

Fait par [@sultanlive](https://github.com/sultanlive). VibeSEO est une plateforme SEO hébergée ; ce dépôt est la documentation de son serveur MCP public. Le code source du serveur n'est pas open.
