---

copyright:
  years: 2015, 2021
lastupdated: "2021-02-12"

subcollection: natural-language-understanding

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:beta: .beta}
{:pre: .pre}
{:important: .important}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Analyzing text with advanced rules (Beta)
{: #advanced-rules}

The advanced rules feature is Beta. It is in a trial stage of development, and is not recommended for production use.
{: beta}

The {{site.data.keyword.knowledgestudioshort}} advanced rules workspace allows you to create text extractors with deeper customization potential than what is offered in other custom models. To get started, see [Creating an advanced rules model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-create-advanced-rules-model).

Advanced rules workspaces are available only in Knowledge Studio instances hosted in the Dallas or Frankfurt locations.
{: note}

## Uploading an advanced rules model
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
    "{url}/v1/models/advanced_rules?version={date}"
    ```

Use the `model_id` in the response to check the status of your model.

## Checking the status of advanced rules models
{: #checking-status-of-advanced-rules-models}

The following sample request for the **Get advanced rules model** method checks the status for the model with ID `e479adbb-8338-4d6d-973c-451548ccb08e`.

```bash
curl -X GET -u "apikey:{apikey}" \
"{url}/v1/models/advanced_rules/e479adbb-8338-4d6d-973c-451548ccb08e?version={date}"
```

To get information for all advanced rules models deployed to your instance, use the **List advanced rules models** method.

```bash
curl -X GET -u "apikey:{apikey}" \
"{url}/v1/models/advanced_rules?version={date}"
```

When the status is `available`, the model is ready to use.

## Analyzing text with advanced rules models
{: #analyzing-text-with-advanced-rules}

After you upload an advanced rules model and the status is `available`, you can use it with the **Analyze text** method.

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

- Example curl request:

    ```bash
    curl --user "apikey":"{apikey}" \
    "{url}/v1/analyze?version={date}" \
    --request POST \
    --header "Content-Type: application/json" \
    --data @parameters.json
    ```

## Analyzing HTML with advanced rules models
{: #analyzing-html-with-advanced-rules-model}

{{site.data.keyword.nlushort}} removes HTML tags that are sent in the `html` or `url` parameters to focus analysis on the text content. In cases where you want the HTML tags to be processed by advanced rules models, follow these steps.

1. When you export your model from {{site.data.keyword.knowledgestudioshort}}, select **Enable Detagging** before you press **OK**.
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

## Output format for advanced rules analysis
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

## Deleting an advanced rules model
{: #deleting-an-advanced-rules-model}

To delete an advanced rules model from your service instance, use the **Delete advanced rules model** method. Replace `{url}` and `{apikey}` with your service URL and API key, and replace `e479adbb-8338-4d6d-973c-451548ccb08e` with the model ID of the model you want to delete.

```bash
curl -X DELETE -u "apikey:{apikey}" \
"{url}/v1/models/advanced_rules/e479adbb-8338-4d6d-973c-451548ccb08e?version={date}"
```
  
