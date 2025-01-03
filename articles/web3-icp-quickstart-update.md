---
title: "Internet Computer Protocol (ICP) 入門 2" # 記事のタイトル
emoji: "🧱" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech" # tech: 技術記事 / idea: アイデア記事
topics: ["web3", "icp", "internet computer protocol"] # タグ。["markdown", "rust", "aws"]のように指定する
published: true # 公開設定（falseにすると下書き）
---

# Internet Computer Protocol (ICP) 入門 2

## クイックスタート (backend update)

Version確認

```
dfx --version
```

dfx 0.24.3


## Local server の起動


--clean で前回の状態をクリーンにしておきます。

```
% dfx start --host 127.0.0.1:7001 --clean

Running dfx start for version 0.24.3
Using the default configuration for the local shared network.
Initialized replica.
Initialized HTTP gateway.
Replica API running on 127.0.0.1:7001
Success! The dfx server is running.
You must open a new terminal to continue developing. If you'd prefer to stop, quit with 'Ctrl-C'.
```

### Backend 側 Methods 追加, Candid file 更新, build, deploy

新規ターミナルを開きます。

カレントディレクトリはtestproj02_update_canister とします。

./src/testproj02_update_canister_backend/src/lib.rs を更新します。

```
#[ic_cdk::query]
fn greet(name: String) -> String {
    format!("Hello, {}!", name)
}

#[ic_cdk::update]
fn world(name: String) -> String {
    format!("World, {}!", name)
}

#[ic_cdk::query]
fn hello(req: String) -> String {
    format!("req: {}", req)
}

// Enable Candid export
ic_cdk::export_candid!();
```

./src/testproj02_update_canister_backend/Cargo.toml
のdependencies のic-cdk を最新のバージョンに設定する。

```
[dependencies]
ic-cdk = "0.17.1"
```


```
dfx build
```

または

```
cargo build --release --target wasm32-unknown-unknown --package testproj02_update_canister_backend
```

以下のコマンドを実行します。

```
% candid-extractor target/wasm32-unknown-unknown/release/testproj02_update_canister_backend.wasm > ./src/testproj02_update_canister_backend/testproj02_update_canister_backend.did
```


Candid は、ICP で実行されているキャニスターと対話するためのインターフェース記述言語 (IDL) です。Candid ファイルは、キャニスターが定義する各関数の名前、パラメーター、結果形式、データ型など、キャニスターのインターフェースの言語に依存しない記述を提供します。 プロジェクトに Candid ファイルを追加することで、データが Rust の定義から適切に変換され、ICP で安全に実行されるようにすることができます。

Local server へDeployします。


```
dfx deploy
```

バックエンドにアクセスして、追加したMethodsが表示されたらOK


![](./contents/web3-icp-quickstart-update/2025-01-03%2013.30.06.png)


ref.

https://internetcomputer.org/docs/current/developer-docs/backend/rust/generating-candid

