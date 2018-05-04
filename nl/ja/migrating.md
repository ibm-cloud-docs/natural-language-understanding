---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-28"

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

# AlchemyLanguage からのマイグレーション

**2017 年 4 月 7 日**以降、AlchemyAPI の新規インスタンスを {{site.data.keyword.cloud}} で作成できなくなります。既存のサービス・インスタンスは **2018 年 3 月 7 日**までサポートされます。{{site.data.keyword.alchemylanguageshort}} フィーチャーの使用を続けるには、ご使用のコードを {{site.data.keyword.nlushort}} にマイグレーションすることが必要になります。
{: shortdesc}

{{site.data.keyword.nlushort}} には、より経済的な価格設定のモデルと、格段に使いやすい統合 API が用意されています。既存のフィーチャーは、お客様のニーズに合わせて、より便利で有益なものになるよう合理化されています。{{site.data.keyword.nlushort}} により、ブランドの管理、ビジネス・インテリジェンスの収集、マッチング、アドテック、レコメンデーションのためのクラスター化がより容易になります。

## 主な変更点の概要

- 新規 API 要求構文: 要求を `/analyze` エンドポイントに送信します。
- 新しい応答構造 ({{site.data.keyword.alchemylanguageshort}} 出力を解析するコードは {{site.data.keyword.nlushort}} 出力に対しては機能しません)。
- JSON が唯一の出力フォーマットです。
- *テキスト抽出*は `return_analyzed_text` パラメーターを `true` に設定することによって有効になります。
- *マイクロフォーマット*はサポートされません。
- *日付抽出*はサポートされません (*パブリケーション日付*は*メタデータ*機能で引き続きサポートされます)。
- エンティティーの「quotations」オプションはサポートされません。
- 「knowledgeGraph」は概念、キーワード、エンティティーのいずれでもサポートされません。
- ビジュアル制約照会 (`cquery` パラメーターで使用) はサポートされません。
- JSONP コールバックはサポートされません。
- {{site.data.keyword.alchemylanguageshort}} の *TypedRelations* は {{site.data.keyword.nlushort}} では *Relations* です。
- {{site.data.keyword.alchemylanguageshort}} の *Relations* は {{site.data.keyword.nlushort}} では *Semantic Roles* です。
- エンティティー・タイプが変更されました (新しいエンティティー・タイプについては[こちら](/docs/services/natural-language-understanding/entity-types.html)を参照)。
- 以下の語は AlchemyLanguage 分類法の結果ではつづりが誤っていました。これらは Natural Language Understanding カテゴリーの結果では修正されています。
  - `offence` -> `offense`
  - `civl` -> `civil`
  - `phyiscs` -> `physics`

## マイグレーション手順

1. {{site.data.keyword.nlushort}} サービスの[使用を開始](/docs/services/natural-language-understanding/getting-started.html)します。
1. Watson Knowledge Studio のカスタム・モデルを使用している場合は、それらを新しい {{site.data.keyword.nlushort}} サービス・インスタンスに再デプロイします。[ルール・ベース・アノテーター](/docs/services/knowledge-studio/rule-annotator-model-use.html#wks_rule_publish)または[機械学習アノテーター](/docs/services/knowledge-studio/publish-ml.html#wks_manlu)のデプロイ手順に従い、デプロイ対象として {{site.data.keyword.nlushort}} サービスを選択します。
1. ご使用のコードをマイグレーションします。{{site.data.keyword.alchemylanguageshort}} との対話に Watson Developer Cloud SDK を使用している場合は、ご使用の SDK コードを変更する必要があります。GitHub での {{site.data.keyword.nlushort}} SDK の例を見るには、以下のリンクをクリックしてください。
    - [Node.js ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/watson-developer-cloud/node-sdk#natural-language-understanding){: new_window}
    - [Python ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/watson-developer-cloud/python-sdk/blob/master/examples/natural_language_understanding_v1.py){: new_window}
    - [Swift ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://github.com/watson-developer-cloud/swift-sdk#natural-language-understanding){: new_window}

また、{{site.data.keyword.alchemylanguageshort}} 要求の出力を必要とするアプリケーション内のロジックを再構成する必要があります。{{site.data.keyword.nlushort}} の新しい出力構造を処理するように、ご使用のコードを必ず調整してください。

### AlchemyLanguage メソッドと対応する Natural Language Understanding フィーチャー
{{site.data.keyword.alchemylanguageshort}} は {{site.data.keyword.nlushort}} `/analyze` エンドポイントに対するマップを要求します。`/analyze` に対する要求は {{site.data.keyword.alchemylanguageshort}} からの Combined Call 要求に似ていますが、その構文は異なり、フィーチャーごとに `limit` のようなオプションを個々に指定できます。`/analyze` に対する POST は入力と要求のパラメーターを含む JSON 本体を受け入れ、`/analyze` に対する GET は JSON パラメーター構文に似た照会パラメーターを受け入れます。

| {{site.data.keyword.alchemylanguageshort}} メソッド| {{site.data.keyword.alchemylanguageshort}} エンドポイント| {{site.data.keyword.nlushort}} フィーチャー|
|------------------------|--------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Authors | `/text/TextGetAuthors`<br/>`/url/URLGetAuthors` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadata</a> |
| Concepts | `/html/HTMLGetRankedConcepts`<br/>`/text/TextGetRankedConcepts`<br/>`/url/URLGetRankedConcepts` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#concepts">Concepts</a> |
| Date Extraction | `/html/HTMLExtractDates`<br/>`/text/TextExtractDates`<br/>`/url/URLExtractDates` | サポートされていません |
| Emotion Analysis | `/html/HTMLGetEmotion`<br/>`/text/TextGetEmotion`<br/>`/url/URLGetEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">Emotion</a> |
| Targeted Emotion | `/html/HTMLGetTargetedEmotion`<br/>`/text/TextGetTargetedEmotion`<br/>`/url/URLGetTargetedEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">Emotion</a> (`targets` オプションを使用) |
| Entities | `/html/HTMLGetRankedNamedEntities`<br/>`/text/TextGetRankedNamedEntities`<br/>`/url/URLGetRankedNamedEntities` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#entities">Entities</a> |
| Feed Detection | `/html/HTMLGetFeedLinks`<br/>`/url/URLGetFeedLinks` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadata</a> |
| Keywords | `/html/HTMLGetRankedKeywords`<br/>`/text/TextGetRankedKeywords`<br/>`/url/URLGetRankedKeywords` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#keywords">Keywords</a> |
| Language Detection | `/html/HTMLGetLanguage`<br/>`/text/TextGetLanguage`<br/>`/url/URLGetLanguage` | 基本言語検出はすべての要求で無料です。ISO コード以外の言語メタデータは返されません。|
| Microformats | `/html/HTMLGetMicroformatData`<br/>`/url/URLGetMicroformatData` | サポートされていません |
| Publication Date | `/html/HTMLGetPubDate`<br/>`/url/URLGetPubDate` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadata</a> |
| Relations | `/html/HTMLGetRelations`<br/>`/text/TextGetRelations`<br/>`/url/URLGetRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#semantic-roles">Semantic Roles</a> |
| Typed Relations | `/html/HTMLGetTypedRelations`<br/>`/text/TextGetTypedRelations`<br/>`/url/URLGetTypedRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#relations">Relations</a> |
| Sentiment Analysis | `/html/HTMLGetTextSentiment`<br/>`/text/TextGetTextSentiment`<br/>`/url/URLGetTextSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">Sentiment</a> |
| Targeted Sentiment | `/html/HTMLGetTargetedSentiment`<br/>`/text/TextGetTargetedSentiment`<br/>`/url/URLGetTargetedSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">Sentiment</a> (`targets` オプションを使用) |
| 分類法 | `/html/HTMLGetRankedTaxonomy`<br/>`/text/TextGetRankedTaxonomy`<br/>`/url/URLGetRankedTaxonomy` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#categories">カテゴリー</a> |
| Text (cleaned) | `/html/HTMLGetText`<br/>`/url/URLGetText` | `/analyze` に対するすべての有効な要求で `return_analyzed_text` を `true` に設定|
| Text (raw) | `/html/HTMLGetRawText`<br/>`/url/URLGetRawText` | `/analyze` に対するすべての有効な要求で `return_analyzed_text` を `true` に、`clean` を `false` に設定|
| Title Extraction | `/html/HTMLGetTitle`<br/>`/url/URLGetTitle` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadata</a> |

そのため、次の結合呼び出しを行う場合、

```bash
curl -X POST \
-d "outputMode=json" \
-d "extract=entities,keywords" \
-d "sentiment=1" \
-d "limit=1" \
-d "url=https://www.ibm.com/us-en/" \
"https://gateway.watsonplatform.net/calls/url/URLGetCombinedData?apikey=$API_KEY"
```
{: pre}

{{site.data.keyword.nlushort}} では次のようになります。

```bash
curl -X POST \
-H "Content-Type: application/json" \
-u "{username}":"{password}" \
-d @parameters.json "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
```
{: pre}

以下の parameters.json を使用します。

```json
{
  "url": "https://www.ibm.com/us-en/",
  "features": {
    "entities": {
      "sentiment": true,
      "limit": 1
    },
    "keywords": {
      "sentiment": true,
      "limit": 1
    }
  }
}
```
{: codeblock}

## エンティティーの一致

{{site.data.keyword.alchemylanguageshort}} の TypedRelations メソッドの公開モデルを使用していた場合は、これらのモデルのエンティティー・タイプを必要とするコードをすべて変更する必要があります。下表に、TypedRelations エンティティー・タイプから {{site.data.keyword.nlushort}} エンティティー・タイプへのマッピングを示します。

| TypedRelations エンティティー・タイプ | {{site.data.keyword.nlushort}} Relations エンティティー・タイプ |
|----------------------------|------------------------------------------------------|
| AGE | Age |
| ANIMAL | Animal |
| AWARD | Award |
| CARDINAL | Cardinal |
| DATE | Date |
| DEGREE | Degree |
| DISEASE | HealthCondition |
| DURATION | Duration |
| EMAIL | EmailAddress |
| EVENT | Event |
| FACILITY | Facility |
| FOOD | Food |
| GEOLOGICALOBJ | GeographicFeature |
| GPE | GeopoliticalEntity |
| LAW | Law |
| LOCATION | Location |
| MEASURE | Measure |
| MONEY | Money |
| ORDINAL | Ordinal |
| ORGAN | Anatomy |
| ORGANIZATION | Organization |
| PEOPLE | Person |
| PERCENT | Percent |
| PERSONPEOPLE | Person |
| PERSON | Person |
| PHONE | Phone |
| PLANT | Plant |
| PRODUCT | Product |
| SUBSTANCE | Substance |
| TICKER | Ticker |
| TIME | Time |
| TITLEWORK | TitleWork |
| VEHICLE | Vehicle |
| WEAPON | Weapon |
| WEATHER | Weather |
| WEB | Web |
| EVENT_AWARD | Award |
| EVENT_BUSINESS | EventBusiness |
| EVENT_COMMUNICATION | EventCommunication |
| EVENT_CRIME | Crime |
| EVENT_CUSTODY | EventCustody |
| EVENT_DEMONSTRATION | EventDemonstration |
| EVENT_DISASTER | NaturalEvent |
| EVENT_EDUCATION | EventEducation |
| EVENT_ELECTION | EventElection |
| EVENT_LEGAL | EventLegal |
| EVENT_LEGISLATION | EventLegislation |
| EVENT_MEETING | EventMeeting |
| EVENT_GATHERING | EventGathering |
| EVENT_PERFORMANCE | EventPerformance |
| EVENT_PERSONNEL | EventPersonnel |
| EVENT_SPORTS | SportingEvent |
| EVENT_VIOLENCE | EventViolence |
| EVENT | Event |
