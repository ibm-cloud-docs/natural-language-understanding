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

# Creating custom entities and relations models
{: #entities-and-relations}

The {{site.data.keyword.nlushort}} Free plan limits the size and performance of your custom model. To test a custom model to its full extent, use it with the {{site.data.keyword.nlushort}} Standard plan.
{: shortdesc}

1. [Get started with {{site.data.keyword.knowledgestudioshort}}](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#wks_tutintro).
1. Create a custom model.
    1. To create a custom entities and relations model, see [Creating a machine learning model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro)
    1. You can also create a custom entities model with a rule-based model. See [Creating a rule-based model](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutrule_intro) for details.
1. [Deploy your model to {{site.data.keyword.nlushort}}](/docs/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#wks_manlu)
1. To use your model, specify the `model` that you deployed in the [entities](https://{DomainName}/apidocs/natural-language-understanding#entities){: external} or [relations](https://{DomainName}/apidocs/natural-language-understanding#relations){: external} options of your API request:

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

    - Example curl request:

        ```bash
        curl --user "apikey":"{apikey}" \
        "{url}/v1/analyze?version={date}" \
        --request POST \
        --header "Content-Type: application/json" \
        --data @parameters.json
        ```

## Deleting custom entities and relations models
{: #deleting-a-custom-model}

To delete an entities or relations model from your service instance, use the **Delete model** method. Replace `{url}` and `{apikey}` with your service URL and API key, and replace `{model_id}` with the model ID of the model you want to delete.

- The following example undeploys an entities or relations model.

  ```bash
  curl --user "apikey":"{apikey}" "{url}/v1/models/{model_id}?version={date}"
  --request DELETE
  ```
