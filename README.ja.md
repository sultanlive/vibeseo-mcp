[en](README.md) • [es](README.es.md) • [de](README.de.md) • **ja** • [fr](README.fr.md) • [pt](README.pt.md) • [ru](README.ru.md) • [it](README.it.md) • [nl](README.nl.md) • [pl](README.pl.md)

# VibeSEO MCP

**SEOリサーチ・サイト監査・コンテンツワークフローのための Model Context Protocol サーバー — OAuth で保護。**

VibeSEO MCP は、リアルタイムの SEO 業務を AI アシスタントの中に持ち込みます。Claude、ChatGPT、Cursor、VS Code、もしくは CLI クライアントを VibeSEO に接続。あとは自然言語で、キーワードリサーチ、サイト監査、被リンク分析、Search Console のトレンド、コンテンツワークフロー操作を依頼するだけです。

- **サーバー URL:** `https://mcp.vibeseo.dev/mcp`
- **トランスポート:** Streamable HTTP
- **認証:** OAuth 2.1 + PKCE、スコープ `mcp:tools`
- **ランディング & セットアップ:** [vibeseo.dev/mcp](https://vibeseo.dev/mcp)

## インストール

VibeSEO MCP は **リモート、OAuth で保護された** サーバーです。クライアントの MCP 設定に以下を追加してください:

```json
{
  "mcpServers": {
    "vibeseo": {
      "url": "https://mcp.vibeseo.dev/mcp"
    }
  }
}
```

**ワンクリックインストール:**

<a href="https://cursor.com/en/install-mcp?name=vibeseo&config=eyJuYW1lIjoidmliZXNlbyIsInR5cGUiOiJodHRwIiwidXJsIjoiaHR0cHM6Ly9tY3AudmliZXNlby5kZXYvbWNwIn0="><img src="https://vibeseo.dev/icons/cursor.svg" width="36" alt="Cursor"></a>&nbsp;&nbsp;<a href="https://insiders.vscode.dev/redirect/mcp/install?name=vibeseo&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.vibeseo.dev%2Fmcp%22%7D"><img src="https://vibeseo.dev/icons/vscode.svg" width="36" alt="VS Code"></a>&nbsp;&nbsp;<a href="https://claude.ai/settings/connectors"><img src="https://vibeseo.dev/icons/claude-desktop.svg" width="36" alt="Claude"></a>&nbsp;&nbsp;<a href="https://chatgpt.com/settings/connectors"><img src="https://vibeseo.dev/icons/chatgpt-icon.svg" width="36" alt="ChatGPT"></a>

CLI クライアント(Claude Code、Gemini CLI、Codex CLI)と手動スニペット: [対応クライアント](#対応クライアント) を参照。

## クイックスタート

1. [vibeseo.dev](https://vibeseo.dev) で VibeSEO アカウントを作成し、トライアルを開始 — 今日は $0、カード登録必須(詳細は[プランとアクセス](#プランとアクセス)を参照)。
2. [VibeSEO MCP ページ](https://vibeseo.dev/mcp) を開き、使用するクライアントのセットアップリンクを選択。
3. ワンクリックインストール、コピー済み CLI コマンド、または手動の JSON/TOML スニペットを利用。
4. クライアントが OAuth 同意画面を開いたら認可。
5. アシスタントに自然言語で SEO 業務を依頼。

## チャットからできること

- **🔍 キーワードリサーチ** — 検索ボリューム、CPC、難易度、インテント、オートコンプリート、質問キーワード、比較、関連語。
- **🌐 ドメイン分析** — ドメイン概要、上位キーワード、上位ページ、トラフィック履歴、競合候補。
- **🛠️ サイト監査** — 監査を開始、クロール結果を取得、課題を一覧化、修正の優先順位付け。
- **📈 GSC パフォーマンス** — 連携済み Google Search Console のサマリ、上位クエリ、上位ページ、トレンド、クエリ単位の診断。
- **🔗 被リンク** *(Pro)* — プロファイル、参照ドメイン、アンカーテキスト、任意ドメインの履歴。
- **🚀 コンテンツワークフロー** *(Pro)* — 記事一覧、アイディアの更新、ドラフト生成、承認、スケジューリング、レビュー。

## ツールサーフェス

MCP サーバーは VibeSEO 内部の SEO ワークフローをそのまま外部に公開したものです。カテゴリ:

| カテゴリ | カバー範囲 |
|---|---|
| 📁 **Projects** | プロジェクト一覧の取得、プロジェクト情報とサイト情報の参照、追跡中の競合の一覧・置き換え。 |
| 🔍 **Keywords** | メトリクス、オートコンプリート、関連語、質問形式、前置詞形式、比較キーワード、ルックアップ履歴。 |
| 🌐 **Domains** | 概要、上位キーワード、上位ページ、トラフィック履歴、競合アイディア、ルックアップ履歴。 |
| 🧯 **Audits** | サイト監査の開始、サマリ取得、課題一覧、クロール済みページの確認。 |
| 📊 **GSC** | 連携ステータス、サマリ、上位クエリ、上位ページ、トレンド、クエリ詳細。 |
| ⚔️ **Competitive** | 競合概要、ドメイン間のキーワードギャップ分析。 |
| 📍 **Locations** | 国、言語、ロケーション、都市ルックアップ、市場別リサーチ用のロケーションコード。 |
| 🔗 **Backlinks** *(Pro)* | プロファイル、参照ドメイン、アンカー、被リンク履歴。 |
| ✍️ **Content** *(Pro)* | アイディア、ドラフト、承認、スケジューリング、コンテンツカレンダー、公開、キーワードスコアリング。 |

ライブなツールセットは進化していきます。正確で最新の一覧は、`https://mcp.vibeseo.dev/mcp` に対して `tools/list` を実行してください。

## プランとアクセス

これらのツールはあなたに代わって有料のデータプロバイダーや AI モデルを呼び出すため、有効な VibeSEO サブスクリプション(トライアルまたは有料プラン)が必要です。匿名利用や永年無料プランはありません。

| | トライアル | SEO Researcher | Pro |
|---|---|---|---|
| **価格** | 今日は $0、カード登録必須 | 月額$9 | 月額$39 |
| キーワード、ドメイン、監査、GSC、競合分析、ロケーション | ✅ | ✅ | ✅ |
| 被リンクデータ | — | — | ✅ |
| AI コンテンツワークフロー(アイディア、ドラフト、公開) | — | — | ✅ |
| 月間クレジット | 40 | 400 | 1500 |

トライアルはカード登録必須で $0 から開始し、いつでもキャンセル可能です。リサーチプラン相当の制限で動作し、終了時には選択したプランへ自動移行します。クレジットはコストが発生する呼び出し(キーワードルックアップ、監査、AI 生成)を計測します — 最新のプラン内容は [vibeseo.dev/pricing](https://vibeseo.dev/pricing) を参照してください。

**支払いのためにチャットを離れる必要はありません。** 有効なサブスクリプションがない、クレジットが不足している、またはそのプランに含まれない機能を呼び出した場合、ツールの実行結果にはあなたのアカウント向けのワンクリック決済リンクまたはチャージリンクが返却されます。

## 対応クライアント

各クライアントのセットアップパス:

- **Claude** (Web & Desktop) — Connectors ページ、もしくは `claude_desktop_config.json`
- **ChatGPT** — OAuth 付きのカスタム MCP コネクタ
- **Cursor** — Deeplink によるワンクリックインストール、もしくは `~/.cursor/mcp.json`
- **VS Code** — Deeplink によるワンクリックインストール、もしくは `.vscode/mcp.json`
- **Claude Code (CLI)** — `claude mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Gemini CLI** — `gemini mcp add --transport http vibeseo https://mcp.vibeseo.dev/mcp`
- **Codex CLI** — `codex mcp add vibeseo --url https://mcp.vibeseo.dev/mcp`
- **汎用 HTTP MCP クライアント** — URL を指定し、OAuth Discovery を完了させる

クライアント別の完全なインストール手順: [docs/setup.md](docs/setup.md)。

## プロンプト例

**キーワード設計**
> 「請求書アプリで、現実的に上位を狙える比較系キーワードを見つけて。」

→ VibeSEO が優先順位付きのトピックリストを返却(商業意図、低難易度、比較アングル)。

**技術監査**
> 「プロジェクトを監査して、追加で記事を出す前に直すべきものを教えて。」

→ VibeSEO がクロールデータを次のアクションに変換(欠けた canonical、重すぎる画像、内部リンクのギャップ)。

**公開キュー**
> 「Ready の記事を見せて、次のドラフトを生成して、強いものをスケジュール。」

→ VibeSEO がコンテンツワークフローを管理(Ready/Drafting の件数、次に承認された記事をスケジュール)。

その他: [docs/examples.md](docs/examples.md)。

## 認可と承認ゲート

認証は OAuth 2.1 + PKCE。アシスタントは `mcp:tools` スコープのトークンを取得し、あなたの VibeSEO アカウントに紐付けされます。トークンは [VibeSEO MCP ページ](https://vibeseo.dev/mcp) の "Connected clients" からいつでも無効化可能 — クライアントの disconnect で即座にアクセスが失効します。

**MCP はワークフロー管理を支援しますが、コンテンツが公開される前の承認ゲートは VibeSEO 側に残ります。** ドラフトや予約投稿は通常通り VibeSEO 内のレビューステップを通ります。

OAuth フローの詳細: [docs/oauth.md](docs/oauth.md)。

## プロジェクトリンク

- プロダクト: [vibeseo.dev](https://vibeseo.dev)
- VibeSEO MCP ページ: [vibeseo.dev/mcp](https://vibeseo.dev/mcp)
- MCP サーバー: `https://mcp.vibeseo.dev/mcp`
- OAuth issuer: `https://api.vibeseo.dev`
- Issues: [github.com/sultanlive/vibeseo-mcp/issues](https://github.com/sultanlive/vibeseo-mcp/issues)

## ライセンス

MIT — [LICENSE](LICENSE) を参照。

---

[@sultanlive](https://github.com/sultanlive) 制作。VibeSEO はホスティング型 SEO プラットフォーム。本リポジトリは公開 MCP サーバーのドキュメントです。サーバーソースは非公開。
