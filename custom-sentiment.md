---

copyright:
  years: 2015, 2022
lastupdated: "2022-01-26"

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

# Creating custom sentiment models (Beta)
{: #custom-sentiment}

The custom sentiment feature is Beta. It is in a trial stage of development and is not recommended for production use.
{: beta}

Do not input any sensitive or personal information when you use the custom sentiment feature. The Beta release might not be compatible with legislation such as GDPR. For more information, see [Information security](/docs/natural-language-understanding?topic=natural-language-understanding-information-security).
{: note}

The custom sentiment feature allows you to train custom English sentiment models with service instances deployed in the Dallas location. The custom models that you create extend the base English sentiment model to create better results that reflect the training data that you provide.

## Creating sentiment training data
{: #creating-sentiment-training-data}

Before you create a model, prepare a CSV training data file that meets the [sentiment training data requirements](#sentiment-training-data-requirements). To view an example file, see [sentiment_data.csv](https://raw.githubusercontent.com/watson-developer-cloud/doc-tutorial-downloads/master/natural-language-understanding/sentiment_data.csv).

Each row of the CSV file contains a text sample under the `doc` column and a sentiment label under the `label` column. When you create your training data, try to include samples that resemble the phrases that you expect to find in your application.

### Sentiment training data requirements
{: #sentiment-training-data-requirements}

- CSV file format
  - Must use `.csv` file extension and UTF-8 encoding
- Minimum number of samples: 20 (3,000 recommended)
- Maximum number of samples: 10,000
- Maximum file size: 10 MB
- Maximum file name length: 255 characters
- Two columns with headers must be included
  - `doc` column that contains sample text phrases
  - `label` column that contains at least one sample for each one of the following sentiment labels:
        - `negative`
        - `neutral`
        - `positive`

## Training a custom sentiment model
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
"{url}/v1/models/sentiment?version={date}"
```

Use the `model_id` in the response to check the status of your model.

## Checking the status of sentiment models
{: #checking-status-of-sentiment-models}

The following sample request for the **Get sentiment model** method checks the status for the model with ID `714a50d1-36c7-4a57-a790-99f13cc9301c`.

```bash
curl -X GET -u "apikey:{apikey}" \
"{url}/v1/models/sentiment/714a50d1-36c7-4a57-a790-99f13cc9301c?version={date}"
```

To get information for all sentiment models deployed to your instance, use the **List sentiment models** method.

```bash
curl -X GET -u "apikey:{apikey}" \
"{url}/v1/models/sentiment?version={date}"
```

When the status is `available`, the model is ready to use.

## Analyzing text with custom sentiment models
{: #analyzing-text-with-custom-sentiment-models}

After you train a sentiment model and the status is `available`, you can use it with the **Analyze text** method.

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

- Example curl request:

    ```bash
    curl --user "apikey":"{apikey}" \
    "{url}/v1/analyze?version={date}" \
    --request POST \
    --header "Content-Type: application/json" \
    --data @parameters.json
    ```

### Analyzing entities and keywords for custom sentiment
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

- Example curl request:

    ```bash
    curl --user "apikey":"{apikey}" \
    "{url}/v1/analyze?version={date}" \
    --request POST \
    --header "Content-Type: application/json" \
    --data @parameters.json
    ```

## Deleting a custom sentiment model
{: #deleting-a-custom-sentiment-model}

To delete a sentiment model from your service instance, use the **Delete sentiment model** method. Replace {url} and {apikey} with your service URL and API key, and replace {model_id} with the model ID of the model you want to delete.

- The following example undeploys a sentiment model.

  ```bash
  curl --user "apikey":"{apikey}" \
  "{url}/v1/models/sentiment/{model_id}?version={date}" \
  --request DELETE
  ```
  
