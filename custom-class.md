---

copyright:
  years: 2015, 2021
lastupdated: "2021-04-26"

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

# Creating custom classification models (Beta)
{: #classifications}

The custom classification feature is Beta. It is in a trial stage of development and is not recommended for production use.
{: beta}

Do not input any sensitive or personal information when you use the custom classification feature. The Beta release might not be compatible with legislation such as GDPR. For more information, see [Information security](/docs/natural-language-understanding?topic=natural-language-understanding-information-security).
{: important}

The custom classifications feature allows you to train a multi-label text classifier using your own labeled data in the Dallas location. Once trained, the model will be automatically deployed in NLU and available for analyze calls.

## Creating classifications model training data
{: #create-classification-training-data}

Create and train a custom classifications model using the Natural Language Understanding training API. You can also use [this example Python notebook](https://github.com/watson-developer-cloud/doc-tutorial-downloads/blob/master/natural-language-understanding/custom_classifications_example.ipynb) that shows how to create and train a classifications model.

Classifications accepts training data in the following JSON format:

  ```bash
  [
    {
        "text": "Example 1",
        "labels": ["label1"]
    },
    {
        "text": "Example 2",
        "labels": ["label1", "label2"]
    }
  ]
  ```

### Classifications training data requirements
{: #classification-training-data-requirements}

- Classifications training data consists of an array containing multiple JSON objects.
- Each of these JSON objects, needs to contain, 1 `text` and 1 `labels` field.
- `text` consists of the training examples and `labels` consists of 1 or more labels associated with an example.
- `labels` are case-sensitive
- Minimum number of unique labels required: `2`
- Maximum number of unique labels allowed: `220`
- Minimum number of examples required per label: `5`
- Maximum size of each example (training and predict): `2000` [codepoints](https://en.wikipedia.org/wiki/Code_point)
- Maximum number of examples: `20000`

## Training a custom classifications model
{: #training-a-custom-classification}

When your training data is ready, use the **Create classifications model** method to create your custom classifications model. Make sure to substitute your credentials for `{apikey}` and `{url}`, and use the path to your training data file in the `training_data` parameter.

```bash
curl -X POST -u "apikey:{apikey}" \
-H "Content-Type: multipart/form-data" \
-F "name=MyClassificationsModel" \
-F "language=en" \
-F "model_version=1.0.1" \
-F "training_data=@classifications_data.json;type=application/json" \
"{url}/v1/models/classifications?version=2021-03-23"
```

Use the `model_id` in the response to check the status of your model.

## Checking the status of a classifications model
{: #checking-status-of-classifications}

The following sample request for the **Get classifications model** method checks the status for the classifications model with ID `cb3755ad-d226-4587-b956-43a4a7202202`.

```bash
curl -X GET -u "apikey:{apikey}" \
"{url}/v1/models/classifications/cb3755ad-d226-4587-b956-43a4a7202202?version=2021-03-23"
```

To get information for all classifications models deployed to your instance, use the **List classifications models** method.

```bash
curl -X GET -u "apikey:{apikey}" \
"{url}/v1/models/classifications?version=2021-03-23"
```

When the status is `available`, the classification is ready to use.

## Analyzing text with a custom classifications model
{: #analyzing-text-with-custom-classifications-models}

To use your classifications model, specify the `model` that you deployed in the [classifications](https://{DomainName}/apidocs/natural-language-understanding#classifications){: external} options of your API request:

- Example *parameters.json* file:

    ```json
    {
      "url": "www.url.example",
      "features": {
        "classifications": {
          "model": "your-model-id-here"
        }
      }
    }
    ```

- Example cURL request:

    ```bash
    curl --request POST \
    --header "Content-Type: application/json" \
    --user "apikey":"{apikey}" \
    "{url}/v1/analyze?version=2021-03-23" \
    --data @parameters.json
    ```

## Deleting a custom classifications model
{: #deleting-a-custom-classifications-model}

To delete a classifications model from your service instance, use the **Delete classifications model** method. Replace `{url}` and `{apikey}` with your service URL and API key, and replace `{model_id}` with the model ID of the classifications model you want to delete.

- The following example deletes a classification model.

  ```bash
  curl --user "apikey":"{apikey}" \
  "{url}/v1/models/classifications/{model_id}?version=2021-03-23" \
  --request DELETE
  ```
