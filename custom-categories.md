---

copyright:
  years: 2015, 2021
lastupdated: "2021-02-18"

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

# Creating custom categories models (Beta)
{: #categories}

The custom categories feature is Beta. It is in a trial stage of development and is not recommended for production use.
{: beta}

Do not input any sensitive or personal information when you use the custom categories feature. The Beta release might not be compatible with legislation such as GDPR. For more information, see [Information security](/docs/natural-language-understanding?topic=natural-language-understanding-information-security).
{: important}

[Learn at-a-glance](https://github.com/watson-developer-cloud/doc-tutorial-downloads/blob/master/natural-language-understanding/Explainers/Custom%20Categories%20One%20Pager-2021.pdf) how the custom categories feature works, and best practices for training your model.
{: note}

The custom categories feature allows you to train custom English categories models with service instances deployed in the Dallas location. A custom categories model can be trained when no data is available; the only fields required for training categories models are `labels` and `key_phrases`.

## Creating categories training data
{: #create-categories-training-data}

### Categories training data requirements
{: #categories-training-data-requirements}

Create and train a custom categories model using the {{site.data.keyword.nlushort}} training API. You can also view an example [Python notebook](https://github.com/watson-developer-cloud/doc-tutorial-downloads/blob/master/natural-language-understanding/custom_categories_example.ipynb) that shows how to create and train a custom categories model.

  1. Training data must be JSON format, with `application/json` content type. Each training data file needs to contain a list of JSON objects, and each of these objects needs to have `labels` and `key_phrases` defined:

      - `labels`: These are the lists of category labels, in the order of their hierarchy. For example, if you want to add labels with a hierarchy where `B` is a child of `A`, the list of labels here would be:

        ```bash
        "labels": ["A", "B"]
        ```

      - `key_phrases`: These are lists of phrases that can uniquely identify the corresponding labels, for example:

        ```bash
        "key_phrases": ["films", "action movies"]
        ```

  2. Up to 5 levels of hierarchy are accepted in `labels`. Following is an example training data format:

      ```bash
        [
            {
                "labels": [
                    "level1"
                ],
                "key_phrases": [
                    "key phrase",
                    "key phrase 2"
                ]
            },
            {
                "labels": [
                    "level1",
                    "level2"
                ],
                "key_phrases": [
                    "key phrase 3",
                    "key phrase 4"
                ]
            }
        ]
      ```

## Training a custom categories model
{: #training-a-custom-categories-model}

When your training data is ready, use the **Create categories model** method to create your custom model. Make sure to substitute your credentials for `{apikey}` and `{url}`, and use the path to your training data file in the `training_data` parameter.

```bash
curl -X POST -u "apikey:{apikey}" \
-H "Content-Type: multipart/form-data" \
-F "name=MyCategoriesModel" \
-F "language=en" \
-F "model_version=1.0.1" \
-F "training_data=@categories_data.json;type=application/json" \
"{url}/v1/models/categories?version=2021-02-16"
```

Use the `model_id` in the response to check the status of your model.

## Checking the status of categories models
{: #checking-status-of-categories-models}

The following sample request for the **Get categories model** method checks the status for the model with ID `714a50d1-36c7-4a57-a790-99f13cc9301c`.

```bash
curl -X GET -u "apikey:{apikey}" \
"{url}/v1/models/categories/714a50d1-36c7-4a57-a790-99f13cc9301c?version=2021-02-16"
```

To get information for all categories models deployed to your instance, use the **List categories models** method.

```bash
curl -X GET -u "apikey:{apikey}" \
"{url}/v1/models/categories?version=2021-02-16"
```

When the status is `available`, the model is ready to use.

## Analyzing text with custom categories models
{: #analyzing-text-with-custom-categories-models}

To use your model, specify the `model` that you deployed in the [categories](https://{DomainName}/apidocs/natural-language-understanding#categories){: external} options of your API request:

- Example *parameters.json* file:

    ```json
    {
      "url": "www.url.example",
      "features": {
        "categories": {
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
    "{url}/v1/analyze?version=2021-02-16" \
    --data @parameters.json
    ```

## Deleting a custom categories model
{: #deleting-a-custom-categories-model}

To delete a categories model from your service instance, use the **Delete categories model** method. Replace {url} and {apikey} with your service URL and API key, and replace {model_id} with the model ID of the model you want to delete.

- The following example undeploys a categories model.

  ```bash
  curl --user "apikey":"{apikey}" \
  "{url}/v1/models/categories/{model_id}?version=2021-02-16" \
  --request DELETE
  ```
