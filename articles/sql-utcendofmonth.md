---
title: "SQL　Server　での先月月初、先月末の日付取得" # 記事のタイトル
emoji: "👩‍💻" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech" # tech: 技術記事 / idea: アイデア記事
topics: ["sql","sqlserver","ssms"] # タグ。["markdown", "rust", "aws"]のように指定する
published: true # 公開設定（falseにすると下書き）
---

# SQL　Server　での先月月初、先月末の日付取得

SQL Server のタイムゾーンがUTCになっていると以下のように取得しても、JST になってしまう。

```
DECLARE @InputDate DATETIME = GETDATE();  
SELECT	DATEADD(dd, 1, EOMONTH (@InputDate , -2)),
	EOMONTH(@InputDate, -1)
```

```
2023-03-01	2023-03-31
```

9時間ずらしてあげることでUTCでの時刻が取れる。

```
DECLARE @InputDate DATETIME = GETDATE();  

SELECT	DATEADD(HOUR, -9, CONVERT(datetime, DATEADD(dd, 1, EOMONTH (@InputDate , -2)))),
	DATEADD(HOUR, -9, CONVERT(datetime, DATEADD(dd, 1, EOMONTH (@InputDate , -1))))
```

```
2023-02-28 15:00:00.000	2023-03-31 15:00:00.000
```
