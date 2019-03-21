---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-20"

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

# Customizing
{: #customizing}

With [{{site.data.keyword.knowledgestudiofull}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/watsonknowledgestudio), you can
extend {{site.data.keyword.nlushort}} with custom models that identify custom
entities, relations, and categories unique to your domain.
{: shortdesc}

## Getting started with custom models
{: #getting-started-with-custom-models}

> The {{site.data.keyword.nlushort}} Free plan limits the size and performance of your custom model. To test a custom model to its full extent, you will need to use it with the {{site.data.keyword.nlushort}} Standard plan.

1. If you haven't done so already, [get started](/docs/services/natural-language-understanding?topic=natural-language-understanding-getting-started) with {{site.data.keyword.nlushort}}.
2. [Get started with {{site.data.keyword.knowledgestudioshort}}](https://cloud.ibm.com/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#wks_tutintro).
3. Create a custom model.
   1. To create a custom entities and relations model, see [Creating a machine learning model](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro) 
   2. You can also create a custom entities model with a rule based model. See [Creating a rule based model](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro) for details.
   3. To create a custom categories model, see [Creating a custom categories model](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-create-categories-model).
4. [Deploy your model to {{site.data.keyword.nlushort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#wks_manlu)
5. To use your model, specify the `model` that you deployed in the
[entities ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/natural-language-understanding#entities){: new_window},
[relations ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/natural-language-understanding#relations){: new_window}, or [categories ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/natural-language-understanding#categories){: new_window} options of your API request:
    - Example *parameters.json* file:

        ```json
        {
          "url": "www.url.example",
          "features": {
            "categories": {
              "model": "your-model-id-here"
            },
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
        "{url}/v1/analyze?version=2018-11-16" \
        --request POST \
        --header "Content-Type: application/json" \
        --data @parameters.json
        ```
        {: pre}

## Deleting a custom model
{: #deleting-a-custom-model}

The number of custom models that you deploy to {{site.data.keyword.nlushort}} affects your {{site.data.keyword.nlushort}} bill according to your [pricing plan](https://www.ibm.com/cloud/watson-natural-language-understanding/pricing). To avoid charges for a model that you no longer use, [undeploy the model with {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#undeploy-view-model), or undeploy the model with the **[Delete model](https://{DomainName}/apidocs/natural-language-understanding#delete-model)** method.

Example curl request:

```bash
curl --user "apikey":"{apikey}" \
"{url}/v1/models/{model_id}?version=2018-10-30" \
--request DELETE
```
{: pre}


## Language support for custom models
{: #language-support-for-custom-models}

Check the *Custom model support* columns in the tables on the [Language support](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support) page to see the custom models that are supported for each language.

### Targeted sentiment for custom model entities
{: #targeted-sentiment-for-custom-entities}

For English only, you can get sentiment scores for each custom model entity that is detected by the service by setting the `sentiment: true` option in the entities object. No other languages support targeted sentiment for custom model entities.
