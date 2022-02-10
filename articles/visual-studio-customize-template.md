---
title: "Visual Studio でテンプレートを変える方法" # 記事のタイトル
emoji: "😸" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech" # tech: 技術記事 / idea: アイデア記事
topics: ["visual studio"] # タグ。["markdown", "rust", "aws"]のように指定する
published: true # 公開設定（falseにすると下書き）
---

# Visual Studio 2019 でテンプレートを変える方法

https://qiita.com/KTA552/items/00358eeec6a3b2afb138

を参考にすればできる。

Template File(Zip)は以下にExport時に置かれる。

```
Documents\Visual Studio 2019\Templates\ItemTemplates
```

これを変えて、自分なりにカスタマイズしてVisual Studio 2019を再起動すればAdd Item したときに表示される。

# Visual Studio 2022 でテンプレートを変える方法

https://docs.microsoft.com/ja-jp/visualstudio/ide/how-to-locate-and-organize-project-and-item-templates?view=vs-2022

上記の方法でやったが2019と2022ではExportしたときのファイルが違うらしく上手く行かなかった。

英語版も確認したがPathが2019になっているので、多分間違い。

https://docs.microsoft.com/en-us/visualstudio/ide/how-to-locate-and-organize-project-and-item-templates?view=vs-2022

既存のTemplateは以下に保存されているようだった。それをUserTemplateにおいてみて表示はされたが、Idがそのままだから悪いのかわからないがCustomize したファイルがAddされず未解決。

```
%ProgramFiles%\Microsoft Visual Studio\2022\<edition>\Common7\IDE\ItemTemplates\
```
