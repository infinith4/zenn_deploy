---
title: "Local でDebug できなくなって、Unable to launch IIS Express となったとき" # 記事のタイトル
emoji: "🎉" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech" # tech: 技術記事 / idea: アイデア記事
topics: ["visual studio", "iss express"] # タグ。["markdown", "rust", "aws"]のように指定する
published: true # 公開設定（falseにすると下書き）
---

# Local でDebug できなくなって、Unable to launch IIS Express となったとき

applicationhost.config を変えれば良い。

```
[ProjectのPath]\.vs\SmartPrint\config\applicationhost.config
```

内のPort番号に対応する箇所の site の箇所を削除して、Project のPropertyでCreate Virtual Directoryとする

Reference:

https://urashita.com/archives/27177#IIS_Expressapplicationhostconfig
