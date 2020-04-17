---

copyright:
  years: 2015, 2020
lastupdated: "2020-04-17"

subcollection: natural-language-understanding

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:note: .note}
{:pre: .pre}
{:important: .important}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Customizing
{: #customizing}

With [{{site.data.keyword.knowledgestudiofull}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/knowledge-studio/), you can extend {{site.data.keyword.nlushort}} with custom models for supported feature and language combinations.
{: shortdesc}

## Before you begin
{: before-you-begin}

1. If you haven't done so already, [get started](/docs/natural-language-understanding?topic=natural-language-understanding-getting-started) with {{site.data.keyword.nlushort}}.
2. Check [Language support for custom models](#language-support-for-custom-models) to make sure that the custom model you want to create is supported.
3. Follow the customization instructions for one of the following features.
   - [Entities and relations](#entities-and-relations)
   - [Advanced rules (Beta)](#advanced-rules)
   - [Sentiment (Beta)](#custom-sentiment)

## Language support for custom models
{: #language-support-for-custom-models}

Check the *Custom model support* columns in the tables on the [Language support](/docs/natural-language-understanding?topic=natural-language-understanding-language-support) page to see the features that support custom models for each language.

### Targeted sentiment for custom model entities
{: #targeted-sentiment-for-custom-entities}

For English only, you can get sentiment scores for each custom model entity that is detected by the service by setting the `sentiment: true` option in the entities object. No other languages support targeted sentiment for custom model entities.

## Creating custom entities and relations models
{: #entities-and-relations}

> The {{site.data.keyword.nlushort}} Free plan limits the size and performance of your custom model. To test a custom model to its full extent, you will need to use it with the {{site.data.keyword.nlushort}} Standard plan.

2. [Get started with {{site.data.keyword.knowledgestudioshort}}](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#wks_tutintro).
3. Create a custom model.
   1. To create a custom entities and relations model, see [Creating a machine learning model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro) 
   2. You can also create a custom entities model with a rule-based model. See [Creating a rule-based model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutrule_intro) for details.
4. [Deploy your model to {{site.data.keyword.nlushort}}](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#wks_manlu)
5. To use your model, specify the `model` that you deployed in the
[entities ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/natural-language-understanding#entities){: new_window} or 
[relations ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/natural-language-understanding#relations){: new_window} options of your API request:
    - Example *parameters.json* file:

        ```json
        {
          "url": "www.url.example",
          "features": {
            "entities": {
              "model": "your-model-id-here"
            },
            "relations": {
              "model": "your-model-id-here"
            }
          }
        }
        ```
        {: codeblock}

    - Example curl request:

        ```bash
        curl --user "apikey":"{apikey}" \
        "{url}/v1/analyze?version=2019-07-12" \
        --request POST \
        --header "Content-Type: application/json" \
        --data @parameters.json
        ```
        {: pre}

## Deleting a custom model
{: #deleting-a-custom-model}

The number of custom models that you deploy to {{site.data.keyword.nlushort}} affects your {{site.data.keyword.nlushort}} bill according to your [pricing plan](https://www.ibm.com/cloud/watson-natural-language-understanding/pricing). To avoid charges for a model that you no longer use, [undeploy the model with {{site.data.keyword.knowledgestudioshort}}](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#undeploy-view-model), or undeploy the model with the delete model method for that feature. 

The following example undeploys an entities model.

```bash
curl --user "apikey":"{apikey}" \
"{url}/v1/models/{model_id}?version=2018-10-30" \
--request DELETE
```
{: pre}

## Creating custom sentiment models (Beta)
{: #custom-sentiment}

The custom sentiment feature is Beta. It is in a trial stage of development and is not recommended for production use.
{: note}

Users should not input any sensitive or personal information when using the custom sentiment feature. The Beta release may not be compatible with legislation such as GDPR. For more information, see [Information security](/docs/natural-language-understanding?topic=natural-language-understanding-information-security).
{: note}

The custom sentiment feature allows you to train custom English sentiment models with service instances deployed in the Dallas location. The custom models you create extend the base English sentiment model to create better results that reflect the training data that you provide.

### Creating sentiment training data
{: #creating-sentiment-training-data}

Before you create a model, prepare a CSV training data file that meets the [sentiment training data requirements](#sentiment-training-data-requirements). To view an example file, see [sentiment_data.csv](https://raw.githubusercontent.com/watson-developer-cloud/doc-tutorial-downloads/master/natural-language-understanding/sentiment_data.csv).

Each row of the CSV file contains a text sample under the `doc` column and a sentiment label under the `label` column. When you create your training data, try to include samples that resemble the phrases that you expect to encounter in your application.

#### Sentiment training data requirements
{: #sentiment-training-data-requirements}

- CSV file format
  - Must use `.csv` file extension and UTF-8 encoding
- Minimum number of samples: 20 (3,000 recommended)
- Maximum number of samples: 10,000
- Maximum file size: 10 MB
- Maximum file name length: 255 characters
- 2 columns with headers must be included
  - `doc` column containing sample text phrases
  - `label` column containing one of the following sentiment labels for each sample
    - `negative`
    - `neutral`
    - `positive`

### Training a custom sentiment model
{: #training-a-custom-sentiment-model}

When your training data is ready, use the **Create sentiment model** method to create your custom model. Make sure to substitute your credentials for `{apikey}` and `{url}`, and use the path to your training data file in the `training_data` parameter. 

```bash
curl -X POST -u "apikey:{apikey}" \
-H "Content-Type: multipart/form-data" \
-F "name=MySentimentModel" \
-F "language=en" \
-F "description=Test sentiment model" \
-F "version=1.0.1" \
-F "version_description=My version description" \
-F "training_data=@/Users/username/sentiment_data.csv;type=text/csv" \
"{url}/v1/models/sentiment?version=2019-07-12"
```
{: pre}

Use the `model_id` in the response to check the status of your model.

### Checking the status of sentiment models
{: #checking-status-of-sentiment-models}

The following sample request for the **Get sentiment model** method checks the status for the model with ID `714a50d1-36c7-4a57-a790-99f13cc9301c`.

```bash
curl -X GET -u "apikey:{apikey}" \
"{url}/v1/models/sentiment/714a50d1-36c7-4a57-a790-99f13cc9301c?version=2019-07-12"
```
{: pre}

To get information for all sentiment models deployed to your instance, use the **List sentiment models** method.

```bash
curl -X GET -u "apikey:{apikey}" \
"{url}/v1/models/sentiment?version=2019-07-12"
```
{: pre}

When the status is `available`, the model is ready to use.


### Analyzing text with custom sentiment models
{: #analyzing-text-with-custom-sentiment-models}

After you've trained a sentiment model and the status is `available`, you can use it with the **Analyze text** method.

- Example *parameters.json* file:

    ```json
    {
      "url": "www.ibm.com",
      "features": {
        "sentiment": {
          "model": "714a50d1-36c7-4a57-a790-99f13cc9301c"
        }
      }
    }
    ```
    {: codeblock}

- Example curl request:

    ```bash
    curl --user "apikey":"{apikey}" \
    "{url}/v1/analyze?version=2019-07-12" \
    --request POST \
    --header "Content-Type: application/json" \
    --data @parameters.json
    ```
    {: pre}

#### Analyzing entities and keywords for custom sentiment
{: #entities-and-keywords-custom-sentiment}

 The `model` sentiment option specifies the sentiment model to use for all sentiment operations in the request, including sentiment analysis for detected entities and keywords. The following example analyzes sentiment for entities and keywords with a custom model, and disables the default sentiment analysis of the whole document.

 - Example *parameters.json* file:

    ```json
    {
      "url": "www.ibm.com",
      "features": {
        "sentiment": {
          "model": "714a50d1-36c7-4a57-a790-99f13cc9301c",
          "document": false
        },
        "entities": {
          "sentiment": true
        },
        "keywords": {
          "sentiment": true
        }
      }
    }
    ```
    {: codeblock}

- Example curl request:

    ```bash
    curl --user "apikey":"{apikey}" \
    "{url}/v1/analyze?version=2019-07-12" \
    --request POST \
    --header "Content-Type: application/json" \
    --data @parameters.json
    ```
    {: pre}

## Analyzing text with advanced rules (Beta)
{: #advanced-rules}

The advanced rules feature is Beta. It is in a trial stage of development and is not recommended for production use.
{: note}

The {{site.data.keyword.knowledgestudioshort}} advanced rules workspace allows you to create text extractors with deeper customization potential than what is offered in other custom models. To get started, see [Creating an advanced rules model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-create-advanced-rules-model).

### Uploading an advanced rules model
{: #uploading-an-advanced-rules-model}

1. Export your model from the advanced rules editor. See step 6 in [Creating an advanced rules model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-create-advanced-rules-model#create-advanced-rules-model-procedure).
    - If you plan to analyze HTML and want to extract spans over the original HTML content, check the **Enable Detagging** box before you export your model.
2. Use the **Create advanced rules model** method to upload your model to {{site.data.keyword.nlushort}}. Replace `{url}` and `{apikey}` with your service URL and API key, and replace `/Users/username/revenue_by_division_en.zip` with the path to your model file.

    ```bash
    curl -X POST -u "apikey:{apikey}" \
    -H "Content-Type: multipart/form-data" \
    -F "name=MyAQLModel" \
    -F "language=en" \
    -F "description=Test AQL model" \
    -F "version=1.0.1" \
    -F "version_description=My version description" \
    -F "model=@/Users/username/revenue_by_division_en.zip;type=application/zip" \
    "{url}/v1/models/advanced_rules?version=2019-07-12"
    ```
    {: pre}

Use the `model_id` in the response to check the status of your model.

### Checking the status of advanced rules models
{: #checking-status-of-advanced-rules-models}

The following sample request for the **Get advanced rules model** method checks the status for the model with ID `e479adbb-8338-4d6d-973c-451548ccb08e`.

```bash
curl -X GET -u "apikey:{apikey}" \
"{url}/v1/models/advanced_rules/e479adbb-8338-4d6d-973c-451548ccb08e?version=2019-07-12"
```
{: pre}

To get information for all advanced rules models deployed to your instance, use the **List advanced rules models** method.

```bash
curl -X GET -u "apikey:{apikey}" \
"{url}/v1/models/advanced_rules?version=2019-07-12"
```
{: pre}

When the status is `available`, the model is ready to use.


### Analyzing text with advanced rules models
{: #analyzing-text-with-advanced-rules}

After you've uploaded an advanced rules model and the status is `available`, you can use it with the **Analyze text** method.

- Example *parameters.json* file:

    ```json
    {
      "text": "IBM Watson",
      "features": {
        "advanced_rules": {
          "model": "e479adbb-8338-4d6d-973c-451548ccb08e"
        }
      }
    }
    ```
    {: codeblock}

- Example curl request:

    ```bash
    curl --user "apikey":"{apikey}" \
    "{url}/v1/analyze?version=2019-07-12" \
    --request POST \
    --header "Content-Type: application/json" \
    --data @parameters.json
    ```
    {: pre}

### Analyzing HTML with advanced rules models
{: #analyzing-html-with-advanced-rules-model}

{{site.data.keyword.nlushort}} removes HTML tags that are sent in the `html` or `url` parameters to focus analysis on the text content. In cases where you want the HTML tags to be processed by advanced rules models, you need to do the following.

1. When exporting your model from {{site.data.keyword.knowledgestudioshort}}, select the **Enable Detagging** button before you press **OK**.
2. Pass HTML content in the `text` field so that the service does not remove HTML tags before analysis.

    - Example *parameters.json* file:

        ```json
        {
          "text": "<html><body>IBM Watson</body></html>",
          "features": {
            "advanced_rules": {
              "model": "e479adbb-8338-4d6d-973c-451548ccb08e"
            }
          }
        }
        ```
        {: codeblock}

### Deleting an advanced rules model
{: #deleting-an-advanced-rules-model}

To delete an advanced rules model from your service instance, use the **Delete advanced rules model** method. Replace `{url}` and `{apikey}` with your service URL and API key, and replace `e479adbb-8338-4d6d-973c-451548ccb08e` with the model ID of the model you want to delete.

```bash
curl -X DELETE -u "apikey:{apikey}" \
"{url}/v1/models/advanced_rules/e479adbb-8338-4d6d-973c-451548ccb08e?version=2019-07-12"
```
{: pre}

### Output format for advanced rules analysis
{: #advanced-rules-analysis-output}

The JSON output of an advanced rules analysis depends on the text extractor that you export from {{site.data.keyword.knowledgestudioshort}}.

- The response is a JSON object, where the keys are the names of the Annotation Query Language (AQL) output views.
- The tuples in an AQL view are represented as array of JSON objects, with one object for each tuple in the view.
- The keys in the JSON object are the names of the attributes in the view, while the values are the values of those attributes.

The following table describes how AQL data types are mapped to JSON.

| AQL Type | JSON Type | Example JSON |
| -------- | --------- | ----------- |
| `Integer` | `number` | `5` |
| `Float` | `number` | `4.13` |
| `Boolean` | `boolean` | `true` |
| `Text` | `string` | `"some string"` |
| `Span` | `object` of the form `{"text": String, "location": {"begin": Integer, "end": Integer}}` | `{ "text": "Jane", location": {"begin": 5, "end": 9} }`|
| Special case: `null` value | `null` | `null` |
| `List of Integer`| `array` of `number` | `[ 1, 2, 3, 4, 5]` |
| `List of Float`| `array` of `number` |  `[ 4.13, 4.5 ]` |
| `List of Boolean` | `array` of `boolean` |  `[ true, true, false]` |
| `List of Text` | `array` of `string` |  `[ "some string", "another string" ]` |
| `List of Span`  | `array` of `object` of the form `{"text":String, "location": {"begin": Integer, "end": Integer}}` | `[{ "text":"Jane", "location": {"begin": 5, "end": 9} }, { "text":"...", "location": {"begin": 15, "end": 40} }]` |
| Special case: empty `List` | `array` with 0 elements |  `[ ]` |
