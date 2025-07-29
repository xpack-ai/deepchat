<div align="center">

![Intro](./docs/assets/xpack/intro-bg.png)

</div>
<p align="center">
  <a href="https://github.com/ThinkInAIXYZ/deepchat/blob/main/LICENSE"><img src="https://img.shields.io/github/license/ThinkInAIXYZ/deepchat" alt="License Badge"/></a>
</p>

<div align="center">
  <a href="./README.zh.md">中文</a> / <a href="./README.md">English</a> / <a href="./README.jp.md">日本語</a>
</div>

## はじめに

このリポジトリは、**DeepChat**と**XPack.AI**の強力な統合を紹介し、世界中の数千の即座に使用可能なツールに接続することで、AIアシスタントの機能を拡張する方法を実演しています。複数のクラウドおよびローカル大規模言語モデルをサポートする機能豊富なオープンソースAIチャットプラットフォームである[DeepChat](https://deepchat.thinkinai.xyz/)の堅牢な基盤の上に構築されたこのプロジェクトは、XPackの広範なサービスマーケットプレイスを活用するためのModel Context Protocol（MCP）サービスの設定の実用的な例を提供します。

## DeepChatとは？

[DeepChat](https://deepchat.thinkinai.xyz/)は、様々な大規模言語モデルと対話するための統一されたインターフェースを提供する強力なオープンソースAIチャットプラットフォームです。OpenAI、Gemini、AnthropicなどのクラウドAPIや、ローカルにデプロイされたOllamaモデルを使用する場合でも、DeepChatは高度な機能を備えたスムーズなユーザー体験を提供します。

**主な機能：**

- **統一されたマルチモデル管理**: 1つのアプリケーションでほぼすべての主要なLLMをサポートし、複数のアプリを切り替える必要がありません
- **シームレスなローカルモデル統合**: 組み込みのOllamaサポートにより、コマンドライン操作なしでローカルモデルを管理・使用できます
- **高度なツール呼び出し**: 組み込みのMCPサポートにより、追加設定なしでコード実行、ウェブアクセス、その他のツールを利用可能です
- **強力な検索強化**: 複数の検索エンジンをサポートし、AIの応答をより正確でタイムリーにします
- **プライバシー重視**: ローカルデータストレージとネットワークプロキシのサポートにより、情報漏洩のリスクを軽減します
- **ビジネスフレンドリー**: Apache License 2.0の下でオープンソース化され、商用・個人利用の両方に適しています

## XPack.AIとは？

[XPack.AI](https://xpack.ai/)は、統一されたModel Context Protocol（MCP）を通じて、AIエージェントがグローバルサービスとツールの広大なエコシステムに接続できるプラットフォームです。XPackを使用すると、AIエージェントの機能を簡単に拡張し、金融、物流、メッセージング、その他の様々なドメインにわたる多様なAPIとサービスに、1分以内でアクセスできます。

## DeepChat + XPack: AIとグローバルサービスの橋渡し

このプロジェクトは、XPackをMCPサーバーとして利用するためのDeepChatの設定方法を実演することに焦点を当てています。これにより、あなたのDeepChatインスタンスはXPackの豊富なツールコレクションに即座にアクセスでき、以下のことが可能になります：

- **多様なサービスへのアクセス**: 金融データから画像処理まで、これまで手の届かなかった機能を統合
- **開発の加速**: 事前構築されたツールを活用してAI駆動ソリューションを迅速にプロトタイプ化・構築
- **ワークフローの合理化**: DeepChatのインテリジェンスとXPackの外部サービス統合を組み合わせて複雑なタスクを自動化
- **簡単なスケーリング**: カスタム統合コードを書くことなく、数千のグローバルサービスに接続

### アーキテクチャ概要

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   User Input    │    │    DeepChat      │    │   XPack.AI      │
│   (Web/Desktop) │◄──►│                  │◄──►│   Marketplace   │
└─────────────────┘    │  ┌─────────────┐ │    │                 │
                       │  │ MCP Client  │ │    │  ┌─────────────┐│
┌─────────────────┐    │  │             │ │    │  │1000+ Global ││
│  Local Tools    │◄──►│  │ • XPack     │ │    │  │Services     ││
│  & Resources    │    │  │ • Local     │ │    │  │• Finance    ││
└─────────────────┘    │  │ • Custom    │ │    │  │• Social     ││
                       │  └─────────────┘ │    │  │• Data       ││
┌─────────────────┐    │  ┌─────────────┐ │    │  │• AI/ML      ││
│  Multi-Model    │◄──►│  │   Chat      │ │    │  │• Utilities  ││
│  Support        │    │  │ Interface   │ │    │  └─────────────┘│
└─────────────────┘    │  └─────────────┘ │    └─────────────────┘
                       └──────────────────┘

```

**主要コンポーネント：**

- **DeepChat Core**: 高度な機能を備えたマルチモデルAIチャットプラットフォーム
- **MCP Client**: 外部ツールプロバイダーに接続するための標準化されたインターフェース
- **XPack MCP Server**: 統一APIを通じて1000以上のグローバルサービスへのゲートウェイ
- **Local Tools**: コード実行、ファイルシステムアクセスなどの組み込み機能
- **Multi-Model System**: 様々なクラウドおよびローカルLLMプロバイダーのサポート

## インストール

### DeepChatのダウンロードとインストール

まず、DeepChatがインストールされていることを確認してください。[GitHub Releasesページ](https://github.com/ThinkInAIXYZ/deepchat/releases)からお使いのオペレーティングシステム用の最新バージョンをダウンロードしてください。

**📥 クイックダウンロード：**

- **Windows**: `.exe`インストーラーをダウンロード
- **macOS**: `.dmg`インストールファイルをダウンロード
- **Linux**: `.AppImage`または`.deb`インストールファイルをダウンロード

ダウンロード後、インストーラーを実行し、画面の指示に従ってインストールを完了してください。

<table align="center">
  <tr>
    <td align="center" style="padding: 10px;">
      <img src='https://github.com/user-attachments/assets/5df4ed93-e4b5-4430-a1e3-bd9beba79e64' alt="DeepChat ライトモード" width="400"/>
      <br/>
    </td>
    <td align="center" style="padding: 10px;">
      <img src='https://github.com/user-attachments/assets/79be4873-f80e-43a9-bfac-e1efb246ea99' alt="DeepChat ダークモード" width="400"/>
      <br/>
    </td>
  </tr>
</table>

_開発、プロジェクト構造、アーキテクチャに関するより詳細なガイドについては、[開発者ガイド](./docs/developer-guide.md)をご覧ください。_

### XPack統合

DeepChatをXPackに接続するには、MCPサーバーを設定する必要があります。これにより、DeepChatはXPackを通じて利用可能なツールを発見し、活用できるようになります。

#### 1. XPack認証キーの取得：

- [XPack.AI](https://xpack.ai/)にアクセスしてアカウントを作成
- XPackダッシュボードから認証キーを生成

![XPack.ai Dashboard](./docs/assets/xpack/xpack-dashboard.png)

#### 2. DeepChatでXPack MCPを設定

##### オプションA: DeepChat設定UI経由（推奨）

設定UIを通じてMCPを設定：

- DeepChatアプリケーションを開く
- 設定ページに移動（⚙️ Setting）
- **MCP Setting**タブに切り替えて「Add」ボタンをクリック
- **Add Server**モーダルで、テキストエリアにxpack mcp設定を貼り付け：

  ```json
  {
    "mcpServers": {
      "xpack-mcp-market": {
        "type": "sse",
        "url": "https://mcp.xpack.ai/v1/mcp?apikey={YOUR_XPACK_AUTH_KEY}",
        "autoApprove": "all"
      }
    }
  }
  ```

  ![mcp config](./docs/assets/ui-mcp-config-1.png)

##### オプションB: 手動設定

手動設定を希望する場合は、DeepChatのDeepLink機能を使用してワンクリックMCPインストールも可能です：

```
deepChat://mcp/install?code={base64Encode(JSON.stringify(jsonConfig))}
```

⚠️ `YOUR_XPACK_AUTH_KEY`をダッシュボードから取得した実際のXPack認証キーに置き換えてください。

詳細なMCP設定手順については、[ユーザーガイド](./docs/user-guide.md)をご覧ください。

#### 3. MCPでDeepChatを実行

設定が完了すると、XPack MCPサーバーに自動的に接続し、利用可能なツールを発見します。

### 設定の確認

XPack MCP統合が正しく動作していることを確認するには：

1. DeepChat MCP設定パネルでスイッチを切り替えてMCPサーバーを有効にします。
2. ツールリストを確認：
   - 接続が成功すると、利用可能なツールが下に表示されます。
   - 任意のツールをクリックして、より詳細な情報を表示できます。
   - ツールリストと詳細なツール情報の存在は、サービス接続が正常で動作していることを示します。

![verify configuration](./docs/assets/ui-mcp-config-2.png)

正しく設定されていれば、DeepChatは利用可能なXPackツールを表示し、様々なタスクでそれらを使用できるようになります。

#### 使用方法

その後、DeepChatでアイデアやプロンプトを入力すると、XPackのツールを活用してタスクを実行します。XPackサービスを特に利用したい場合は、リクエストで「use XPack」と言及してください。

## 人気のタスク

このセクションでは、様々なタスクでDeepChatとXPackを活用する実用的な例を提供します。

### YouTubeコメントの分析と改善提案

YouTube動画のコメントを簡単に分析して、視聴者の感情を理解し、コンテンツ改善の提案を得ることができます。

```
xpackを使用して、このYouTube動画のコメントを読み取ってください：https://www.youtube.com/watch?v=LPZh9BOjkQs、フィードバックの感情を分析し、動画の改善点を推奨してください。
```

![Analyze YouTube comments Image](./docs/assets/xpack/demo-youtube-analysis.png)

### 現在の金価格と影響要因

最新の金価格を迅速に確認し、将来のトレンドに影響を与える可能性のある主要な要因を発見できます。

```
xpackを使用して現在の金のリアルタイム価格を調べ、将来の価格に影響を与える可能性のある具体的な要因を提供してください。
```

![Current Gold Price Image](./docs/assets/xpack/demo-gold-monitor.png)

### カスタム画像の生成

XPackを通じてAI画像生成ツールを使用して、カスタム画像を簡単に作成できます。

```
xpackで走っている子犬の画像を生成してください
```

![Generated image of a cute puppy running in a park](./docs/assets/xpack/demo-running-puppy.png)

### ドッグフード広告ポスターの生成

簡単にインスピレーションを検索し、ホットなプロモーション要素を組み合わせたカスタムドッグフード広告ポスターを生成できます。

```
ドッグフードのホットプロモーションポスターについて画像を検索し、ホット要素を組み合わせたドッグフード広告ポスターを生成してください
```

![Dog Food Hot Promotion Poster Example](./docs/assets/xpack/demo-dogfood-poster.png)

---

**DeepChatをグローバルサービスでスーパーチャージする準備はできましたか？** 今すぐXPack.AIを始めて、AI駆動アシスタンスの全ポテンシャルを解き放ちましょう！
