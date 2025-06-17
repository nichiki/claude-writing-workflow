# Claude Writing Workflow

Claude Codeを使用した対話型文章執筆ワークフローシステムです。AIとの対話を通じて、高品質な文章を効率的に作成できます。

## 🎯 プロジェクト概要

このプロジェクトは、Claude（Anthropic社のAI）と対話しながら文章を作成するためのワークフローフレームワークです。ユーザーの意図を最大限に反映しながら、AIの強みを活かした執筆支援を実現します。

### 基本理念

- **制作者（ユーザー）の意図を最大限に反映する**
- 対話的な要件ヒアリングと都度確認による品質確保
- AIの強みを活かした効率化
- ワークフロー自体の継続的改善

## ✨ 主な特徴

### 1. 対話的要件ヒアリング
- 柔軟な制作プロセスの実現
- 様々なケース（具体的イメージあり/なし、コンセプトベース等）に対応
- 提案・修正のループを納得いくまで繰り返し可能

### 2. 設定ファイル＋対話の組み合わせ
- **設定ファイル**: 定型的な要素（論調、ターゲット、目的）を事前定義
- **対話**: 毎回変わる内容にフォーカス
- note向け、ブログ向け、論文向けなどのテンプレート対応

### 3. 事前リサーチ機能
- テーマに基づいた自動的な情報収集
- 複数視点からの並列リサーチ
- リサーチ結果を記事執筆に活用

### 4. 構造化された執筆プロセス
- リサーチ → アウトライン → 執筆 → 品質チェック
- 各ステップでの確認と修正
- 文字数管理と進捗の可視化

### 5. 自動ファイル管理
- 日付ベースのプロジェクトディレクトリ
- ドラフトと最終版の自動保存
- リサーチ結果の体系的な保存

## 🚀 セットアップ

### 必要な環境
- [Claude Code](https://claude.ai/code) のインストール
- macOS、Linux、またはWindows

### インストール手順

1. リポジトリをクローン
```bash
git clone https://github.com/nichiki/claude-writing-workflow.git
cd claude-writing-workflow
```

2. Claude Codeを実行
```bash
claude
```

## 📝 使用方法

### 基本的な使い方

1. Claude Codeで以下のコマンドを実行：
```
/project:write
```

2. 対話的に要件を入力：
```
Claude: 文章のテーマを教えてください。

You: AIを活用した業務効率化について

Claude: 執筆の目的は何ですか？
1. 情報提供・解説
2. 提案・企画
3. レポート・報告
4. その他（自由入力）

You: 1
```

3. リサーチの実施（推奨）：
```
Claude: より良い記事にするため、事前リサーチを行いますか？（推奨）
1. はい（推奨）
2. いいえ

You: 1
```

4. アウトラインの確認と執筆：
- Claudeが提案するアウトラインを確認
- 各セクションごとに執筆を進行
- 都度確認しながら修正可能

### 実行例

実際の執筆例は[articles/2025-06-17_tomato-yogurt-curry](./articles/2025-06-17_tomato-yogurt-curry)ディレクトリを参照してください。リサーチ結果から最終的な記事まで、実際のワークフローの成果物を確認できます。

## 📁 プロジェクト構造

```
claude-writing-workflow/
├── .claude/
│   └── commands/         # Claudeコマンド定義
│       └── write.md      # 文章執筆コマンド
├── writing-configs/      # 文章執筆用の設定ファイル
│   └── default.yaml      # デフォルト設定
├── articles/             # 執筆した文章の保存先
│   └── YYYY-MM-DD_{slug}/
│       ├── draft.md      # 執筆中のドラフト
│       ├── article.md    # 完成版
│       └── assets/       # 関連リソース
│           └── research.md # リサーチ結果
├── CLAUDE.md            # プロジェクトガイドライン
└── README.md            # このファイル
```

## ⚙️ 設定ファイルのカスタマイズ

`writing-configs/`ディレクトリに独自の設定ファイルを作成できます。

### 設定ファイルの例（blog.yaml）

```yaml
metadata:
  config_name: "blog"
  description: "ブログ記事用の設定"

writing_style:
  tone: "カジュアル"
  person: "です・ます調"
  word_count_range: [1500, 2500]

audience:
  primary: "技術ブログ読者"
  knowledge_level: "中級〜上級"
  age_range: "20-40代"

structure:
  introduction:
    purpose: "課題提起と記事の価値を示す"
    length_ratio: 0.2
  body:
    purpose: "実践的な内容を具体例とともに展開"
    length_ratio: 0.65
    sections: 4-6
  conclusion:
    purpose: "まとめと次のアクション"
    length_ratio: 0.15

quality_checks:
  - "具体例は含まれているか"
  - "実践可能な内容か"
  - "読者の課題を解決できるか"
```

## 🚀 拡張の可能性

このプロジェクトは、シンプルな対話型ワークフローを示すサンプルですが、様々な方向への拡張が可能です。

### 自己改善するワークフロー
**Claude Codeの最大の強みは、ワークフロー自体を自分で修正・改善できることです。** 使用中に不便を感じたら、その場でClaudeに改善を依頼するだけで、コマンドファイルや設定を自動的に更新できます。例えば：

- 「このステップは不要だから削除して」
- 「文字数チェックをもっと詳細にして」
- 「新しい文体設定を追加して」

このような要望を伝えるだけで、Claudeがワークフローを進化させていきます。

### 非同期・並列実行
現在は対話型の実行方式ですが、要件をすべてファイルで定義することで、複数の記事を並列で生成することも可能になります。バッチ処理やCI/CDパイプラインへの組み込みなど、自動化の選択肢が広がります。

### MCPによる機能拡張
Model Context Protocol (MCP) を活用することで、必要な機能を柔軟に追加できます：

- **コンテンツ生成**: 記事に合わせた画像の自動生成、図表の作成
- **外部連携**: SNSへの自動投稿、CMSへの直接公開、Slackへの通知
- **品質向上**: 外部校正ツールとの連携、SEO分析ツールの統合
- **パーソナライズ**: 自分の過去記事をRAGで参照し文体を統一、独自の品質基準でのチェック

このフレームワークをベースに、あなたのニーズに合わせた独自のワークフローを構築できます。可能性は無限大です！

## 🤝 貢献方法

プルリクエストを歓迎します！

1. このリポジトリをフォーク
2. 機能ブランチを作成（`git checkout -b feature/amazing-feature`）
3. 変更をコミット（`git commit -m 'Add amazing feature'`）
4. ブランチにプッシュ（`git push origin feature/amazing-feature`）
5. プルリクエストを作成

### 貢献のガイドライン

- コードやドキュメントは日本語でOK
- 既存のコードスタイルに従う
- 新機能は設定ファイルで制御可能にする
- ユーザーの意図を最優先に考える

## 📄 ライセンス

このプロジェクトはMITライセンスの下で公開されています。

```
MIT License

Copyright (c) 2025 Nobuo Ichiki

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## 🙏 謝辞

- [Anthropic](https://www.anthropic.com/) - Claude AIの開発
- Claude Codeコミュニティ - フィードバックとサポート

---

質問や提案がある場合は、[Issues](https://github.com/nichiki/claude-writing-workflow/issues)でお知らせください。