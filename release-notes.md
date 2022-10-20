---

copyright:
  years: 2015, 2022
lastupdated: "2022-09-01"

subcollection: natural-language-understanding

content-type: release-note

---

{{site.data.keyword.attribute-definition-list}}

# Release notes for {{site.data.keyword.nlushort}}
{: #release-notes}

The following new features and changes to the service are available.
{: shortdesc}

## Service API versioning
{: #service-api-versioning}
{: release-note}

**Current API version**: 2022-08-10

API requests require a version parameter that takes the date in the format `version=YYYY-MM-DD`. Send the version parameter with every API request.

When we change the API in a backwards-incompatible way, we release a new minor version. To take advantage of the changes in a new version, change the value of the version parameter to the new date. If you're not ready to update to that version, don't change your version date.

### Active version dates
{: #active-version-dates}
{: release-note}

The following table shows the service behavior changes for each version date. Switching to a later version date will activate all changes introduced in earlier versions.

|Version date|Changes summary|
|---|---|
|[`2022-08-10`](#natural-language-understanding-aug1022)| <li>Language expansion of entities with a new model for improved accuracy and confidence scores.</li><li>Version 2 Russian entity type system.</li><li>Version 2 Swedish entity type system.</li>|
|[`2022-04-07`](#natural-language-understanding-apr0722)| <li>Bug fix for Version 2 Categories type system.</li>|
|[`2021-08-15`](#natural-language-understanding-aug1521)| <li>Classifications GA and Categories type system Version 2 features.</li>|
|[`2021-03-25`](#natural-language-understanding-mar2521)| <li>Custom categories (beta) and custom classifications (beta) features.</li>|
|[`2020-12-09`](#natural-language-understanding-dec0920)| <li>Version 2 English entity type system.</li>|
|[`2020-12-02`](#natural-language-understanding-dec0220)| <li>Version 2 Korean entity type system.</li><li>Version 2 Spanish entity type system.</li>|
|[`2020-08-01`](#natural-language-understanding-aug0120)| <li>Taxonomy changes aimed towards standardization of the label names in the default taxonomy.</li>|
|[`2019-07-12`](#natural-language-understanding-jul1219)| <li>New English entities model with improved accuracy and confidence scores.</li>|
|[`2019-06-04`](#natural-language-understanding-jun0419)| <li>Fixed a bug that caused entities requests with custom models to ignore the `limit` option.</li><li>The default `limit` value for all entities requests is now 50 for all models.</li><li>The maximum `limit` value of 250 entities has been removed.</li>|
|[`2018-11-16`](#natural-language-understanding-nov1618)| <li>Version 2 Italian entity type system.</li>|
|[`2018-09-21`](#natural-language-understanding-sep2118)| <li>Version 2 Portuguese entity type system.</li>|
|[`2018-03-16`](#natural-language-understanding-mar1618)| <li>Version 2 French entity type system.</li><li>Version 2 German entity type system.</li>|
|[`2017-02-27`](#natural-language-understanding-feb2717)| Base version.|

## 6 October 2022
{: #natural-language-understanding-oct0622}
{: release-note}

Improved Error Handling and Validation for Sentiment and Custom Sentiment
:   If a request contains both an error in the sentiment feature and a valid feature request for another feature, the response returns a 200 with a warning for the sentiment feature.
:   Requests for Custom Sentiment that include at least one target found in the document will now return a 200 with sentiment analysis for the found targets.

## 1 September 2022
{: #natural-language-understanding-sep0122}
{: release-note}

Improved Categories and Custom Categories (beta) Models
:   The model for [Categories](/docs/natural-language-understanding?topic=natural-language-understanding-categories-hierarchy) and [Custom Categories (beta)](/docs/natural-language-understanding?topic=natural-language-understanding-categories) now supports more contemporary vocabulary. For example, newer words such as "Covid-19" can be interpreted.

## 10 August 2022
{: #natural-language-understanding-aug1022}
{: release-note}

Entities support for additional languages
:   Support for entities is now available, for all public and premium service instances, for the following languages: Czech, Danish, Finnish, Hebrew, Hindi, Norwegian Bokmål, Norwegian Nynorsk, Polish, Romanian, Slovak, Turkish. For details, see [Language support](/docs/natural-language-understanding?topic=natural-language-understanding-language-support).

Version 2 entity support for Russian and Swedish
:   Version 2 entity type support is now available, for all public and premium service instances, for the following languages: Russian and Swedish. For details, see [Entity type systems](/docs/natural-language-understanding?topic=natural-language-understanding-entity-type-systems).

## 3 August 2022
{: #natural-language-understanding-aug0322}
{: release-note}

Support for Single Label Classifications
:   Classifications now allows users to pass in a `model_type` training parameter when creating or updating a model, in order to train a single label classifier. See [Classifications training parameters](/docs/natural-language-understanding?topic=natural-language-understanding-classifications#classification-training-parameters) for more details.

## 11 July 2022
{: #natural-language-understanding-jul1122}
{: release-note}

Improved [custom classifications](/docs/natural-language-understanding?topic=natural-language-understanding-classifications) model - Japanese
:   Japanese custom classifications models now train and perform inference faster, with improved model results.

Improved [custom categories](/docs/natural-language-understanding?topic=natural-language-understanding-categories) model
:   Model contains improved word filtering, resulting in better category determination.

## 7 April 2022
{: #natural-language-understanding-apr0722}
{: release-note}

Categories bug fix
:   Fixed a bug in the Version 2 Categories type system.

## 14 February 2022
{: #natural-language-understanding-feb1422}
{: release-note}

Emotion support
:   Support for emotion is now available, for all public service instances, for French. For details, see [Language support](/docs/natural-language-understanding?topic=natural-language-understanding-language-support).

Improved error handling and validation for emotion
:   If a request contains both an error in the emotion feature and a valid feature request for another feature, the response returns a 200 with a warning for the emotion feature.
:   The error log has changed from `emotion request must specify at least one of: document, targets` to `emotion request must specify at least one of: document or targets`.
:   Requests that include the emotion feature with any nonstring elements in the targets list returns an error.

## 1 December 2021
{: #natural-language-understanding-dec0121}
{: release-note}

Tone analytics
:   [Tone analytics](/docs/natural-language-understanding?topic=natural-language-understanding-tone_analytics) is now available, for English and French languages only. The tone analytics feature detects `excited`, `frustrated`, `impolite`, `polite`, `sad`, `satisfied`, and `sympathetic` tones from text.

## 12 October 2021
{: #natural-language-understanding-oct1221}
{: release-note}

Keyword and syntax support for additional languages
:   Support for keywords and syntax is now available, for all public and premium service instances, for the following languages: Hindi, Romanian, and Turkish. In addition, syntax is available for all supported languages. For details, see [Language support](/docs/natural-language-understanding?topic=natural-language-understanding-language-support).

## 15 August 2021
{: #natural-language-understanding-aug1521}
{: release-note}

Custom classification feature
:   The [custom classifications](/docs/natural-language-understanding?topic=natural-language-understanding-classifications) feature is now generally available (GA).

Categories stock model updated
:   The [categories stock model](/docs/natural-language-understanding?topic=natural-language-understanding-categories-hierarchy) has been updated to use the [IAB Tech Lab 2.0 taxonomy](https://iabtechlab.com/standards/content-taxonomy/).

## 5 May 2021
{: #natural-language-understanding-may0521}
{: release-note}

Advanced Rules beta feature deprecated
:   The advanced rules beta feature is deprecated. As of June 10, 2021, you will not be able to deploy advanced rules models to {{site.data.keyword.nlushort}}; existing models will keep running. After June 24, 2021, no advanced rules models will run in {{site.data.keyword.nlushort}}.

## 25 March 2021
{: #natural-language-understanding-mar2521}
{: release-note}

Custom classifications beta feature
:   The [custom classifications (Beta)](/docs/natural-language-understanding?topic=natural-language-understanding-classifications) feature allows you to train a multi-label text classifier (English-only) by using your own labeled data.

## 18 February 2021
{: #natural-language-understanding-feb1821}
{: release-note}

Custom categories beta feature
:   The [custom categories (Beta)](/docs/natural-language-understanding?topic=natural-language-understanding-categories) feature allows you to train custom categories models (English only) with service instances deployed in the Dallas location.

## December 2020
{: #natural-language-understanding-dec20}

### 9 December 2020
{: #natural-language-understanding-dec0920}
{: release-note}

Version 2 entity support for English
:   Version 2 entity type support is now available, for all public and premium service instances, for English language. For details, see [Entity type systems](/docs/natural-language-understanding?topic=natural-language-understanding-entity-type-systems).

### 2 December 2020
{: #natural-language-understanding-dec0220}
{: release-note}

Version 2 entity support for Korean and Spanish
:   Version 2 entity type support is now available, for all public and premium service instances, for the following languages: Korean and Spanish. For details, see [Entity type systems](/docs/natural-language-understanding?topic=natural-language-understanding-entity-type-systems).

## November 2020
{: #natural-language-understanding-nov20}

### 12 November 2020
{: #natural-language-understanding-nov1220}
{: release-note}

Entity support for Arabic, Chinese (Simplified), and Dutch
:   Support for entities is now available, for all public and premium service instances, for the following languages: Arabic, Chinese (Simplified) and Dutch. For details, see [Language support](/docs/natural-language-understanding?topic=natural-language-understanding-language-support).

:   Relevance ranking is not supported.
    {: note}

### 4 November 2020
{: #natural-language-understanding-nov0420}
{: release-note}

Keyword support for additional languages
:   Support for keywords is now available, for all public and premium service instances, for the following languages: Czech, Danish, Finnish, Hebrew, Norwegian, Norwegian-Bokmal, Norwegian-Nynorsk, Polish, and Slovak. For details, see [Language support](/docs/natural-language-understanding?topic=natural-language-understanding-language-support).

Improved keyword support for Russian and Swedish
:   The code that is used for keyword support for Russian and Swedish has been improved, so different, higher quality results are expected.

## September 2020
{: #natural-language-understanding-sep20}

### 25 September 2020
{: #natural-language-understanding-sep2520}
{: release-note}

`version` parameter deprecated
:   The `version` form parameter for model objects in the [API definition](https://cloud.ibm.com/apidocs/natural-language-understanding#createadvancedrulesmodel) has been deprecated; use the `model_version` parameter instead. The `model_version` parameter will override `version` whenever there is a conflict until April 9, 2021.

### 3 September 2020
{: #natural-language-understanding-sep0320}
{: release-note}

Summarization
:   [Summarization (Experimental)](/docs/natural-language-understanding?topic=natural-language-understanding-about#summarization) returns a summary of input source content. Summarization is currently available for English only.

Categories support for Dutch and Chinese
:   Support for Chinese and Dutch categories is now available, for all public and premium service instances. For details, see [Language support](/docs/natural-language-understanding?topic=natural-language-understanding-language-support).

## August 2020
{: #natural-language-understanding-aug20}

### 6 August 2020
{: #natural-language-understanding-aug0620}
{: release-note}

Syntax support
:   Syntax support is no longer "experimental", and is supported in all public and premium environments, for the following languages: English, Arabic, German, Spanish, French, Italian, Japanese, Korean, Dutch, Portuguese, and Chinese (Simplified). For details, see [Language support](/docs/natural-language-understanding?topic=natural-language-understanding-language-support).

### 1 August 2020
{: #natural-language-understanding-aug0120}
{: release-note}

Taxonomy changes
:   The following changes to the default taxonomy are activated when you use the version date `2020-08-01` or later:

|Previous entry|Updated entry|
|---|---|
|`/food and drink/health and lowfat cooking`|`/food and drink/health and low-fat cooking`|
|`/society/crime/sexual offence`|`/society/crime/sexual offense`|
|`/society/crime/sexual offence/paedophilia`|`/society/crime/sexual offense/pedophilia`|
|`/society/crime/sexual offence/prostitution`|`/society/crime/sexual offense/prostitution`|
|`/society/crime/sexual offence/rape`|`/society/crime/sexual offense/rape`|
|`/style and fashion/men 's fashion`|`/style and fashion/men's fashion`|
|`/technology and computing/consumer electronics/ebook reader`|`/technology and computing/consumer electronics/e-book reader`|

## 8 July 2020
{: #natural-language-understanding-jul0820}
{: release-note}

Arabic keyword support
:   Support for Arabic keywords is now available, for all public and premium service instances. For details, see [Language support](/docs/natural-language-understanding?topic=natural-language-understanding-language-support).

## 10 April 2020
{: #natural-language-understanding-apr1020}
{: release-note}

Custom Sentiment (Beta)
:   Custom Sentiment (Beta) is now available. The Beta supports English and is available only for service instances in the Dallas location. For details, see [Creating custom sentiment models](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing#custom-sentiment).

## March 2020
{: #natural-language-understanding-mar20}

### 20 March 2020
{: #natural-language-understanding-mar2020}
{: release-note}

Error response format change for advanced rules model endpoints (Beta)
:   Changed the error response format for advanced rules model endpoints (Beta) to be consistent with other endpoints.
- Renamed `status` to `code`.
- Renamed `message` to `error`.
  - Previous format:

    ```json
    {
        "status": 404,
        "message": "not found"
    }
    ```

  - New format:

    ```json
    {
        "code": 404,
        "error": "not found"
    }
    ```

### 11 March 2020
{: #natural-language-understanding-mar1120}
{: release-note}

Enhanced sentiment analysis for English
:   Enhanced English sentiment analysis to better identify and understand idioms in text.

## December 2019
{: #natural-language-understanding-dec19}

### 12 December 2019
{: #natural-language-understanding-dec1919}
{: release-note}

Full support for IBM Cloud IAM
:   {{site.data.keyword.nlushort}} now supports the full implementation of {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM). API keys for Watson services are no longer limited to a single service instance. You can create access policies and API keys that apply to more than one service, and you can grant access between services.

To support this change, the API service endpoints use a different domain and include the service instance ID. 

- The pattern is `api.{location}.{offering}.watson.cloud.ibm.com/instances/{instance_id}`.

- Example URL for an instance hosted in the Dallas location: `api.us-south.natural-language-understanding.watson.cloud.ibm.com/instances/6bbda3b3-d572-45e1-8c54-22d6ed9e52c2`

- The previous public endpoint domain was `watsonplatform.net`.

For more information about the URLs, see the [API reference](https://cloud.ibm.com/apidocs/natural-language-understanding/natural-language-understanding#service-endpoint){: external}.

These URLs do not introduce a breaking change. The new URLs work both for your existing service instances and for new instances. The original URLs continue to work on your existing service instances for at least one year (until December 2020).

For more information about IAM, see [Authenticating to Watson services](/docs/watson?topic=watson-iam).

New network and data security features
:   Support for data encryption with customer-managed keys
Users of new premium and dedicated instances can integrate {{site.data.keyword.keymanagementservicefull}} with {{site.data.keyword.nlushort}} to encrypt their data and manage encryption keys. For more information, see [Protecting sensitive information in your Watson service](/docs/watson?topic=watson-keyservice).

:   Support for private network endpoints
Users of Premium plans can create private network endpoints to connect to {{site.data.keyword.nlushort}} over a private network. Connections to private network endpoints do not require public internet access. For more information, see [Public and private network endpoints](/docs/watson?topic=watson-public-private-endpoints).

### 11 December 2019
{: #natural-language-understanding-dec1119}
{: release-note}

Custom categories (experimental) to be retired
:   The custom categories experimental feature will be retired on 19 December 2019. On that date, deployed custom categories models will no longer be accessible in {{site.data.keyword.nlushort}}. The feature will be removed from {{site.data.keyword.knowledgestudioshort}} on an earlier date. Custom categories models will no longer be accessible in {{site.data.keyword.knowledgestudioshort}} on 17 December 2019.

## November 2019
{: #natural-language-understanding-nov19}

### 25 November 2019
{: #natural-language-understanding-nov2519}
{: release-note}

Advanced rules (Beta)
:   Analyze text with custom advanced rules models that you create in {{site.data.keyword.knowledgestudiofull}}.

- [Get started with advanced rules models in {{site.data.keyword.knowledgestudioshort}}](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-create-advanced-rules-model)
- [Upload an advanced rules model to {{site.data.keyword.nlushort}}](https://cloud.ibm.com/docs/natural-language-understanding?topic=natural-language-understanding-customizing#advanced-rules)

### 13 November 2019
{: #natural-language-understanding-nov1319}
{: release-note}

New South Korea location
:   You can now create {{site.data.keyword.nlushort}} instances in the Seoul location. As with other locations, the {{site.data.keyword.cloud_notm}} Seoul location uses token-based Identity and Access Management (IAM) authentication.

## 10 October 2019
{: #natural-language-understanding-oct1019}
{: release-note}

Improved Sentiment response times
:   Improved response times for Japanese and Korean sentiment requests.

## September 2019
{: #natural-language-understanding-sep19}

### 17 September 2019
{: #natural-language-understanding-sep1719}
{: release-note}

Added Keyword and Sentiment support for Dutch and Chinese (Simplified)
:   Added support for Dutch keywords and sentiment. Added support for Chinese (Simplified) keywords and sentiment.

### 5 September 2019
{: #natural-language-understanding-sep0519}
{: release-note}

Improved Sentiment support for Spanish and Portuguese
:   Improved accuracy for Spanish and Portuguese sentiment. Improved response times for Portuguese sentiment requests.

## 29 August 2019
{: #natural-language-understanding-aug2919}
{: release-note}

Improved Sentiment support for English
:   Improved accuracy for English sentiment.

## 12 July 2019
{: #natural-language-understanding-jul1219}
{: release-note}

The following changes are activated when you use the version date `2019-07-12` or later.
:   New English entities model with improved accuracy.
:   Confidence scores are returned in English entities results.

## June 2019
{: #natural-language-understanding-jun19}

### 21 June 2019
{: #natural-language-understanding-jun2119}
{: release-note}

Confidence score returned for entities
:   Entity confidence score is now returned for entities requests that use custom machine learning models.

### 4 June 2019
{: #natural-language-understanding-jun0419}
{: release-note}

The following changes are activated when you use the version date `2019-06-04` or later.
:   Fixed a bug that caused entities requests with custom models to ignore the `limit` option.
:   The default `limit` value for all entities requests is now 50 for all models.
:   The maximum `limit` value of 250 entities has been removed.

## May 2019

### 29 May 2019
{: #natural-language-understanding-may2919}
{: release-note}

Sentiment improved for Spanish
:   Improved Spanish sentiment.

Bug fix for special characters
:   Fixed a bug that may have affected targeted sentiment results if the target contained special characters.

Service instance changes
:   The following changes are enabled for service instances in Washington DC, Tokyo, London, and Sydney:

- Sentiment option for entities requests that use custom models is enabled for all sentiment-supported languages except Arabic and Russian.

### 24 May 2019
{: #natural-language-understanding-may2419}
{: release-note}

Keywords improved for German
:   Improved German keywords.

Sentiment updates for English to locations
:   English sentiment updates released to service instances in all IBM Cloud locations other than Dallas.

### 3 May 2019
{: #natural-language-understanding-may0319}
{: release-note}

Sentiment detection for German improved
:   Improved German document-level sentiment detection.

## 25 April 2019
{: #natural-language-understanding-apr2519}
{: release-note}

Entity mentions for rule-based custom models
:   Enabled entity mentions for rule-based [custom models](/docs/natural-language-understanding?topic=natural-language-understanding-customizing). To view mentions in your results, set the `mentions` entities option to `true`.

Explanations for English categories results
:   Released explanations for English categories results. To see relevant text from the source that contributed to each result, set the `explanation` categories option to `true`.

## 19 March 2019
{: #natural-language-understanding-mar1919}
{: release-note}

Custom categories models created with {{site.data.keyword.knowledgestudioshort}}
:   Introduced experimental support for custom categories models created with {{site.data.keyword.knowledgestudioshort}}.

Keywords and concepts improved for Spanish
:   Improved Spanish keywords and concepts.

## 10 January 2019
{: #natural-language-understanding-jan1019}
{: release-note}

Requests with no version date parameter return error
:   `List models` and `Delete model` requests that don't include a version date parameter now return `400` errors instead of successful responses.

Entites performance improved
:   Improved entities performance for languages other than English.

## December 2018
{: #natural-language-understanding-dec18}

### 14 December 2018
{: #natural-language-understanding-dec1418}
{: release-note}

Support improvements
:   You can now create {{site.data.keyword.nlushort}} service instances in the IBM Cloud London location.
:   Added support for Portuguese relations.
:   Added support for Italian relations.
:   Added a `limit` parameter for categories requests that controls the number of categories returned up to a maximum of 10.
:   Improved accuracy for Japanese and German sentiment.

### 6 December 2018
{: #natural-language-understanding-dec0618}
{: release-note}

Improved accuracy for Italian
:   Improved accuracy for Italian categories, keywords, entities, and categories.

## November 2018
{: #natural-language-understanding-nov18}

### 27 November 2018
{: #natural-language-understanding-nov2718}
{: release-note}

Improvements and bug fixes
:   Improved quality of keywords results for English, French, Japanese, and Portuguese input.
:   Keywords with different capitalizations now appear in results as the same keyword.
:   The **Get models** method now returns additional fields that you can use to manage custom models across several deployments.
- `version`: user-provided version string from {{site.data.keyword.knowledgestudioshort}}
- `version_description`: user-provided description of this version from {{site.data.keyword.knowledgestudioshort}} (for example, what changed since the previous version)
- `workspace_id`: An ID provided by {{site.data.keyword.knowledgestudioshort}} that remains constant over repeated deployments from the same {{site.data.keyword.knowledgestudioshort}} workspace.
- `created`: A datetime string that indicates when the model was deployed to NLU.

### 16 November 2018
{: #natural-language-understanding-nov1618}
{: release-note}

New algorithm, improvements, and bug fixes
:   Released new algorithms for English keywords and sentiment to improve accuracy and performance.
:   Improved keywords accuracy and performance for English, French, Japanese, and Portuguese input.
:   Improved Italian sentiment accuracy and performance, including better accuracy for large text samples.
:   Fixed a bug that caused URL-encoded text to appear in Spanish entity disambiguation results.
:   Released a new Italian entities model with the latest entity type system. You can learn about the latest type system on the [Entity types and subtypes (Version 2)](/docs/natural-language-understanding?topic=natural-language-understanding-entity-types-version-2) page. When your application is compatible with the new type system, change the version date parameter in your requests to `2018-11-16` to use the new model.

### 9 November 2018
{: #natural-language-understanding-nov0918}
{: release-note}

Categories improvement
:   Major improvement in accuracy for Categories in all supported languages.

### 8 November 2018
{: #natural-language-understanding-nov0818}
{: release-note}

Service instances can be created in Tokyo location
:   You can now create {{site.data.keyword.nlushort}} service instances in the IBM Cloud Tokyo location.

### 5 November 2018
{: #natural-language-understanding-nov0518}
{: release-note}

Support for Concepts in Italian
:   Added support for Italian concepts.

## 30 October 2018
{: #natural-language-understanding-oct3018}
{: release-note}

IAM used for service instances
:   As of 30 October 2018, new service instances created in the Germany and US South regions use [Identity and Access Management (IAM) authentication](#iam-auth-process).

## 21 September 2018
{: #natural-language-understanding-sep2118}
{: release-note}

Language support improvements
:   Added support for French relations and Portuguese concepts.
:   The targeted sentiment option is now supported for French and Portuguese keywords.
:   Improved French keywords.
:   Improved Korean sentiment.
:   Improved Portuguese keywords and sentiment.
:   Released a new Portuguese entities model with the latest entity type system. You can learn about the latest type system on the [Entity types and subtypes (Version 2)](/docs/natural-language-understanding?topic=natural-language-understanding-entity-types-version-2) page. When your application is compatible with the new type system, change the version date parameter in your requests to `2018-09-21` to use the new model.

## June 2018
{: #natural-language-understanding-jun18}

### 26 June 2018
{: #natural-language-understanding-jun2618}
{: release-note}

Added support for Japanese entities and keywords.
:   For Japanese input, the following entities are not yet supported:

- Number
- Percent
- PhoneNumber
- URL

IPv6 addresses in Japanese input are not yet detectable as IPAddress entities.

### 12 June 2018
{: #natural-language-understanding-jun1218}
{: release-note}

IAM used for US East region
:   As of 12 June 2018, new service instances created in the US East region use [Identity and Access Management (IAM) authentication](#iam-auth-process).

### 6 June 2018
{: #natural-language-understanding-jun0618}
{: release-note}

Korean categories improvement
:   Minor improvements for Korean categories results.

## May 2018
{: #natural-language-understanding-may18}

### 29 May 2018
{: #natural-language-understanding-may2918}
{: release-note}

IAM used in Sydney region
:   As of 29 May 2018, new service instances created in the Sydney region use [Identity and Access Management (IAM) authentication](#iam-auth-process).

### 9 May 2018
{: #natural-language-understanding-may0918}
{: release-note}

German entities improvement
:   Improved German entities.

### 4 May 2018
{: #4natural-language-understanding-may0418}
{: release-note}

Bug fixes and performance improvements
:   Added support for Japanese sentiment and semantic roles.
:   Improved performance for metadata requests.
:   Fixed a bug that caused `NAN` relevance scores to appear in some entities results.
:   Fixed a bug that returned `400` error codes in German and Korean keywords requests when `500` error codes were more appropriate.

## April 2018
{: #natural-language-understanding-apr18}

### 19 April 2018
{: #natural-language-understanding-apr1918}
{: release-note}

Bug fixes and performance improvements
:   Added support for Japanese relations.
:   Improved German keywords.
:   Fixed a bug that caused incorrect entity mention text to be returned.
:   Fixed a bug that could cause poor results for targeted sentiment.
:   Fixed a bug that caused the returned `analyzed_text` to include characters that were not analyzed.

### 5 April 2018
{: #natural-language-understanding-apr0518}
{: release-note}

Webpage improvements
:   Improved webpage content fetching. If you use the `url` parameter to analyze webpages, you'll see better results, especially from webpages that use framesets and cookies.

Korean concept improvement
:   Minor improvements to Korean concepts.

## 16 March 2018
{: #natural-language-understanding-mar1618}
{: release-note}

Language support improvements
:   Added support for German categories, relations, and semantic roles.
:   A new relation type system is used for German relations. To view details, see the [Relation types (Version 2)](/docs/natural-language-understanding?topic=natural-language-understanding-relation-types-version-2) page.
:   Improved German keywords and sentiment.
:   Added support for Japanese categories and concepts.
:   Language detection improvements.
:   Improved webpage cleaning.
:   Improved French and German entities models. The models use a new entity type system. Check out the new entity types and subtypes on the [Entity types and subtypes (Version 2)](/docs/natural-language-understanding?topic=natural-language-understanding-entity-types-version-2) page. When your application is compatible with the new type system, change the version date parameter in your requests to `2018-03-16` to use the new model. The following are the differences between the _Version 1_ type system and the _Version 2_ type system.

- New entity types:
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
- Removed entity types:
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
- New entity subtype:
  - Quantity

&ast; This entity type is not yet detectable in French text.

## January 2018
{: #natural-language-understanding-jan18}

### 25 January 2018
{: #natural-language-understanding-jan2518}
{: release-note}

Custom model support for Chinese (Simplified)
:   Chinese (Simplified) [custom model](/docs/natural-language-understanding?topic=natural-language-understanding-customizing) support is now available for entities and relations.

### 12 January 2018
{: #natural-language-understanding-jan1218}
{: release-note}

Concepts support for German
:   Added support for German concepts.

## 15 December 2017
{: #natural-language-understanding-dec1517}
{: release-note}

Language support improvements
:   Dutch [custom model](/docs/natural-language-understanding?topic=natural-language-understanding-customizing) support is now available for entities and relations.
:   [French language support](/docs/natural-language-understanding?topic=natural-language-understanding-language-support#french) now includes concepts.
:   The French sentiment model has been improved to deliver better results.
:   The language detection model is faster and detects more languages overall. For the complete list of languages, see [Detectable languages](/docs/natural-language-understanding?topic=natural-language-understanding-detectable-languages).

- The following languages are new additions to the list:
  - Belarusian (be)
  - Bihari (bh)
  - Dhivehi (dv)
  - Galician (gl)
  - Ganda (lg)
  - Inuktitut (iu)
  - Javanese (jv)
  - Kannada (kn)
  - Khmer (km)
  - Kinyarwanda (rw)
  - Laothian (lo)
  - Malayalam (ml)
  - Marathi (mr)
  - Oriya (or)
  - Punjabi (pa)
  - Scots Gaelic (gd)
  - Sinhalese (si)
  - Tamil (ta)
  - Telugu (te)
  - Yiddish (yi)

- The following languages are no longer detectable:
  - Breton (br)
  - Chamorro (ch)
  - Esperanto (eo)
  - Faroese (fo)
  - Hausa (ha)
  - Ndebele (nr)
  - Ojibwa (oj)

## November 2017
{: #natural-language-understanding-nov17}

## 28 November 2017
{: #natural-language-understanding-nov2817}
{: release-note}

Entity mentions
:  Get the locations of entity mentions in your `entities` requests by adding the option `"mentions": true`.

- Example `POST /analyze` request body:

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

- Example response:

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

## 17 November 2017
{: #natural-language-understanding-nov1717}
{: release-note}

Korean language support improved
:   [Korean language support](/docs/natural-language-understanding?topic=natural-language-understanding-language-support#korean) has expanded to include the following features:

- Entities
- Keywords
- Semantic Roles

## 30 July 2017
{: #natural-language-understanding-jul3017}
{: release-note}

Limit number of characters processed
:   You can control cost by using the optional `limit_text_characters` parameter to limit the number of characters that are processed. For example,

```bash
{
  "text": "The United States of America, commonly known as the United States (U.S.) or America, is a federal republic composed of 50 states, a federal district, five major self-governing territories, and various possessions. Forty-eight of the fifty states and the federal district are contiguous and located in North America between Canada and Mexico. The state of Alaska is in the northwest corner of North America, bordered by Canada to the east and across the Bering Strait from Russia to the west.",
  "features": {
    "entities": {}
  },
  "limit_text_characters": 50,
  "return_analyzed_text": true
}
```

- Each character counts as one character, regardless of whether the character is a single-byte character or a multibyte character.

- For metering, one {{site.data.keyword.nlushort}} Item continues to be one feature (also known as an enrichment) per one text unit. One text unit is 10,000 characters or less.

- For detailed pricing information, see [{{site.data.keyword.nlushort}}](https://cloud.ibm.com/catalog/natural-language-understanding) in the {{site.data.keyword.cloud}} Catalog.

In addition to adding the `limit_text_characters` parameter, the following changes were made to text size limits and truncation:

- All text greater than 50,000 characters is truncated before processing. Previously, truncation was based on kilobytes, where one kilobyte equaled 1024 bytes.

- An informational message is returned in the response when text beyond 50,000 characters is truncated.

- Text limit size for custom models has increased from 10,000 characters to 50,000 characters.

- Usage information is added to the response for clarity around number of {{site.data.keyword.nlushort}} Items used for each request. For example,

```bash
{
  "usage": {
    "text_units": 5,
    "text_characters": 41186,
    "features": 1
  },
  ...
}
```

## 8 May 2017
{: #natural-language-understanding-may0817}
{: release-note}

Emotion tone score updates
:   Updated the emotion tone score model. The training data set was expanded and feature engineering was altered and as a result, the model has higher precision on the IBM benchmark data set.

## March 2017
{: #natural-language-understanding-mar17}

### 27 March 2017
{: #natural-language-understanding-mar2717}
{: release-note}

Model improvements
:   The entity and sentiment models have been improved, which means that when you call those features, you will get better results.
:   Relations now support {{site.data.keyword.knowledgestudioshort}} custom models in French, German, Italian, and Portuguese.

### 15 March 2017
{: #natural-language-understanding-mar1517}
{: release-note}

Emotion tone score updated
:   We released updates to the emotion tone score model. The training data set was expanded and as a result, the model has higher precision on the IBM benchmark data set.

## 27 February 2017
{: #natural-language-understanding-feb2717}
{: release-note}

Service GA
:   The Natural Language Understanding service is now GA.
