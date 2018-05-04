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

# 從 AlchemyLanguage 移轉

從 **2017 年 4 月 7 日**開始，無法再於 {{site.data.keyword.cloud}} 上建立新的 AlchemyAPI 實例。在 **2018 年 3 月 7 日**之前，將會支援現有服務實例。若要繼續使用 {{site.data.keyword.alchemylanguageshort}} 特性，您需要將程式碼移轉至 {{site.data.keyword.nlushort}}。
{: shortdesc}

{{site.data.keyword.nlushort}} 提供更經濟的定價模型以及更容易使用的合併 API。現有特性已經過簡化，讓它們對我們的客戶需求而言更為實用且有價值。{{site.data.keyword.nlushort}} 可讓您更輕鬆地管理品牌、收集商業智慧，以及針對比對、ad-tech 和建議建立叢集。

## 主要變更概觀

- 新的 API 要求語法：將要求傳送至 `/analyze` 端點
- 新的回應結構（剖析 {{site.data.keyword.alchemylanguageshort}} 輸出的程式碼不適用於 {{site.data.keyword.nlushort}} 輸出）
- JSON 是唯一的輸出格式
- 將 `return_analyzed_text` 參數設為 `true`，以啟用*文字擷取*
- 不支援*微格式*
- 不支援*日期擷取*（*meta 資料* 特性仍然支援*發佈日期*）
- 不支援實體的 "quotations" 選項
- 概念、關鍵字或實體不支援 "knowledgeGraph"
- 不支援視覺化限制查詢（與 `cquery` 參數搭配使用）
- 不支援 JSONP 回呼
- {{site.data.keyword.alchemylanguageshort}} 中的 *TypedRelations* 是 {{site.data.keyword.nlushort}} 中的*關係*
- {{site.data.keyword.alchemylanguageshort}} 中的 *Relations* 是 {{site.data.keyword.nlushort}} 中的*語意角色*
- 實體類型已變更（請參閱[這裡](/docs/services/natural-language-understanding/entity-types.html)的新實體類型）
- 下列單字在 AlchemyLanguage 分類架構結果中拼錯。它們已在 Natural Language Understanding 種類結果中進行更正。
  - `offence` -> `offense`
  - `civl` -> `civil`
  - `phyiscs` -> `physics`

## 移轉步驟

1. [開始使用](/docs/services/natural-language-understanding/getting-started.html) {{site.data.keyword.nlushort}} 服務。
1. 如果您使用來自 Watson Knowledge Studio 的自訂模型，請將它們重新部署至新的 {{site.data.keyword.nlushort}} 服務實例。遵循[規則型註解程式](/docs/services/knowledge-studio/rule-annotator-model-use.html#wks_rule_publish)或[機器學習註解程式](/docs/services/knowledge-studio/publish-ml.html#wks_manlu)的部署步驟，然後選取 {{site.data.keyword.nlushort}} 服務作為部署的目標。
1. 移轉程式碼。
    如果您使用 Watson Developer Cloud SDK 以與 {{site.data.keyword.alchemylanguageshort}} 互動，則需要變更 SDK 程式碼。按下列鏈結，以檢視 GitHub 中的 {{site.data.keyword.nlushort}} SDK 範例：
    - [Node.js ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/watson-developer-cloud/node-sdk#natural-language-understanding){: new_window}
    - [Python ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/watson-developer-cloud/python-sdk/blob/master/examples/natural_language_understanding_v1.py){: new_window}
    - [Swift ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://github.com/watson-developer-cloud/swift-sdk#natural-language-understanding){: new_window}

此外，您還需要重新配置應用程式中預期 {{site.data.keyword.alchemylanguageshort}} 要求輸出的任何邏輯。請確定您的程式碼已調整為處理新的 {{site.data.keyword.nlushort}} 輸出結構。

### AlchemyLanguage 方法及對應的 Natural Language Understanding 特性
{{site.data.keyword.alchemylanguageshort}} 要求對映至 {{site.data.keyword.nlushort}} `/analyze` 端點。`/analyze` 的要求與 {{site.data.keyword.alchemylanguageshort}} 中的「結合呼叫」要求類似，但語法不同，而且您可以為每一個特性個別指定 `limit` 這類選項。POST 至 `/analyze` 接受包含要求輸入及參數的 JSON 內文，而 GET 至 `/analyze` 接受與 JSON 參數語法類似的查詢參數。

| {{site.data.keyword.alchemylanguageshort}} 方法   | {{site.data.keyword.alchemylanguageshort}} 端點     | {{site.data.keyword.nlushort}} 特性    |
|------------------------|--------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| 作者    | `/text/TextGetAuthors`<br/>`/url/URLGetAuthors` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">meta 資料</a> |
| 概念     | `/html/HTMLGetRankedConcepts`<br/>`/text/TextGetRankedConcepts`<br/>`/url/URLGetRankedConcepts` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#concepts">概念</a> |
| 日期擷取        | `/html/HTMLExtractDates`<br/>`/text/TextExtractDates`<br/>`/url/URLExtractDates` | 不支援|
| 情緒分析         | `/html/HTMLGetEmotion`<br/>`/text/TextGetEmotion`<br/>`/url/URLGetEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">情緒</a> |
| 目標情緒         | `/html/HTMLGetTargetedEmotion`<br/>`/text/TextGetTargetedEmotion`<br/>`/url/URLGetTargetedEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">情緒</a>（使用 `targets` 選項）|
| 實體     | `/html/HTMLGetRankedNamedEntities`<br/>`/text/TextGetRankedNamedEntities`<br/>`/url/URLGetRankedNamedEntities` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#entities">實體</a> |
| 資訊來源偵測   | `/html/HTMLGetFeedLinks`<br/>`/url/URLGetFeedLinks` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">meta 資料</a> |
| 關鍵字   | `/html/HTMLGetRankedKeywords`<br/>`/text/TextGetRankedKeywords`<br/>`/url/URLGetRankedKeywords` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#keywords">關鍵字</a> |
| 語言偵測           | `/html/HTMLGetLanguage`<br/>`/text/TextGetLanguage`<br/>`/url/URLGetLanguage` | 每個要求都可以免費使用基本語言偵測。不會傳回 ISO 代碼以外的語言 meta 資料。|
| 微格式       | `/html/HTMLGetMicroformatData`<br/>`/url/URLGetMicroformatData` | 不支援|
| 發佈日期         | `/html/HTMLGetPubDate`<br/>`/url/URLGetPubDate` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">meta 資料</a> |
| 關係      | `/html/HTMLGetRelations`<br/>`/text/TextGetRelations`<br/>`/url/URLGetRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#semantic-roles">語意角色</a> |
| 類型化關係      | `/html/HTMLGetTypedRelations`<br/>`/text/TextGetTypedRelations`<br/>`/url/URLGetTypedRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#relations">關係</a> |
| 觀感分析           | `/html/HTMLGetTextSentiment`<br/>`/text/TextGetTextSentiment`<br/>`/url/URLGetTextSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">觀感</a> |
| 目標觀感           | `/html/HTMLGetTargetedSentiment`<br/>`/text/TextGetTargetedSentiment`<br/>`/url/URLGetTargetedSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">觀感</a>（使用 `targets` 選項）|
| 分類架構 | `/html/HTMLGetRankedTaxonomy`<br/>`/text/TextGetRankedTaxonomy`<br/>`/url/URLGetRankedTaxonomy` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#categories">種類</a> |
| 文字（已清除）| `/html/HTMLGetText`<br/>`/url/URLGetText` | 在 `/analyze` 的任何有效要求中，將 `return_analyzed_text` 設為 `true` |
| 文字（原始）| `/html/HTMLGetRawText`<br/>`/url/URLGetRawText` | 在 `/analyze` 的任何有效要求中，將 `return_analyzed_text` 設為 `true`，並將 `clean` 設為 `false` |
| 標題擷取         | `/html/HTMLGetTitle`<br/>`/url/URLGetTitle` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">meta 資料</a> |

因此，如果您要進行這項結合呼叫，請執行下列指令：

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

現在，它在 {{site.data.keyword.nlushort}} 中看起來如下：

```bash
curl -X POST \
-H "Content-Type: application/json" \
-u "{username}":"{password}" \
-d @parameters.json "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
```
{: pre}

使用此 parameters.json：

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

## 實體調和

如果您是使用來自 {{site.data.keyword.alchemylanguageshort}} TypedRelations 方法的公用模型，則需要變更任何預期來自這些模型之實體類型的程式碼。下表顯示 TypedRelations 實體類型與 {{site.data.keyword.nlushort}} 實體類型的對映。

| TypedRelations 實體類型    | {{site.data.keyword.nlushort}} 關係實體類型          |
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
