---
title: "IC (Internet Computer) による新しいインターネット世界" # 記事のタイトル
emoji: "♾️" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech" # tech: 技術記事 / idea: アイデア記事
topics: ["web3", "ic", "internet computer", "icp", "internet computer protocol", "icp hackathon"] # タグ。["markdown", "rust", "aws"]のように指定する
published: false # 公開設定（falseにすると下書き）
---

# IC (Internet Computer) による新しいインターネット世界

IC (Internet Computer) は ブロックチェーンを用いた分散型クラウドであり、従来のweb2 の中央集権的なインターネットへの革新をもたらす技術です。
web2 の世界と共存しつつも新しいインターネット世界を見せてくれることでしょう。

IC (Internet Computer) の概念からロードマップまでをご紹介します。

## IC (Internet Computer) の概要

IC (Internet Computer)は、DFINITY Foundation が開発した分散型クラウドコンピューティングプラットフォームの提供をするパブリック ブロックチェーン ネットワークです。

IC (Internet Computer)は、既存の中央集権的なクラウドサービス(AWS, Azure, GCP など)や従来のインターネットを置き換える存在です。
IC のビジョンは、ほぼ全てのアプリケーションがスマート コントラクトに置き換えられることです。このビジョンを実現するために、スマート コントラクトは従来のアプリケーションが稼働し、拡張できるように設計されています。

IC (Internet Computer) のネットワークは、許可のない分散型ガバナンスによって編成され、独立した当事者によって運営される主権ハードウェア デバイスでホストされています。その目的は、ネイティブ クラウド コンピューティング機能を使用してパブリック インターネットを拡張することです。

## IC (Internet Computer) の活用

主に以下の分野での活用がされています。

- ソーシャルメディア
- ゲーム
- メタバース
- エンタープライズ向けシステム
- DeFi (Decentralized Finance)
- Decentralized AI (DeAI)

### 活用事例

IC (Internet Computer) 上で動作するアプリケーションが紹介されています。

[https://internetcomputer.org/ecosystem](https://internetcomputer.org/ecosystem)

ここでは主なものをピックアップしてご紹介します。

### DSCVR

[DSCVR](https://dscvr.one/) は分散型掲示板のサービスを提供している。コメントを書き込むことで報酬が付与されるComment to Earn のような仕組みになっている。

### Distrikt

[Distrikt](https://distrikt.app/) は分散型 SNSであり、Xと使い勝手はほぼ同じサービスです。ユーザーは[Internet Identity（II）](https://identity.ic0.app/) での認証を行い、投稿や画像、いいねなどはブロックチェーン上に記録されるため、データはユーザ自身に所有権があります。

### **OpenChat**

完全オンチェーンのSNSであり、トークンの送金、ビデオ通話、チャットグループなどの機能があります。ユーザーは[Internet Identity（II）](https://identity.ic0.app/) での認証を行い、真正性が高いSNSを実現している。2024年11月時点で [1日あたりのアクティブユーザーは数は15,000人以上](https://www.icp-japan.org/post/openchat-ddau-15000)。

### Dmail

[Dmail](https://dmail.ai/) は分散型 メールであり、従来のweb2 のメールサービス、Dropbox、Metamaskなどとの連携も可能で低コストでのメールサービスを実現しています。

### Onicai

[Onicai](https://www.onicai.com/) はLLMをIC上で実装するためのサービスです。[Onicai のX](https://x.com/onicaiHQ/status/1879211961088659974) によると 1.5 Billion のLLM パラメータを実行することができたとありましたが、WASM の制限もあるためまだ課題はあります。

## IC (Internet Computer) とそれを取り巻くエンティティの概念図

IC (Internet Computer) とそれを取り巻くエンティティの概念図は以下のようになります。
IC 内部はもっと詳細な技術が利用されていますが、ここでは簡略化しています。
IC に対するシステム運用の方針をNNSで決定し、Canisterの運用費としてCanister運用者・所有者は手数料を支払います。Canisterによる収益をCanister運用者・所有者はエンドユーザから収益を得ます。
データセンター自体は運用手数料を取得します。

![](/images/web3-icp-fascinate-internet-world-wave-01/icp.drawio-overview.png)

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

[https://internetcomputer.org/how-it-works/scalability/](https://internetcomputer.org/how-it-works/scalability/)

### 従来のweb3 での問題のUX体験が改善されている

従来のweb3, ブロックチェーンを利用した技術だとwallet の導入や秘密鍵の管理が面倒ですが、IC (Internet Computer) では秘密鍵の管理が容易にできます。
[Internet Identity（II）](https://internetcomputer.org/internet-identity) という技術が利用でき、IC上のdapp はIIによるユーザ認証を行うことができます。パスワードレスでPCやスマートフォンでの生体認証やYubiKeyなどのデバイスを利用したユーザー認証(WebAuthnに対応)が可能です。ユーザーが利用するデバイス上に秘密鍵が生成・保存され、生成された公開鍵とIdentity Anchor はII 上に保存されます。また、複数のデバイスでシームレスにdapp を利用できる仕組みになっています。
[Internet Identity（II）](https://identity.ic0.app/) からアカウントの発行が可能です。

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

[https://www.icp-japan.org/post/webassembly-on-the-internet-computer](https://www.icp-japan.org/post/webassembly-on-the-internet-computer)[https://internetcomputer.org/docs/current/developer-docs/smart-contracts/overview/introduction](https://internetcomputer.org/docs/current/developer-docs/smart-contracts/overview/introduction)

### Chain-Key Cryptography

クライアントが canisterの呼び出しすると、トランザクションの結果はChain-key署名によって署名され、正しく生成されたことと改ざんされていないことを証明します。

Chain-Key 暗号化により、以下が実現できます。

- サブネット間での安全かつ効率的な通信
- 認証されたレスポンス

ICで利用する公開鍵は、外部ユーザーからの入力メッセージへの応答や、あるキャニスターから別のキャニスターへのメッセージなど、IC の出力を検証するために使用します。IC と他のブロックチェーンとの違いは他のブロックチェーンでは、ジェネシス ブロックからプロトコル全体を実行することによってのみ検証します。一方、IC では、単一のデジタル署名を検証するだけで検証できます。したがって、効率的な通信を実現する1つの重要な点です。

https://internetcomputer.org/how-it-works/chain-key-technology

https://internetcomputer.org/docs/current/references/glossary/#chain-key

これにより、BitcoinやEthereumとも安全に連携できる機能を備えています。詳細は以下に記載されています。

https://wiki.internetcomputer.org/wiki/Bitcoin_Integration

https://internetcomputer.org/ethereum-integration

### 逆ガスモデル（Cycles）:

Ethereumなどで採用しているガス代の支払いモデルはユーザの負担だが、IC(Internet Computer)では開発者やサービス提供者が負担するモデルを採用している。ユーザにとって利用障壁が低くなっています。

### Network Nervous System

IC はNetwork Nervous System （NNS）というDAO（Decentralized Autonomous Organization）のガバナンスにより実現されています。NNSでの投票によってICが維持されています。


## ネットワーク構成

IC には複数のsubnet が存在し、subnet を追加することでスケーラビリティが実現されます。

subnet は複数データセンターを跨るノードで構成されるネットワークです。ノードの運用者はnode provider と呼ばれます。subnet は13 台から40 台のノードにより構成されます。

node provider は署名をすることで不正を働くと金銭的な損害を被るようなルールになっています。

[ICP DASHBOARD](https://dashboard.internetcomputer.org/) でsubnet数を確認できます。

https://internetcomputer.org/docs/current/developer-docs/getting-started/network-overview

### subnet の種類

[subnet の種類](https://internetcomputer.org/docs/current/references/subnets/subnet-types)には以下があります。

- application subnet
- system subnet
- fiduciary subnet
- European subnet

**application subnet**

application subnetは最も一般的なタイプのサブネットです。ほぼすべてのキャニスターはアプリケーション サブネット上で実行されます。

**system subnet**

ICの稼働を維持するために必要なサブネットのことです。NNS のシステムを稼働する際にも複数のsystem subnet が必要です。一般の開発者はsystem subnet へデプロイすることはできません。（cycles の支払いも発生しない）system subnet では呼び出しごとの命令制限や Web Assembly モジュールのサイズ制限がより寛容になっています。

**fiduciary subnet**

13 ノードより多いノードで構成されるサブネットです。13 ノードのサブネットで実行されるキャニスターと比較して、より多くのcycles が必要です。サイクル コストは、ノードの数に比例して増加します。fiduciary subnetは、13 ノードのサブネットが提供できるものよりもよりセキュリティレベルが高い必要がある DeFi アプリケーションをより安全に運用できるサービスを提供するために利用されます。

**European subnet**

European subnetは、ヨーロッパにあるノード マシンのみで構成されています。開発者は、GDPR に準拠したインフラストラクチャを必要とするアプリケーションを構築し、データ主権のニーズに合わせることができます。

## ICP のロードマップ

[ロードマップ](https://internetcomputer.org/roadmap)は 9 つのテーマに分かれています。

https://www.icp-japan.org/post/internet-computer-loadmap

https://internetcomputer.org/roadmap

- Compute Platform
    - レイテンシーの削減を行うことでUXを向上します。
- Decentralized AI
    - GPU ハードウェア アクセラレーションによるAIによる推論やデータセットのトレーニングが可能になる見込みです。
    - 現状、32 ビットのWasm メモリ4GiB の制限があるため、従来のLLMの実行が困難である。64 ビットのWasmではるかに大きなアドレスが指定可能なメモリを備えた Wasm64 に移行することで開発者はメイン メモリに大規模なモデルをロードできるようになります。
- Chain Fusion
    - Bitcoin、Ethereum、その他の主要なブロックチェーンとの直接的な相互運用性（インターオペラビリティ）を可能とします。
    - EVM RPC CanisterをリリースすることでICP のCanister から直接Ethereum と連携できるようにする。
    - Chain-Key ECDSA機能のレイテンシーとスループットの向上を目指します。
- Privacy
    - 検証可能な暗号化閾値鍵導出（vetKeysという）を導入することで、ICP上のユーザデータを暗号化して、暗号化されていないデータがブロックチェーンに記録されないようにする仕組みにします。
- Platform Decentralization
    - node provider がノードのHealth Checkを独立してトリアージし、問題が発生した場合に是正措置を講じることができるnode provider 用の監視ソリューションの提供を行います。
    - サブネットをレンタルし、サブネットのリソースを完全に制御できる仕組みを導入予定です。
- Identity
    - Internet Identity で検証可能な資格情報とアイデンティティ属性を導入することでアイデンティティ プロバイダーのビジネス モデルを構築します。
- Digital Assets
    - マルチチェーン カストディ ソリューション、ウォレットを構築することが可能です。認証にパスキーを使用し、シードフレーズやパスワードが不要でユーザフレンドリーでかつ安全性を確保できます。
- Governance & Tokenomics
    - リキッドデモクラシー(液体民主主義)「選挙権を他の専門知識がある人に託すことができる投票方式」と個別に投票する方式を導入し、ICPを稼働するための提案の決定方式をより分散化します。
- Developer Experience
    - サードパーティの機能を DFX に直接統合するためのプラグインを導入します。
    - より多くの改善されたチュートリアルにより、ICP エコシステムへの開発者のオンボーディングがより迅速に成功します。


## まとめ

インフラレイヤーからアプリケーション実行までをカバーし、これまでのweb3 の技術で課題となっているUXへの問題に取り組みユーザフレンドリーな体験を提供してくれることと思います。
活用例としても技術進歩とともにAI活用などにより面白いものがたくさん出てくることと思いますのでぜひ皆さんでICPを盛り上げていきましょう。

