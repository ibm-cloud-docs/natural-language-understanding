---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# リリース情報

本サービスに対する以下の新機能および変更点があります。
{: shortdesc}

## サービス API のバージョン管理

**現行 API バージョン**: 2018-03-16

API 要求には、`version=YYYY-MM-DD` という形式で日付を取得する version パラメーターが必要です。API 要求ごとに version パラメーターを送信します。

後方互換性のある方法で API を変更する場合、IBM は新規マイナー・バージョンをリリースします。新規バージョンでの変更を利用するには、version パラメーターの値を新しい日付に変更します。当該バージョンに更新する準備ができていない場合は、バージョン日付を変更しないでください。

## 変更内容

### 2018 年 3 月 16 日
{: #03-march-2018}

- ドイツ語のカテゴリー、関係、および意味役割のサポートが追加されました。
  - ドイツ語の関係には新しい関係タイプ・システムが使用されます。詳しくは、[『関係タイプ (バージョン 2)』](relations-v2.html)ページを参照してください。
- ドイツ語のキーワードと評判が向上しました。
- 日本語カテゴリーと概念のサポートが追加されました。
- 言語検出が向上しました。
- Web ページ・クリーニングが向上しました。
- フランス語とドイツ語のエンティティー・モデルが向上しました。これらのモデルは新しいエンティティー・タイプ・システムを使用します。[『エンティティーのタイプとサブタイプ (バージョン 2)』](entity-types-v2.html)ページで、新しいエンティティーのタイプとサブタイプを確認してください。アプリケーションに新しいタイプ・システムとの互換性がある場合は、新しいモデルを使用するように、要求内のバージョン日付パラメーターを `2018-03-16` に変更してください。_バージョン 1_ タイプ・システムと_バージョン 2_ タイプ・システムの違いは以下のとおりです。
  - 新しいエンティティー・タイプ:
    - Date 
    - Duration 
    - Measure 
    - Money 
    - Number&ast;
    - Percent&ast;
    - PhoneNumber&ast;
    - Ordinal 
    - Time 
    - URL&ast;
  - 削除されたエンティティー・タイプ:
    - Anatomy 
    - Award 
    - Broadcaster
    - Company
    - Crime 
    - Drug
    - HealthCondition
    - Movie
    - MusicGroup
    - NaturalEvent
    - PrintMedia
    - Quantity
    - Sport
    - SportingEvent
    - TelevisionShow
    - Vehicle
  - 新しいエンティティー・サブタイプ:
    - Quantity

&ast; このエンティティー・タイプはまだ、フランス語テキストでは検出可能ではありません。



### 2018 年 1 月 25 日
{: #25-january-2018}

- 中国語 (簡体字) [カスタム・モデル](customizing.html)・サポートがエンティティーと関係で使用できるようになりました。

### 2018 年 1 月 12 日
{: #12-january-2018}

- ドイツ語の概念のサポートが追加されました。

### 2017 年 12 月 15 日
{: #15-december-2017}

- オランダ語 [カスタム・モデル](customizing.html)・サポートがエンティティーと関係で使用できるようになりました。
- [フランス語の言語サポート](language-support.html#french)に概念が組み込まれました。
- フランス語の評判モデルが向上し、より良い結果が出されるようになりました。
- 言語検出モデルが高速化され、全体的により多くの言語が検出されるようになりました。言語の全リストについては、[『検出可能言語』](detectable-languages.html)を参照してください。

  以下の言語が新たにリストに加えられました。
  - ベラルーシ語 (be)
  - ビハール語 (bh)
  - ディベヒ語 (dv)
  - ガリシア語 (gl)
  - ガンダ語 (lg)
  - イヌクティトゥト語 (iu)
  - ジャワ語 (jv)
  - カンナダ語 (kn)
  - クメール語 (km)
  - キニヤルワンダ語 (rw)
  - ラオス語 (lo)
  - マラヤーラム語 (ml)
  - マラーティー語 (mr)
  - オリヤー語 (or)
  - パンジャブ語 (pa)
  - スコッチ・ゲール語 (gd)
  - シンハラ語 (si)
  - タミール語 (ta)
  - テルグ語 (te)
  - イディッシュ語 (yi)

  以下の言語は検出可能ではなくなりました。
  - ブルトン語 (br)
  - チャモロ語 (ch)
  - エスペラント語 (eo)
  - フェロー語 (fo)
  - ハウサ語 (ha)
  - ンデベレ語 (nr)
  - オジブワ語 (oj)

### 2017 年 11 月 28 日
{: #28-november-2017}

- **エンティティー言及。** オプション `"mentions": true` を追加することにより、`entities` 要求でエンティティー言及の場所を取得します。
    
    `POST /analyze` 要求本文の例:
    
    ```json
    {
      "text": "Intel planned to announce Monday a laptop-computer chip that combines an Intel processor and an AMD graphics unit.",
      "features": {
        "entities": {
          "mentions": true
        }
      }
    }
    ```
    {: codeblock}
    
    応答の例:
    
    ```json
    {
      "usage": {
        "text_units": 1,
        "text_characters": 114,
        "features": 1
      },
      "language": "en",
      "entities": [
        {
          "type": "Company",
          "text": "Intel",
          "relevance": 0.33,
          "mentions": [
            {
              "text": "Intel",
              "location": [
                0,
                5
              ]
            },
            {
              "text": "Intel",
              "location": [
                73,
                78
              ]
            }
          ],
          "disambiguation": {
            "subtype": [
              "OperatingSystemDeveloper",
              "ProcessorManufacturer",
              "SoftwareDeveloper"
            ],
            "name": "Intel",
            "dbpedia_resource": "http://dbpedia.org/resource/Intel"
          },
          "count": 2
        },
        {
          "type": "Company",
          "text": "AMD",
          "relevance": 0.33,
          "mentions": [
            {
              "text": "AMD",
              "location": [
                96,
                99
              ]
            }
          ],
          "disambiguation": {
            "subtype": [
              "ProcessorManufacturer"
            ],
            "name": "Advanced Micro Devices",
            "dbpedia_resource": "http://dbpedia.org/resource/Advanced_Micro_Devices"
          },
          "count": 1
        }
      ]
    }
    ```
    {: codeblock}
    
### 2017 年 11 月 17 日
{: #17-november-2017}

- **[韓国語言語サポート](language-support.html#korean)**が拡張され、以下の機能が加わりました。

    - エンティティー
    - キーワード
    - 意味役割


### 2017 年 7 月 30 日
{: #30-july-2017}

- オプションの `limit_text_characters` パラメーターを使用して処理対象の文字数を制限することにより、コストを制御することができます。以下に例を示します。

```
{
  "text": "The United States of America, commonly known as the United States (U.S.) or America, is a federal republic composed of 50 states, a federal district, five major self-governing territories, and various possessions. Forty-eight of the fifty states and the federal district are contiguous and located in North America between Canada and Mexico. The state of Alaska is in the northwest corner of North America, bordered by Canada to the east and across the Bering Strait from Russia to the west.",
  "features": {
    "entities": {}
  },
  "limit_text_characters": 50,
  "return_analyzed_text": true
}
```

- 文字が 1 バイト文字かマルチバイト文字かにかかわらず、各文字は 1 文字とカウントされます。

- 計量については、1 つの {{site.data.keyword.nlushort}} 項目は引き続き、1 テキスト単位あたり 1 つのフィーチャー (エンリッチメントとも呼ばれます) です。1 テキスト単位は 10,000 文字以下です。

- 価格設定情報について詳しくは、{{site.data.keyword.cloud}} カタログにある[「{{site.data.keyword.nlushort}}」](https://console.bluemix.net/catalog/services/natural-language-understanding)を参照してください。

- `limit_text_characters` パラメーターの追加のほかにも、テキスト・サイズ制限と切り捨てに対して以下の変更が行われました。

  - 50,000 文字を超えるテキストはすべて、処理前に切り捨てられます。以前には、切り捨てはキロバイト (1 キロバイトは 1024 バイト) に基づいて行われていました。

  - 50,000 文字を超えるテキストに対して切り捨てが行われると、応答で通知メッセージが返されます。

  - カスタム・モデルのテキスト制限サイズは、10,000 文字から 50,000 文字に上げられました。

  - 各要求で使用される {{site.data.keyword.nlushort}} 項目数を明確にするために、応答に使用状況情報が追加されました。以下に例を示します。

```
{
  "usage": {
    "text_units": 5,
    "text_characters": 41186,
    "features": 1
  },
  ...
}
```


### 2017 年 5 月 8 日
{: #8-may-2017}

- 感情トーン・スコア・モデルが更新されました。トレーニング・データ・セットが拡張され、フィーチャー・エンジニアリングが変更されました。その結果、ベンチマーク・データ・セットでのモデルの精度が高くなりました。

### 2017 年 3 月 27 日
{: #27-march-2017}

- エンティティーおよび評判のモデルが向上し、これらの機能の呼び出し時により良い結果が返されるようになりました。
- 関係で、フランス語、ドイツ語、イタリア語、およびポルトガル語の {{site.data.keyword.knowledgestudioshort}} カスタム・モデルがサポートされるようになりました。

### 2017 年 3 月 15 日
{: #15-march-2017}

感情トーン・スコア・モデルに対する更新がリリースされました。トレーニング・データ・セットが拡張された結果、ベンチマーク・データ・セットでのモデルの精度が高くなりました。

### 2017 年 2 月 27 日
{: #27-february-2017}

Natural Language Understanding サービスが GA になりました。

