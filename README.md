# EasyJsonParserSample

## UE4 Marketplace
[https://unrealengine.com/marketplace/ja/slug/easyjsonparser](https://unrealengine.com/marketplace/ja/slug/easyjsonparser)

## Description
Usage and sample of EasyJsonParser released in the market place of UE4.


[f:id:ayuma0913:20190615230834p:plain]



# 使い方
Json文字列 or Jsonファイルロードした後、アクセス文字列を指定して値の取得を行います。

[f:id:ayuma0913:20190615222610p:plain]


# アクセス文字列の指定
基本的には取得したい値までのパスをドットでつなげて指定します。

## シンプルなケース
以下のシンプルなJsonから"prop"の値をとる場合のアクセス文字列は`prop`になります。

```json
{
  "prop":"abc"
}
```


## オブジェクトの階層になっている場合
以下のように階層になっている場合は、ドットでつなげてアクセス文字列を作ります。

以下のケースでは`obj`というオブジェクトの中の`prop`プロパティを取りたいため、アクセス文字列は`obj.prop`になります。

```json
{
  "obj":
  {
    "prop":"abc"
  }
}
```

## 配列が含まれる場合
以下のように配列になっている場合は、何番目のものを取りたいかを指定します。

例えば2個目の`prop`を取りたい場合は、`obj[1].prop`となります。

1個目の`prop`を取りたい場合は、`obj[0].prop`となります。

```json
{
  "obj":[
  {
    "prop":"abc"
  },
  {
    "prop":"def"
  }
  ]
}
```

## 型を指定しての値の取得

Jsonから値を取得するために、次の4つの関数が用意されます。

[f:id:ayuma0913:20190615225443p:plain]

+ ReadInt(int)
+ ReadFloat(float)
+ ReadString(string)
+ ReadBool(bool)


「AccessString」にはアクセス文字列を入力します。

「DefaultValue」にはデフォルト値を入力します。指定された値がJsonに存在しない場合は、デフォルト値が返されます。

## オブジェクトの取得

値ではなくオブジェクトとして取得する "ReadObject"および "ReadObjects"メソッドもあります。

このメソッドで取得できるのはオブジェクトプロパティのみです。

ReadObjectは1つのノードオブジェクトを取得します。

ReadObjectsは複数のオブジェクトの配列を取得します。

以下のように、いったん階層途中のオブジェクトを取得してから、そのオブジェクトのプロパティを取得する使い方もできます。

[f:id:ayuma0913:20190615230219p:plain]

[f:id:ayuma0913:20190615230333p:plain]

# 今できることと今後やりたいこと
今回は`Jsonから値を取得する`という機能のみを、いかにシンプルに実装するかを考えて作成しました。

今はJsonはConfig値を設定ファイルに保存して利用したり、Web APIのデータのやりとりなど様々なところで使われていると思います。

このプラグインを使用すると、そのようなJsonからの値の取り出しをブループリントから楽にできるようになります。

今後の機能UPとしては以下のようなものを候補に考えています。
特に今は値の取得しかできないので、値の設定側もできるようになると幅が広がるのかなあと思っています。

+ マルチプラットフォーム対応
+ 値の設定

