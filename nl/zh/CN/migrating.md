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

# 从 AlchemyLanguage 迁移

自 **2017 年 4 月 7 日**开始，不能再在 {{site.data.keyword.cloud}} 上创建 AlchemyAPI 的新实例。对现有服务实例的支持将持续到 **2018 年 3 月 7 日**为止。要继续使用 {{site.data.keyword.alchemylanguageshort}} 功能，您需要将代码迁移到 {{site.data.keyword.nlushort}}。
{: shortdesc}

{{site.data.keyword.nlushort}} 提供了更经济的定价模型和使用起来容易得多的合并 API。现有功能经过简化，对于满足客户需求而言更有用、更有价值。通过 {{site.data.keyword.nlushort}}，可更轻松地管理品牌，收集商业情报以及对匹配项、广告技术和建议进行聚类。

## 主要更改概述

- 新的 API 请求语法：将请求发送到 `/analyze` 端点
- 新的响应结构（用于对 {{site.data.keyword.alchemylanguageshort}} 输出进行解析的代码不适用于 {{site.data.keyword.nlushort}} 输出）
- JSON 是唯一的输出格式
- *文本抽取*通过将 `return_analyzed_text` 参数设置为 `true` 来启用
- 不支持*微格式*
- 不支持*日期抽取*（*元数据*特征中仍支持*发布日期*）
- 不支持实体的“quotations”选项
- 概念、关键字或实体不支持“knowledgeGraph”
- 不支持可视约束查询（与 `cquery` 参数配合使用）
- 不支持 JSONP 回调
- {{site.data.keyword.alchemylanguageshort}} 中的 *TypedRelations* 是 {{site.data.keyword.nlushort}} 中的*关系*
- {{site.data.keyword.alchemylanguageshort}} 中的 *Relations* 是 {{site.data.keyword.nlushort}} 中的*语义角色*
- 实体类型已更改（在[此处](/docs/services/natural-language-understanding/entity-types.html)查看新的实体类型）
- 在 AlchemyLanguage 分类法结果中存在以下拼写错误的单词。这些单词已在 Natural Language Understanding 类别结果中进行了更正。
  - `offence` -> `offense`
  - `civl` -> `civil`
  - `phyiscs` -> `physics`

## 迁移步骤

1. {{site.data.keyword.nlushort}} 服务[入门](/docs/services/natural-language-understanding/getting-started.html)
1. 如果使用的是 Watson Knowledge Studio 中的定制模型，请将其重新部署到新的 {{site.data.keyword.nlushort}} 服务实例。执行用于部署[基于规则的注释器](/docs/services/knowledge-studio/rule-annotator-model-use.html#wks_rule_publish)或[机器学习注释器](/docs/services/knowledge-studio/publish-ml.html#wks_manlu)的步骤，然后选择 {{site.data.keyword.nlushort}} 服务作为部署的目标。
1. 迁移代码。
    如果使用 Watson Developer Cloud SDK 与 {{site.data.keyword.alchemylanguageshort}} 进行交互，那么需要更改 SDK 代码。单击以下链接以查看 GitHub 中的 {{site.data.keyword.nlushort}} SDK 示例：
    - [Node.js ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/watson-developer-cloud/node-sdk#natural-language-understanding){: new_window}
    - [Python ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/watson-developer-cloud/python-sdk/blob/master/examples/natural_language_understanding_v1.py){: new_window}
    - [Swift ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/watson-developer-cloud/swift-sdk#natural-language-understanding){: new_window}

此外，您需要重新配置应用程序中需要 {{site.data.keyword.alchemylanguageshort}} 请求的输出的任何逻辑。确保调整代码以处理 {{site.data.keyword.nlushort}} 的新输出结构。

### AlchemyLanguage 方法和对应的 Natural Language Understanding 特征
{{site.data.keyword.alchemylanguageshort}} 请求会映射到 {{site.data.keyword.nlushort}} `/analyze` 端点。对 `/analyze` 的请求与 {{site.data.keyword.alchemylanguageshort}} 中的“组合调用”请求类似，但语法不同，并且您能够分别为每个特征指定 `limit` 等选项。对 `/analyze` 执行的 POST 操作接受包含请求的输入和参数的 JSON 主体，对 `/analyze` 执行的 GET 操作接受与 JSON 参数语法类似的查询参数。

| {{site.data.keyword.alchemylanguageshort}} 方法| {{site.data.keyword.alchemylanguageshort}} 端点| {{site.data.keyword.nlushort}} 特征|
|------------------------|--------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| 作者| `/text/TextGetAuthors`<br/>`/url/URLGetAuthors`| <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">元数据</a>|
| 概念| `/html/HTMLGetRankedConcepts`<br/>`/text/TextGetRankedConcepts`<br/>`/url/URLGetRankedConcepts`| <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#concepts">概念</a>|
| 日期抽取| `/html/HTMLExtractDates`<br/>`/text/TextExtractDates`<br/>`/url/URLExtractDates`| 不支持|
| 情绪分析| `/html/HTMLGetEmotion`<br/>`/text/TextGetEmotion`<br/>`/url/URLGetEmotion`| <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">情绪</a>|
| 目标情绪| `/html/HTMLGetTargetedEmotion`<br/>`/text/TextGetTargetedEmotion`<br/>`/url/URLGetTargetedEmotion`| <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">情绪</a>（使用 `targets` 选项）|
| 实体| `/html/HTMLGetRankedNamedEntities`<br/>`/text/TextGetRankedNamedEntities`<br/>`/url/URLGetRankedNamedEntities`| <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#entities">实体</a>|
| 订阅源检测| `/html/HTMLGetFeedLinks`<br/>`/url/URLGetFeedLinks` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">元数据</a>|
| 关键字| `/html/HTMLGetRankedKeywords`<br/>`/text/TextGetRankedKeywords`<br/>`/url/URLGetRankedKeywords`| <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#keywords">关键字</a>|
| 语言检测| `/html/HTMLGetLanguage`<br/>`/text/TextGetLanguage`<br/>`/url/URLGetLanguage`| 在每个请求中都可免费使用基本语言检测。不会返回除 ISO 代码以外的其他语言元数据。|
| 微格式| `/html/HTMLGetMicroformatData`<br/>`/url/URLGetMicroformatData`| 不支持|
| 发布日期| `/html/HTMLGetPubDate`<br/>`/url/URLGetPubDate`| <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">元数据</a>|
| 关系| `/html/HTMLGetRelations`<br/>`/text/TextGetRelations`<br/>`/url/URLGetRelations`| <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#semantic-roles">语义角色</a>|
| 类型化关系| `/html/HTMLGetTypedRelations`<br/>`/text/TextGetTypedRelations`<br/>`/url/URLGetTypedRelations`| <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#relations">关系</a>|
| 观点分析| `/html/HTMLGetTextSentiment`<br/>`/text/TextGetTextSentiment`<br/>`/url/URLGetTextSentiment`| <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">观点</a>|
| 目标观点| `/html/HTMLGetTargetedSentiment`<br/>`/text/TextGetTargetedSentiment`<br/>`/url/URLGetTargetedSentiment`| <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">观点</a>（使用 `targets` 选项）|
| 分类法| `/html/HTMLGetRankedTaxonomy`<br/>`/text/TextGetRankedTaxonomy`<br/>`/url/URLGetRankedTaxonomy`| <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#categories">类别</a>|
| 文本（已清除）| `/html/HTMLGetText`<br/>`/url/URLGetText`| 在对 `/analyze` 的任何有效请求中，将 `return_analyzed_text` 设置为 `true`|
| 文本（原始）| `/html/HTMLGetRawText`<br/>`/url/URLGetRawText`| 在对 `/analyze` 的任何有效请求中，将 `return_analyzed_text` 设置为 `true`，并将 `clean` 设置为 `false`|
| 标题抽取| `/html/HTMLGetTitle`<br/>`/url/URLGetTitle`| <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">元数据</a>|

因此，如果要发出以下组合调用：

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

现在，在 {{site.data.keyword.nlushort}} 中此组合调用类似于以下内容：

```bash
curl -X POST \
-H "Content-Type: application/json" \
-u "{username}":"{password}" \
-d @parameters.json "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
```
{: pre}

parameters.json 如下：

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

## 实体协调

如果是通过 {{site.data.keyword.alchemylanguageshort}} 的 TypedRelations 方法使用公共模型，那么需要更改预期从这些模型中获取实体类型的任何代码。下表显示了 TypedRelations 实体类型到 {{site.data.keyword.nlushort}} 实体类型的映射。

| TypedRelations 实体类型| {{site.data.keyword.nlushort}} 关系实体类型|
|----------------------------|------------------------------------------------------|
| AGE| Age|
| ANIMAL| Animal|
| AWARD| Award|
| CARDINAL| Cardinal|
| DATE| Date|
| DEGREE| Degree|
| DISEASE| HealthCondition|
| DURATION| Duration|
| EMAIL| EmailAddress|
| EVENT| Event|
| FACILITY| Facility|
| FOOD| Food|
| GEOLOGICALOBJ| GeographicFeature|
| GPE| GeopoliticalEntity|
| LAW| Law|
| LOCATION| Location|
| MEASURE| Measure|
| MONEY| Money|
| ORDINAL| Ordinal|
| ORGAN| Anatomy|
| ORGANIZATION| Organization|
| PEOPLE| Person|
| PERCENT| Percent|
| PERSONPEOPLE| Person|
| PERSON| Person|
| PHONE| Phone|
| PLANT| Plant|
| PRODUCT| Product|
| SUBSTANCE| Substance|
| TICKER| Ticker|
| TIME| Time|
| TITLEWORK| TitleWork|
| VEHICLE| Vehicle|
| WEAPON| Weapon|
| WEATHER| Weather|
| WEB| Web|
| EVENT_AWARD| Award|
| EVENT_BUSINESS| EventBusiness|
| EVENT_COMMUNICATION| EventCommunication|
| EVENT_CRIME| Crime|
| EVENT_CUSTODY| EventCustody|
| EVENT_DEMONSTRATION| EventDemonstration|
| EVENT_DISASTER| NaturalEvent|
| EVENT_EDUCATION| EventEducation|
| EVENT_ELECTION| EventElection|
| EVENT_LEGAL| EventLegal|
| EVENT_LEGISLATION| EventLegislation|
| EVENT_MEETING| EventMeeting|
| EVENT_GATHERING| EventGathering|
| EVENT_PERFORMANCE| EventPerformance|
| EVENT_PERSONNEL| EventPersonnel|
| EVENT_SPORTS| SportingEvent|
| EVENT_VIOLENCE| EventViolence|
| EVENT| Event|
