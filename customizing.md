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

# Customizing

With [{{site.data.keyword.knowledgestudiofull}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/watsonknowledgestudio), you can
extend {{site.data.keyword.nlushort}} with custom models that identify custom
entities and relations unique to your domain.
{: shortdesc}

The following example request uses a custom model trained with traffic incident reports. It detects custom relations like `impactPoint`, and custom entities like `MANUFACTURER`, `MODEL`, and `MODEL_YEAR` that are not available in the generic models for entities and relations. You can try this publicly available model in the live API with the model ID `en-us-tir`.

> *The public `en-us-tir` model is for demonstration purposes only, and is not intended for production use. The models you create with {{site.data.keyword.knowledgestudioshort}} are private and only visible to your organization.*

**Example request**

Example parameters.json file

```json
{
  "features": {
    "entities": {
      "model": "en-us-tir"
    },
    "relations": {
      "model": "en-us-tir"
    }
  },
  "text": "The vehicle rotated out from the initial wall impact and was subsequently struck by a 2013 BYD Qin pulling a single trailer"
}
```
{: codeblock}
Example curl request

```bash
curl -X POST \
-H "Content-Type: application/json" \
-u "{username}":"{password}" \
-d @parameters.json \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
```
{: pre}

**Output**

```json
{
  "relations": [
    {
      "type": "impactPoint",
      "sentence": "The vehicle rotated out from the initial wall impact and was subsequently struck by a 2013 BYD Qin pulling a single trailer",
      "score": 0.889433,
      "arguments": [
        {
          "text": "rotated out",
          "entities": [
            {
              "type": "IMPACT",
              "text": "rotated out"
            }
          ]
        },
        {
          "text": "vehicle",
          "entities": [
            {
              "type": "VEHICLE",
              "text": "vehicle"
            }
          ]
        }
      ]
    },
    {
      "type": "impactPoint",
      "sentence": "The vehicle rotated out from the initial wall impact and was subsequently struck by a 2013 BYD Qin pulling a single trailer",
      "score": 0.562738,
      "arguments": [
        {
          "text": "wall impact",
          "entities": [
            {
              "type": "IMPACT",
              "text": "wall impact"
            }
          ]
        },
        {
          "text": "vehicle",
          "entities": [
            {
              "type": "VEHICLE",
              "text": "vehicle"
            }
          ]
        }
      ]
    },
    {
      "type": "impactPoint",
      "sentence": "The vehicle rotated out from the initial wall impact and was subsequently struck by a 2013 BYD Qin pulling a single trailer",
      "score": 0.808518,
      "arguments": [
        {
          "text": "struck",
          "entities": [
            {
              "type": "IMPACT",
              "text": "struck"
            }
          ]
        },
        {
          "text": "Qin",
          "entities": [
            {
              "type": "MODEL",
              "text": "Qin"
            }
          ]
        }
      ]
    },
    {
      "type": "hasProperty",
      "sentence": "The vehicle rotated out from the initial wall impact and was subsequently struck by a 2013 BYD Qin pulling a single trailer",
      "score": 0.953107,
      "arguments": [
        {
          "text": "Qin",
          "entities": [
            {
              "type": "MODEL",
              "text": "Qin"
            }
          ]
        },
        {
          "text": "2013",
          "entities": [
            {
              "type": "MODEL_YEAR",
              "text": "2013"
            }
          ]
        }
      ]
    },
    {
      "type": "hasProperty",
      "sentence": "The vehicle rotated out from the initial wall impact and was subsequently struck by a 2013 BYD Qin pulling a single trailer",
      "score": 0.99409,
      "arguments": [
        {
          "text": "Qin",
          "entities": [
            {
              "type": "MODEL",
              "text": "Qin"
            }
          ]
        },
        {
          "text": "BYD",
          "entities": [
            {
              "type": "MANUFACTURER",
              "text": "BYD"
            }
          ]
        }
      ]
    }
  ],
  "entities": [
    {
      "type": "MANUFACTURER",
      "text": "BYD",
      "count": 1
    },
    {
      "type": "MODEL",
      "text": "Qin",
      "count": 1
    },
    {
      "type": "VEHICLE",
      "text": "vehicle",
      "count": 1
    },
    {
      "type": "IMPACT",
      "text": "wall impact",
      "count": 1
    },
    {
      "type": "VEHICLE",
      "text": "trailer",
      "count": 1
    },
    {
      "type": "IMPACT",
      "text": "rotated out",
      "count": 1
    },
    {
      "type": "IMPACT",
      "text": "struck",
      "count": 1
    },
    {
      "type": "MODEL_YEAR",
      "text": "2013",
      "count": 1
    }
  ],
  "language": "en"
}
```
{: codeblock}

## Getting started with custom models

> The {{site.data.keyword.nlushort}} Free plan limits the size and performance of your custom model. To test a custom model to its full extent, you will need to use it with the {{site.data.keyword.nlushort}} Standard plan.

1. If you haven't done so already, [get started](/docs/services/natural-language-understanding/getting-started.html) with {{site.data.keyword.nlushort}}.
1. [Get access to {{site.data.keyword.knowledgestudioshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top), and log in through the [online dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://gateway.watsonplatform.net/knowledge-studio/ui/dashboard/).
1. View the {{site.data.keyword.knowledgestudioshort}} [documentation](/docs/services/knowledge-studio/index.html) to learn how to create a custom model (annotator) and deploy it to {{site.data.keyword.nlushort}}.
1. To use your model, specify the `model` that you deployed in the
[entities ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#entities){: new_window} or
[relations ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#relations){: new_window} options of your API request:
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
        curl -X POST \
        -H "Content-Type: application/json" \
        -u "{username}":"{password}" \
        -d @parameters.json \
        "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
        ```
        {: pre}

