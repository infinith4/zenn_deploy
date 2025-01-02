---
title: "Internet Computer Protocol (ICP) 入門" # 記事のタイトル
emoji: "🧱" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech" # tech: 技術記事 / idea: アイデア記事
topics: ["web3", "icp", "internet computer protocol"] # タグ。["markdown", "rust", "aws"]のように指定する
published: true # 公開設定（falseにすると下書き）
---

# Internet Computer Protocol (ICP) 入門

## Internet Computer Protocol (ICP) 概要

Internet Computer Protocol (ICP)は、DFINITYが開発した分散型クラウドコンピューティングプラットフォームです。従来のブロックチェーンの機能を拡張し、Webアプリケーションを完全にオンチェーンでホスティングすることを可能にします。

## 主な特徴

- **Web速度**: 1-2秒での取引確定
- **無限のスケーラビリティ**: サブネットを追加することで水平方向にスケール可能
- **リバースガス**: ユーザーは gas fee を支払う必要がなく、開発者がサイクル（計算資源）を提供
- **スマートコントラクト**: Rustや Motoko言語でのスマートコントラクト開発が可能
- **Web3開発**: フロントエンド、バックエンド、データストレージを完全にオンチェーンで実現

## 技術的な特徴

### サブネット
- 独立して動作する複数のブロックチェーンネットワーク
- 異なる目的に最適化された設定が可能
- チェーン間通信により相互運用性を確保

### Internet Identity
- 生体認証を利用した安全な認証システム
- デバイスに依存しない認証
- プライバシーを重視した設計

### キャニスター
- ICPのスマートコントラクトの単位
- WebAssembly形式で実行
- メモリと計算能力を備えた完全な実行環境

## クイックスタート

Mac M1 上でのICPのプロジェクト作成、Local server の起動、Deployまでを実行します。

![png](https://github.com/infinith4/zenn_deploy/blob/main/articles/contents/web3-icp-quickstart/icp.drawio.png)

### dfx のインストール

```
sh -ci "$(curl -fsSL https://internetcomputer.org/install.sh)"
```

Version確認

```
dfx --version
```

dfx 0.24.3


#### プロジェクトの作成

```
dfx new {project name} --type=rust
```

例 : 

```
dfx new testproj02 --type=rust
```

```
cd testproj02
```


## Local server の起動

```
% dfx start

Running dfx start for version 0.24.3
Using the default configuration for the local shared network.
Initialized replica.
Initialized HTTP gateway.
Replica API running on 127.0.0.1:4943
Success! The dfx server is running.
You must open a new terminal to continue developing. If you'd prefer to stop, quit with 'Ctrl-C'.
```

#### create canister, build, deploy

新規ターミナルを開きます。

```
% dfx canister create --all
Creating canister testproj02_backend...
testproj02_backend canister created with canister id: a4tbr-q4aaa-aaaaa-qaafq-cai
Creating canister testproj02_frontend...
testproj02_frontend canister created with canister id: ajuq4-ruaaa-aaaaa-qaaga-cai
```

```
dfx build
```

wasm32 をインストールする必要があれば、以下でインストールします。（エラーコマンドに従う）

```
rustup target add wasm32-unknown-unknown
```

成功したらもう一度Buildを実行。
 
```
dfx build
```

Local server へDeployします。


```
dfx deploy
```

こんな感じで表示されれば成功🎊

```
Deployed canisters.
URLs:
  Frontend canister via browser
    testproj02_frontend:
      - http://127.0.0.1:4943/?canisterId=asrmz-lmaaa-aaaaa-qaaeq-cai
      - http://asrmz-lmaaa-aaaaa-qaaeq-cai.localhost:4943/
  Backend canister via Candid interface:
    testproj02_backend: http://127.0.0.1:4943/?canisterId=a3shf-5eaaa-aaaaa-qaafa-cai&id=avqkn-guaaa-aaaaa-qaaea-cai
```


バックエンドとフロントエンドにそれぞれアクセスして、動作確認したらOKです。

