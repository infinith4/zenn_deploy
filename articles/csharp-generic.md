---
title: "[C#] Generic 制約" # 記事のタイトル
emoji: "😭" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech" # tech: 技術記事 / idea: アイデア記事
topics: ["dotnet", "csharp", "C#"] # タグ。["markdown", "rust", "aws"]のように指定する
published: true # 公開設定（falseにすると下書き）
---

# [C#] Generic 制約

### new 制約

以下のようにかけるけど、Entity Class のConstructorに引数があるときはエラーになる。

```
public class Entity
{
    public Entity()
    {
    }
    
    //これはエラー
    //public Entity(Fuga fuga)
    //{
    //}
    
    public void Hoge()
    {
      return;
    }
}
public class MyClass<T> where T : new()
{
    public MyClass()
    {
        this.entity = new T();
    }
}

private void Main()
{
    var my = new MyClass<Entity>();
}
```

