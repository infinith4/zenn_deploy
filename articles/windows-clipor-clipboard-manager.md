---
title: "Clipor - Windows向け高速クリップボードマネージャーを作った" # 記事のタイトル
emoji: "📋" # アイキャッチとして使われる絵文字（1文字だけ）
type: "idea" # tech: 技術記事 / idea: アイデア記事
topics: ["windows", "clipboard", "tauri", "rust", "react"] # タグ。["markdown", "rust", "aws"]のように指定する
published: false # 公開設定（false にすると下書き）
---

# Clipor - Windows向け高速クリップボードマネージャー

Windowsで作業していると、コピー＆ペーストを繰り返す場面が多々あります。しかし標準のクリップボードは直前の1件しか保持できず、何度もコピーし直す手間が発生します。そこで、**Clipor**というクリップボードマネージャーを開発しました。

- **GitHub**: https://github.com/infinith4/dev-clipor
- **公式サイト**: https://infinith4.github.io/dev-clipor/
- **Microsoft Store**: https://apps.microsoft.com/detail/9P0CRL2FRKF9?hl=ja&gl=JP

## Clipor とは

Clipor は、Windows向けの軽量・高速なクリップボードマネージャーです。コピーした内容を自動で蓄積し、いつでも呼び出せるようにします。Rust + Tauriによるネイティブ実装で、リソース消費を最小限に抑えながら快適な操作感を実現しています。

**無料・オープンソース（MIT ライセンス）** で、Microsoft Store からも入手できます。

## 主な機能

### クリップボード履歴

コピーしたテキスト・画像を自動で記録します。最大 1,000 件まで保存でき、全文検索やフィルタリングで素早く目的の内容を見つけられます。

![Cliporのメイン画面（日本語UI）](/images/windows-clipor-clipboard-manager/screenshot-ja.png)
*左ペインにクリップボード履歴一覧、右ペインにホバープレビュー*

### ピン機能

よく使うエントリをピン留めすることで、履歴の自動削除対象から除外できます。定型文や頻繁に使う情報を常に手元に置いておけます。

### スマートテンプレート

よく使うテキストをテンプレートとして保存・管理できます。`{{date}}`、`{{time}}`、`{{clipboard}}` などの動的変数もサポートしており、日付入り定型文なども自動生成できます。テンプレートはグループ管理・インポート／エクスポートにも対応しています。

### テキスト変換

全角／半角変換、余分な空白の除去、テキストの正規化などを一括で行えます。

### パスワード保護（AES-256-GCM 暗号化）

クリップボード履歴にパスワードを設定することで、AES-256-GCM + PBKDF2 による暗号化が有効になります。機密性の高い情報を安全に管理できます。なお、すべてのデータはローカルに保存され、外部への通信は一切行いません。

### グローバルホットキー

デフォルトは `Ctrl+Alt+Z` で、どのアプリケーションを使用中でも呼び出せます。ホットキーは以下の3モードからカスタマイズ可能です。

- カスタムホットキー指定
- Ctrl ダブル押し
- Alt ダブル押し

### スタートアップ起動

Windows 起動時に自動で立ち上がり、常にバックグラウンドで履歴を記録し続けます。

### ホバープレビュー

リスト上でエントリにマウスオーバーすると、全文をツールチップで確認できます。クリックせずに内容を把握できるため、選択ミスを防げます。

### 画像対応

テキストだけでなく、コピーした画像もサムネイル表示で保存・ペーストできます。

![画像コピーにも対応（英語UI）](/images/windows-clipor-clipboard-manager/screenshot-en.png)
*画像のサムネイルが履歴リストに表示される*

## 技術スタック

| レイヤー | 技術 |
|---|---|
| フロントエンド | React 19 + TypeScript + Vite |
| バックエンド | Rust + Tauri 2 |
| データベース | SQLite (rusqlite) |
| 暗号化 | AES-256-GCM + PBKDF2 |
| テスト | Vitest + Testing Library |

Rust + Tauri を採用することで、Electron ベースのアプリと比較して大幅に軽量・高速な動作を実現しています。

データの保存先は以下の通りです。

- クリップボード履歴: `%LOCALAPPDATA%\Clipor\history.db`
- 設定: `%LOCALAPPDATA%\Clipor\settings.json`

## 動作環境

- Windows 10 (バージョン 1809 / ビルド 17763 以降) または Windows 11
- 64 ビット (x64) アーキテクチャ
- WebView2 ランタイム
- 約 10 MB のディスク空き容量

## インストール方法

### Microsoft Store から（推奨）

Microsoft Store で「Clipor」を検索するか、以下のリンクからインストールできます。

https://apps.microsoft.com/detail/9P0CRL2FRKF9?hl=ja&gl=JP

### GitHub Releases から

MSI インストーラーまたは EXE セットアップファイルを GitHub の Releases ページからダウンロードできます。

https://github.com/infinith4/dev-clipor/releases

## まとめ

Clipor は以下のような方におすすめです。

- コピー＆ペーストを多用するエンジニア・ライター・デザイナー
- 定型文を頻繁に入力する業務をしている方
- クリップボード履歴をセキュアに管理したい方
- 軽量なツールを求めている方

無料で Microsoft Store から入手できますので、ぜひ試してみてください。

フィードバックや不具合報告は GitHub の Issues からお願いします。

https://github.com/infinith4/dev-clipor/issues
