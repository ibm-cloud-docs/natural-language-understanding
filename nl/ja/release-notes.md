---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-25"

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
{: #release-notes}

本サービスに対する以下の新機能および変更点があります。
{: shortdesc}

## 新しい API 認証プロセス
{: #iam-auth-process }

2018 年 10 月 30 日に、ダラス (米国南部) およびフランクフルト (ドイツ) の各ロケーションが、トークン・ベースの ID およびアクセス管理 (IAM) 認証を使用するように移行されました (詳しくは、[IAM トークンを使用した認証![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/services/watson/getting-started-iam.html) を参照してください)。
{: important}

{{site.data.keyword.nlushort}} サービスは、次のロケーションでホストされるサービス・インスタンスの API 認証プロセスを刷新しました。

- ダラス (2018 年 10 月 30 日)
- フランクフルト (2018 年 10 月 30 日)
- ロンドン
- シドニー (2018 年 5 月 29 日)
- 東京
- ワシントン DC (2018 年 6 月 12 日)

{{site.data.keyword.cloud_notm}} は、トークン・ベースの ID およびアクセス管理 (IAM) 認証へのマイグレーションを進めています。一部のサービス・インスタンスでは、API に対する認証で IAM を使用します。

- 記載した日付以降にこれらのロケーションで作成した*新しい*サービス・インスタンスでは、API に対する認証に IAM を使用します。許可ヘッダーでベアラー・トークンを渡すか、または API キーを渡すことができます。トークンを使用すれば、認証済み要求がサポートされるので、呼び出すたびにサービス資格情報を埋め込む必要がありません。API キーは基本認証を使用します。IAM の詳細については、[こちら](/docs/services/watson/getting-started-iam.html)を参照してください。

Watson SDK を使用する場合は、API キーを渡して、SDK にトークンのライフサイクルを管理させることができます。詳細情報と例については、API リファレンスの[認証 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/apidocs/natural-language-understanding/#authentication){: new_window} を参照してください。
- 記載した日付より前に作成した_既存の_サービス・インスタンスでは、引き続きサービス・インスタンスのユーザー名とパスワードを渡して認証できます。最終的には、これらのサービス・インスタンスは IAM 認証にマイグレーションする必要があります。マイグレーションのプロセスと日付に関する新たな情報が提供される予定です。マイグレーションの詳細については、[リソース・グループへの Cloud Foundry サービス・インスタンスのマイグレーション](/docs/resources/instance_migration.html)を参照してください。

使用すべき認証を調べるには、[ダッシュボード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/dashboard/apps?watson){: new_window} でサービス・インスタンスをクリックしてサービス資格情報を参照します。


## サービス API のバージョン管理
{: #service-api-versioning}

**現在の API バージョン**: 2018-11-16

API 要求には、`version=YYYY-MM-DD` という形式で日付を取得する version パラメーターが必要です。 API 要求ごとに version パラメーターを送信します。

後方互換性のある方法で API を変更する場合、IBM は新規マイナー・バージョンをリリースします。 新規バージョンでの変更を利用するには、version パラメーターの値を新しい日付に変更します。 当該バージョンに更新する準備ができていない場合は、バージョン日付を変更しないでください。

## 変更内容
{: #changes}

### 2019 年 1 月 10 日
{: #10-january-2019}

- バージョン日付パラメーターが指定されていない **モデルのリスト**要求と **モデルの削除**要求では、成功の応答ではなく `400` エラーが返されるようになりました。
- 英語以外の言語でのエンティティーのパフォーマンスが向上しました。

### 2018 年 12 月 14 日
{: #14-december-2018}

- IBM Cloud のロンドン・ロケーションで {{site.data.keyword.nlushort}} サービス・インスタンスを作成できるようになりました。
- ポルトガル語の関係のサポートが追加されました。
- イタリア語の関係のサポートが追加されました。
- カテゴリー要求に、返されるカテゴリーの数 (最大 10 個) を制御する `limit` パラメーターが追加されました。
- 日本語とドイツ語の評判の精度が向上しました。

### 2018 年 12 月 6 日
{: #6-december-2018}

- イタリア語のカテゴリー、キーワード、エンティティーの精度が向上しました。

### 2018 年 11 月 27 日
{: #27-november-2018}

- 英語、フランス語、日本語、およびポルトガル語の入力に対するキーワードの結果の品質が向上しました。
- 大文字化が異なるキーワードが同一キーワードとして結果に表示されるようになりました。
- **モデルの取得** メソッドで、さまざまなデプロイメントでカスタム・モデルを管理するために使用できる追加のフィールドが返されるようになりました。
  - `version`: {{site.data.keyword.knowledgestudioshort}} のユーザー指定バージョン文字列
  - `version_description`: {{site.data.keyword.knowledgestudioshort}} でのこのバージョンに関するユーザー指定の説明 (以前のバージョンから変更された内容など)
  - `workspace_id`: {{site.data.keyword.knowledgestudioshort}} によって指定され、繰り返しデプロイしても {{site.data.keyword.knowledgestudioshort}} ワークスペースが同じであれば変わらない ID。
  - `created`: モデルが NLU にデプロイされた日時を示す日時文字列

### 2018 年 11 月 16 日
{: #16-november-2018}

- 精度とパフォーマンスの向上のため、英語のキーワードと評判の新しいアルゴリズムがリリースされました。
- 英語、日本語、およびポルトガル語の入力に対するキーワードの精度とパフォーマンスが向上しました。
- イタリア語の評判の精度とパフォーマンスが向上しました。この中で大きなテキスト・サンプルを使用した場合の精度が向上しています。
- スペイン語のエンティティーの明確化の結果に、URL エンコード・テキストが表示されるバグが修正されました。
- 最新のエンティティー・タイプ・システムを使用した新しいイタリア語のエンティティー・モデルがリリースされました。最新のタイプ・システムの詳細については、[エンティティーのタイプとサブタイプ (バージョン 2)](entity-types-v2.html)ページを参照してください。アプリケーションが新しいタイプ・システムに対応している場合は、新しいモデルを使用するように、要求内のバージョン日付パラメーターを `2018-11-16` に変更してください。

### 2018 年 11 月 9 日
{: #9-november-2018}

- サポートされているすべての言語でカテゴリーの精度が大幅に向上しました。

### 2018 年 11 月 8 日
{: #8-november-2018}

- IBM Cloud の東京ロケーションで {{site.data.keyword.nlushort}} サービス・インスタンスを作成できるようになりました。

### 2018 年 11 月 5 日
{: #5-november-2018}

- イタリア語の概念のサポートが追加されました。

### 2018 年 10 月 30 日	
{: #30-october-2018}	

2018 年 10 月 30 日より、ドイツと米国南部地域で作成される新しいサービス・インスタンスは [ID およびアクセス管理 (IAM) 認証](#iam-auth-process) を使用します。	

### 2018 年 9 月 21 日
{: #21-september-2018}

- フランス語の関係とポルトガル語の概念のサポートが追加されました。
- フランス語とポルトガル語のキーワードをターゲットにした評判オプションのサポートが追加されました。
- フランス語のキーワードが向上しました。
- 韓国語の評判が向上しました。
- ポルトガル語のキーワードと評判が向上しました。
- 最新のエンティティー・タイプ・システムを使用したポルトガル語の新しいエンティティー・モデルがリリースされました。最新のタイプ・システムの詳細については、[エンティティーのタイプとサブタイプ (バージョン 2)](entity-types-v2.html)ページを参照してください。アプリケーションが新しいタイプ・システムに対応している場合は、新しいモデルを使用するように、要求内のバージョン日付パラメーターを `2018-09-21` に変更してください。 

### 2018 年 6 月 26 日
{: #26-june-2018}

日本語のエンティティーとキーワードのサポートが追加されました。

- 日本語の入力では次のエンティティーはまだサポートされていません。
  - Number
  - Percent
  - PhoneNumber
  - URL
- 日本語の入力の IPv6 アドレスはまだ IPAddress エンティティーとして検出されません。

### 2018 年 6 月 12 日
{: #12-june-2018}

2018 年 6 月 12 日より、米国東部地域で作成される新しいサービス・インスタンスは [ID およびアクセス管理 (IAM) 認証](#iam-auth-process) を使用します。

### 2018 年 6 月 6 日
{: #06-june-2018}

- 韓国語のカテゴリーの結果がやや向上しました。

### 2018 年 5 月 29 日
{: #29-may-2018}

2018 年 5 月 29 日より、シドニー地域で作成される新しいサービス・インスタンスは [ID およびアクセス管理 (IAM) 認証](#iam-auth-process)を使用します。

### 2018 年 5 月 9 日
{: #9-may-2018}

- ドイツ語のエンティティーが向上しました。

### 2018 年 5 月 4 日
{: #4-may-2018}

- 日本語の評判と意味役割のサポートが追加されました。
- メタデータ要求のパフォーマンスが向上しました。
- `NAN` 関連性スコアが一部のエンティティー結果に表示されるバグが修正されました。
- ドイツ語と韓国語のキーワード要求で、`500` エラー・コードが適切である場合に `400` エラー・コードが返されるバグが修正されました。


### 2018 年 4 月 19 日
{: #19-april-2018}

- 日本語の関係のサポートが追加されました。
- ドイツ語のキーワードが向上しました。
- 正しくないエンティティー言及テキストが返されるバグが修正されました。
- ターゲットを設定した評判の結果として適切でない結果が返されるバグが修正されました。
- 分析されていない文字が `analyzed_text` に含めて返されるバグが修正されました。


### 2018 年 4 月 5 日
{: #05-april-2018}

- Web コンテンツ・フェッチが向上しました。`url` パラメーターを使用して Web ページを分析する場合の結果が向上しました。特にフレームセットと Cookie を使用する Web ページについて向上しました。
- 韓国語の概念がやや向上しました。

### 2018 年 3 月 16 日
{: #03-march-2018}

- ドイツ語のカテゴリー、関係、および意味役割のサポートが追加されました。
  - ドイツ語の関係には新しい関係タイプ・システムが使用されます。 詳しくは、[「関係タイプ (バージョン 2)」](relations-v2.html)ページを参照してください。
- ドイツ語のキーワードと評判が向上しました。
- 日本語カテゴリーと概念のサポートが追加されました。
- 言語検出が向上しました。
- Web ページ・クリーニングが向上しました。
- フランス語とドイツ語のエンティティー・モデルが向上しました。 これらのモデルは新しいエンティティー・タイプ・システムを使用します。 [「エンティティーのタイプとサブタイプ (バージョン 2)」](entity-types-v2.html)ページで、新しいエンティティーのタイプとサブタイプを確認してください。 アプリケーションが新しいタイプ・システムに対応している場合は、新しいモデルを使用するように、要求内のバージョン日付パラメーターを `2018-03-16` に変更してください。 _バージョン 1_ タイプ・システムと_バージョン 2_ タイプ・システムの違いは以下のとおりです。
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
- 言語検出モデルが高速化され、全体的により多くの言語が検出されるようになりました。 言語の全リストについては、[『検出可能言語』](detectable-languages.html)を参照してください。

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

- オプションの `limit_text_characters` パラメーターを使用して処理対象の文字数を制限することにより、コストを制御することができます。 以下に例を示します。

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

- 計量については、1 つの {{site.data.keyword.nlushort}} 項目は引き続き、1 テキスト単位あたり 1 つのフィーチャー (エンリッチメントとも呼ばれます) です。 1 テキスト単位は 10,000 文字以下です。

- 価格設定情報について詳しくは、{{site.data.keyword.cloud}} カタログにある[「{{site.data.keyword.nlushort}}」](https://console.bluemix.net/catalog/services/natural-language-understanding)を参照してください。

- `limit_text_characters` パラメーターの追加のほかにも、テキスト・サイズ制限と切り捨てに対して以下の変更が行われました。

  - 50,000 文字を超えるテキストはすべて、処理前に切り捨てられます。 以前には、切り捨てはキロバイト (1 キロバイトは 1024 バイト) に基づいて行われていました。

  - 50,000 文字を超えるテキストに対して切り捨てが行われると、応答で通知メッセージが返されます。

  - カスタム・モデルのテキスト制限サイズは、10,000 文字から 50,000 文字に上げられました。

  - 各要求で使用される {{site.data.keyword.nlushort}} 項目数を明確にするために、応答に使用状況情報が追加されました。 以下に例を示します。

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

- 感情トーン・スコア・モデルが更新されました。 トレーニング・データ・セットが拡張され、フィーチャー・エンジニアリングが変更されました。その結果、ベンチマーク・データ・セットでのモデルの精度が高くなりました。

### 2017 年 3 月 27 日
{: #27-march-2017}

- エンティティーおよび評判のモデルが向上し、これらのフィーチャーの呼び出し時により良い結果が返されるようになりました。
- 関係で、フランス語、ドイツ語、イタリア語、およびポルトガル語の {{site.data.keyword.knowledgestudioshort}} カスタム・モデルがサポートされるようになりました。

### 2017 年 3 月 15 日
{: #15-march-2017}

感情トーン・スコア・モデルに対する更新がリリースされました。 トレーニング・データ・セットが拡張された結果、ベンチマーク・データ・セットでのモデルの精度が高くなりました。

### 2017 年 2 月 27 日
{: #27-february-2017}

Natural Language Understanding サービスが一般出荷されました。
