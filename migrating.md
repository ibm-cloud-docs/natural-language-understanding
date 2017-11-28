---

copyright:
  years: 2015, 2017
lastupdated: "2017-07-21"

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

# Migrating from AlchemyLanguage

Starting on **April 7, 2017**, it will no longer be possible to create a new instance of AlchemyAPI on {{site.data.keyword.Bluemix}}. Existing service instances will be supported until **March 7, 2018**. To continue using {{site.data.keyword.alchemylanguageshort}} features, you will need to migrate your code to {{site.data.keyword.nlushort}}.
{: shortdesc}

{{site.data.keyword.nlushort}} offers a more economical pricing model and a consolidated API that is much easier to use. Existing features are streamlined to make them more useful and valuable for our customers needs. {{site.data.keyword.nlushort}} makes it easier to manage your brand, gather business intelligence, and cluster for matching, ad-tech, and recommendations.

## Overview of major changes

- New API request syntax: send requests to the `/analyze` endpoint
- New response structure (code that parses {{site.data.keyword.alchemylanguageshort}} output does not work for {{site.data.keyword.nlushort}} output)
- JSON is the only output format
- *Text extraction* is enabled by setting the `return_analyzed_text` parameter to `true`
- *Microformats* is not supported
- *Date extraction* is not supported (*Publication Date* is still supported in the *Metadata* feature)
- "quotations" options for entities are not supported
- "knowledgeGraph" is not supported for concepts, keywords, or entities
- Visual constraints queries (used with the `cquery` parameter) are not supported
- JSONP callbacks are not supported
- *TypedRelations* from {{site.data.keyword.alchemylanguageshort}} is *Relations* in {{site.data.keyword.nlushort}}
- *Relations* from {{site.data.keyword.alchemylanguageshort}} is *Semantic Roles* in {{site.data.keyword.nlushort}}
- Entity types have changed (see the new entity types [here](/docs/services/natural-language-understanding/entity-types.html))
- The following words were misspelled in AlchemyLanguage taxonomy results. They have been corrected in Natural Language Understanding categories results.
  - `offence` -> `offense`
  - `civl` -> `civil`
  - `phyiscs` -> `physics`

## Migration steps

1. [Get started](/docs/services/natural-language-understanding/getting-started.html) with the {{site.data.keyword.nlushort}} service.
1. If you use custom models from Watson Knowledge Studio, redeploy them to your new {{site.data.keyword.nlushort}} service instance. Follow the steps for deploying [rule-based annotators](/docs/services/knowledge-studio/rule-annotator-model-use.html#wks_rule_publish) or [machine-learning annotators](/docs/services/knowledge-studio/publish-ml.html#wks_manlu), and select the {{site.data.keyword.nlushort}} service as the target for deployment.
1. Migrate your code.
    If you use the Watson Developer Cloud SDKs to interact with {{site.data.keyword.alchemylanguageshort}}, you need to change your SDK code. Click the following links to view {{site.data.keyword.nlushort}} SDK examples in GitHub:
    - [Node.js ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-developer-cloud/node-sdk#natural-language-understanding){: new_window}
    - [Python ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-developer-cloud/python-sdk/blob/master/examples/natural_language_understanding_v1.py){: new_window}
    - [Swift ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/watson-developer-cloud/swift-sdk#natural-language-understanding){: new_window}

Additionally, you need to reconfigure any logic in your application that expects the output of {{site.data.keyword.alchemylanguageshort}} requests. Make sure that your code is adjusted to process the new output structure of {{site.data.keyword.nlushort}}.

### AlchemyLanguage methods and corresponding Natural Language Understanding features
{{site.data.keyword.alchemylanguageshort}} requests map to the {{site.data.keyword.nlushort}} `/analyze` endpoint. Requests to `/analyze` are similar to Combined Call requests from {{site.data.keyword.alchemylanguageshort}}, but the syntax is different and you are able to specify options like `limit` individually for each feature. POSTs to `/analyze` accept a JSON body that contains the input and the parameters for the request, and GETs to `/analyze` accept query parameters that are analogous to the JSON parameter syntax.

| {{site.data.keyword.alchemylanguageshort}} method | {{site.data.keyword.alchemylanguageshort}} endpoint | {{site.data.keyword.nlushort}} feature |
|------------------------|--------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Authors | `/text/TextGetAuthors`<br/>`/url/URLGetAuthors` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadata</a> |
| Concepts | `/html/HTMLGetRankedConcepts`<br/>`/text/TextGetRankedConcepts`<br/>`/url/URLGetRankedConcepts` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#concepts">Concepts</a> |
| Date Extraction | `/html/HTMLExtractDates`<br/>`/text/TextExtractDates`<br/>`/url/URLExtractDates` | Not supported |
| Emotion Analysis | `/html/HTMLGetEmotion`<br/>`/text/TextGetEmotion`<br/>`/url/URLGetEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">Emotion</a> |
| Targeted Emotion | `/html/HTMLGetTargetedEmotion`<br/>`/text/TextGetTargetedEmotion`<br/>`/url/URLGetTargetedEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">Emotion</a> (use the `targets` option) |
| Entities | `/html/HTMLGetRankedNamedEntities`<br/>`/text/TextGetRankedNamedEntities`<br/>`/url/URLGetRankedNamedEntities` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#entities">Entities</a> |
| Feed Detection | `/html/HTMLGetFeedLinks`<br/>`/url/URLGetFeedLinks` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadata</a> |
| Keywords | `/html/HTMLGetRankedKeywords`<br/>`/text/TextGetRankedKeywords`<br/>`/url/URLGetRankedKeywords` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#keywords">Keywords</a> |
| Language Detection | `/html/HTMLGetLanguage`<br/>`/text/TextGetLanguage`<br/>`/url/URLGetLanguage` | Basic language detection is free in every request. Language metadata other than the ISO code is not returned. |
| Microformats | `/html/HTMLGetMicroformatData`<br/>`/url/URLGetMicroformatData` | Not supported |
| Publication Date | `/html/HTMLGetPubDate`<br/>`/url/URLGetPubDate` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadata</a> |
| Relations | `/html/HTMLGetRelations`<br/>`/text/TextGetRelations`<br/>`/url/URLGetRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#semantic-roles">Semantic Roles</a> |
| Typed Relations | `/html/HTMLGetTypedRelations`<br/>`/text/TextGetTypedRelations`<br/>`/url/URLGetTypedRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#relations">Relations</a> |
| Sentiment Analysis | `/html/HTMLGetTextSentiment`<br/>`/text/TextGetTextSentiment`<br/>`/url/URLGetTextSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">Sentiment</a> |
| Targeted Sentiment | `/html/HTMLGetTargetedSentiment`<br/>`/text/TextGetTargetedSentiment`<br/>`/url/URLGetTargetedSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">Sentiment</a> (use the `targets` option) |
| Taxonomy | `/html/HTMLGetRankedTaxonomy`<br/>`/text/TextGetRankedTaxonomy`<br/>`/url/URLGetRankedTaxonomy` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#categories">Categories</a> |
| Text (cleaned) | `/html/HTMLGetText`<br/>`/url/URLGetText` | Set `return_analyzed_text` to `true` in any valid request to `/analyze` |
| Text (raw) | `/html/HTMLGetRawText`<br/>`/url/URLGetRawText` | Set `return_analyzed_text` to `true` and `clean` to `false` in any valid request to `/analyze` |
| Title Extraction | `/html/HTMLGetTitle`<br/>`/url/URLGetTitle` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadata</a> |

So, if you are making this combined call:

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

it would now look like this in {{site.data.keyword.nlushort}}:

```bash
curl -X POST \
-H "Content-Type: application/json" \
-u "{username}":"{password}" \
-d @parameters.json "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
```
{: pre}

With this parameters.json:

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

## Entity harmonization

If you were using the public models from {{site.data.keyword.alchemylanguageshort}}'s TypedRelations method, you will need to change any code that expects the entity types from those models. The following table shows the mapping of TypedRelations entity types to {{site.data.keyword.nlushort}} entity types.

| TypedRelations entity type | {{site.data.keyword.nlushort}} Relations entity type |
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
