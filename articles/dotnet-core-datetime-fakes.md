---
title: ".net core でSystem.DateTimeのFakeをしたい" # 記事のタイトル
emoji: "❄" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech" # tech: 技術記事 / idea: アイデア記事
topics: ["dotnet core", "fakes"] # タグ。["markdown", "rust", "aws"]のように指定する
published: true # 公開設定（falseにすると下書き）
---

# .net core でSystem.DateTimeのFakeをしたい

dotnet coreで System.DateTime をFakesしたいときは、System.Runtime をNugetでInstallして System.Runtime のFakeを追加すれば良い。


```
using System.Runtime.Fakes;
```

```
var testDateTime = new DateTime(2022, 2, 10, 23, 1, 1);

System.Fakes.ShimDateTime.NowGet = () => new DateTime(testDateTime.Year, testDateTime.Month, testDateTime.Day, testDateTime.Hour, testDateTime.Minute, testDateTime.Second);
```

