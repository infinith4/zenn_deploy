---
title: "cli-tracker - ターミナルで完結する開発者向け時間管理CLIツールを作った" # 記事のタイトル
emoji: "⏱️" # アイキャッチとして使われる絵文字（1文字だけ）
type: "idea" # tech: 技術記事 / idea: アイデア記事
topics: ["cli", "nodejs", "typescript", "timetracking", "productivity"] # タグ。["markdown", "rust", "aws"]のように指定する
published: false # 公開設定（false にすると下書き）
---

# cli-tracker - ターミナルで完結する開発者向け時間管理CLIツール

開発中に時間管理ツールを使おうとすると、GUIアプリに切り替えるたびに集中が途切れてしまいます。「ちょっと記録するだけ」のつもりが、コンテキストスイッチのコストで結局ツールを使わなくなる——そんな経験から、**cli-tracker（`trc`）** を開発しました。

- **GitHub**: https://github.com/infinith4/dev-time-tracker
- **npm**: https://www.npmjs.com/package/@infinith4/cli-tracker

## cli-tracker とは

cli-tracker は、ターミナルから離れずに使える開発者向け時間管理CLIツールです。コマンド一発で計測を開始・停止でき、プロジェクトやタグによる分類、レポート出力、ポモドーロタイマーなど、時間管理に必要な機能をすべてCLI上で提供します。

**無料・オープンソース（MIT ライセンス）** で、npm から即座にインストールできます。

## 主な機能

### タイマーの開始・停止・再開

作業内容を引数で渡すだけで計測が始まります。途中で止めても、前回のタスクをそのまま再開できます。

```bash
trc start "code review"
trc stop
trc resume
```

### 作業ログの管理

記録した作業エントリの一覧表示、編集、削除、再計算が可能です。後から修正が必要な場面でも対応できます。

```bash
trc list
trc edit <id>
trc delete <id>
```

### プロジェクト・タグ管理

エントリにプロジェクト名やタグを紐づけて整理できます。複数プロジェクトを並行している場合でも、素早く切り替えながら記録できます。

### レポート出力

日次・週次・月次の集計レポートを生成します。プロジェクト別・タグ別の内訳も確認でき、振り返りや請求書作成に役立ちます。

```bash
trc report --period week
trc report --period month --project myapp
```

![trc report --period month](/images/cli-tracker-dev-time-management/screenshot-01.png)

### ポモドーロタイマー

作業サイクルとインターバルをカスタマイズできるポモドーロタイマーを内蔵しています。集中と休憩のリズムをターミナル上で管理できます。

### 目標設定・進捗トラッキング

日次・週次・月次の作業時間目標を設定し、達成状況をリアルタイムで確認できます。

### TUIダッシュボード

テキストUIの対話式ダッシュボードをターミナル上に表示できます。リアルタイムで作業状況を一覧できます。

```bash
trc ui
```

![trc ui - Interactive Dashboard](/images/cli-tracker-dev-time-management/screenshot-02.png)

### データのエクスポート・インポート

CSV または YAML 形式でデータをエクスポート・インポートできます。他ツールとの連携やバックアップに対応しています。

```bash
trc export --format csv
trc import data.csv
```

## 技術スタック

| レイヤー | 技術 |
|---|---|
| ランタイム | Node.js v18+ |
| 言語 | TypeScript |
| データベース | SQLite (`~/.cli-tracker/data.db`) |
| TUI | 対話式テキストUI |
| 対応OS | macOS / Linux / Windows |

完全オフラインで動作し、ネットワーク通信は一切行いません。データはすべてローカルに保存されます（`XDG_DATA_HOME` にも対応）。コマンド実行速度は 200ms 以下を目標としており、~10万件のエントリまで快適に動作します。

## インストール方法

Node.js v18 以上が必要です。

```bash
npm install -g @infinith4/cli-tracker
```

インストール後、`trc` コマンドが使えるようになります。

```bash
trc --help
```

## 使い方の例

```bash
# 作業開始
trc start "機能A実装"

# 現在のステータス確認
trc status

# 作業停止
trc stop

# 今週のレポート
trc report --period week

# ダッシュボード起動
trc ui
```

タイムゾーンは `--timezone` フラグまたは環境変数 `TRC_TIMEZONE` で設定できます。

## まとめ

cli-tracker は以下のような方におすすめです。

- 時間管理ツールを導入したいが、GUIアプリへの切り替えが面倒なエンジニア
- ターミナルを中心に作業しているフリーランサー・業務委託の方
- プロジェクトごとの工数を手軽に記録・集計したい方
- ポモドーロテクニックをターミナルで実践したい方

`npm install -g @infinith4/cli-tracker` でサクッと試せます。フィードバックや不具合報告は GitHub の Issues からお願いします。

https://github.com/infinith4/dev-time-tracker/issues
