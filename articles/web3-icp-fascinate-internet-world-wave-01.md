---
title: "IC (Internet Computer) による新しいインターネット世界" # 記事のタイトル
emoji: "♾️" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech" # tech: 技術記事 / idea: アイデア記事
topics: ["web3", "ic", "internet computer", "icp", "internet computer protocol", "icp hackathon"] # タグ。["markdown", "rust", "aws"]のように指定する
published: false # 公開設定（falseにすると下書き）
---

# IC (Internet Computer) による新しいインターネット世界

## IC (Internet Computer) の概要

IC (Internet Computer)は、DFINITY Foundation が開発した分散型クラウドコンピューティングプラットフォームの提供をするパブリック ブロックチェーン ネットワークです。

IC (Internet Computer)は、既存の中央集権的なクラウドサービス(AWS, Azure, GCP など)や従来のインターネットを置き換える存在です。
IC のビジョンは、ほぼ全てのアプリケーションがスマート コントラクトに置き換えられることです。このビジョンを実現するために、スマート コントラクトは従来のアプリケーションが稼働し、拡張できるように設計されています。

IC (Internet Computer) のネットワークは、許可のない分散型ガバナンスによって編成され、独立した当事者によって運営される主権ハードウェア デバイスでホストされています。その目的は、ネイティブ クラウド コンピューティング機能を使用してパブリック インターネットを拡張することです。

## IC (Internet Computer) の活用

主に以下の分野ので活用がされている。

- ソーシャルメディア
- ゲーム
- メタバース
- エンタープライズ向けシステム
- DeFi (Decentralized Finance)
- Decentralized AI (DeAI)

### 活用事例

以下はIC (Internet Computer) 上で動作するアプリケーションです。

### DSCVR (分散型 掲示板)

[DSCVR (分散型 掲示板)](https://dscvr.one/)

### Distrikt (分散型 SNS)

[Distrikt (分散型 SNS)](https://distrikt.app/)

### Dmail

[Dmail (分散型 メール)](https://dmail.ai/)

## IC (Internet Computer) の特徴

IC (Internet Computer) の特徴として以下が挙げられます。

- レスポンス速度が速い
- ガス代（インフラ費用）が安い
- スケーラビリティが可能
- 従来のweb3 での問題のUX体験が改善されている

### レスポンス速度が速い

[2024年12月時点での記事](https://www.icp-japan.org/post/icp-world-tps)によると高速のブロックチェーンの処理速度が記録されているため、既存のクラウドでのアプリケーションと引けを取らないクラウド基盤を提供できます。

### ガス代が安い

 [L1 での各ブロックチェーンの比較](https://wiki.internetcomputer.org/wiki/L1_comparison)において ICP のガス代のコストは最も安い結果が示されています。

### スケーラビリティが可能

IC は複数サブネットで構成されるため、理論上は容量やトランザクション数の制限はありません。

https://internetcomputer.org/how-it-works/scalability/

### 従来のweb3 での問題のUX体験が改善されている

従来のweb3, ブロックチェーンを利用した技術だとwallet の導入や秘密鍵の管理が面倒ですが、IC (Internet Computer) では秘密鍵の管理が容易にできます。
[Internet Identity（II）](https://internetcomputer.org/internet-identity) という技術が利用でき、IC上のdapp はIIによるユーザ認証を行うことができます。パスワードレスでPCやスマートフォンでの生体認証やYubiKeyなどのデバイスを利用したユーザー認証(WebAuthnに対応)が可能です。ユーザーが利用するデバイス上に秘密鍵が生成・保存され、生成された公開鍵とIdentity Anchor はII 上に保存されます。また、複数のデバイスでシームレスにdapp を利用できる仕組みになっています。
[Internet Identity（II）](https://identity.ic0.app/) からアカウントの発行が可能です。

### ネットワーク構成

subnet

## IC(Internet Computer) の構成

### Canister

Canister は永続的なデータを保存したり、ユーザーや他のキャニスターと通信するなどが可能な追加機能を備えた [WebAssembly (Wasm)](https://en.wikipedia.org/wiki/WebAssembly) プログラムです。

バックエンドcanister はIC上のスマートコントラクトの役割を果たします。

フロントエンドcanister はweb2でのフロントエンド技術がそのまま利用できます。

Canister は以下の言語で開発できます。

- Motoko
- Rust
- Python
- TypeScript
- EVM for Solidity
- C++

https://www.icp-japan.org/post/webassembly-on-the-internet-computerhttps://internetcomputer.org/docs/current/developer-docs/smart-contracts/overview/introduction

32-bit Wasm の4GB

## Chain-Key Cryptography

クライアントが canisterの呼び出しすると、トランザクションの結果はChain-key署名によって署名され、正しく生成されたことと改ざんされていないことを証明します。

Chain-Key 暗号化により、以下が実現できます。

- サブネット間での安全かつ効率的な通信
- 認証されたレスポンス

ICで利用する公開鍵は、外部ユーザーからの入力メッセージへの応答や、あるキャニスターから別のキャニスターへのメッセージなど、IC の出力を検証するために使用します。IC と他のブロックチェーンとの違いは他のブロックチェーンでは、ジェネシス ブロックからプロトコル全体を実行することによってのみ検証します。一方、IC では、単一のデジタル署名を検証するだけで検証できます。したがって、効率的な通信を実現する1つの重要な点です。

これにより、BitcoinやEthereumとも安全に連携できるという特徴を持っています。

https://internetcomputer.org/how-it-works/chain-key-technology

https://internetcomputer.org/docs/current/references/glossary/#chain-key


## 逆ガスモデル（Cycles）:

Ethereumなどで採用しているガス代の支払いモデルはユーザの負担だが、IC(Internet Computer)では開発者やサービス提供者が負担するモデルを採用している。ユーザにとって利用障壁が低くなっています。

### Network Nervous System

IC はNetwork Nervous System （NNS）というDAO（Decentralized Autonomous Organization）により実現されています。

