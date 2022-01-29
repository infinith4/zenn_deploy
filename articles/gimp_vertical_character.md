---
title: "GIMP でかっこいい縦書きにしたい" # 記事のタイトル
emoji: "😸" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech" # tech: 技術記事 / idea: アイデア記事
topics: [] # タグ。["markdown", "rust", "aws"]のように指定する
published: true # 公開設定（falseにすると下書き）
---

# GIMP でかっこいい縦書きにしたい

Google Docs で縦書きしたくても現状はできないので、
以下のようにできるが、微調整したいときやFontを大きくしたいときに変にスペースが空いたりして、細かな対応ができない。

http://hinata.la.coocan.jp/tool/tategaki.cgi

縦書きにするアプリもあるが、一部のフォントを大きくできないので、今のところ良い方法を見つけられていない。

GIMPを使って、縦書きする方法を考える。

縦書きするのでFontも行書体などにしたい。

https://fonts.google.com/

Japanese

https://fonts.google.com/?subset=japanese

1.GIMPを開く。
2.メニューバーから「編集」->「設定」をクリック
3.設定ダイアログの左メニューの「フォルダー」の中にある「フォント」をクリック
4.Pathがいくつかあるので適切なフォルダを開く
5.ダウンロードしたttfファイルを4の場所にコピー
6.GIMPを再起動する

Fontをできれば買いたくないし、サンプルだと小学生くらいまでに習う漢字しか適用されないので、空白になってしまう。


## 切り抜いて、サイズ変更したい

1.切り抜きを選択

![image](https://user-images.githubusercontent.com/43472251/150901863-797d8bb5-6112-4d7d-a179-3925b1cda4a3.png)

2.選択した範囲をクリックするかShift + Cを押すとできる。

Ref.

https://citrus-designs.com/gimp-cropping/

