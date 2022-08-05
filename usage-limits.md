---

copyright:
  years: 2015, 2022
lastupdated: "2022-08-05"

subcollection: natural-language-understanding

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

# Usage limits
{: #usage-limits}

The following usage limits and restrictions apply to {{site.data.keyword.nlushort}} service instances.
{: shortdesc}

## Analyzed text limit
{: #analyzed-text}

{{site.data.keyword.nlushort}} truncates analyzed text that contains more than 50,000 single-byte or multibyte characters. To view the text that counts toward this limit in your requests, set the `return_analyzed_text` parameter to `true`.

You can set a smaller character limit with the `limit_text_characters` parameter. If you are interested in analyzing only a small portion of your content, this can help you avoid excessive costs.

Example parameters object:
```json
{
  "url": "ibm.com",
  "limit_text_characters": 10000,
  "return_analyzed_text": true,
  "features": {
    "concepts": {}
  }
}
```

## Request limit
{: #concurrent-requests}

Each {{site.data.keyword.nlushort}} service instance is limited, based on the number of analyze requests being processed. For the Lite plan, the limit is 5 analyze requests per second; for the Standard plan, the limit is 150 analyze requests per second. Analyze requests exceeding these limits may receive a `429: Too Many Requests` error.

The limit for the Standard plan can be increased by [opening a support ticket](https://ibm.biz/ibmcloudsupport).

All other requests are rate-limited at 5 requests per second.

## Custom model training limit
{: custom-model-training-limit}

The maximum number of models that can be trained via the {{site.data.keyword.nlushort}} customization API in parallel is 3.

## Custom model size limit for Lite pricing plans
{: #custom-models}

There is a size limit for {{site.data.keyword.knowledgestudioshort}} custom models that are deployed to {{site.data.keyword.nlushort}} service instances on Lite pricing plans. To remove the custom model size limit, upgrade your {{site.data.keyword.nlushort}} service instance to a paid pricing plan. You can find your service instances on the {{site.data.keyword.cloud_notm}} [resources page](https://{DomainName}/resources).

## Language support
{: #usage-language-support}

Different language restrictions apply depending on how you use the service. For details, see the [Language support](/docs/natural-language-understanding?topic=natural-language-understanding-language-support) page.


