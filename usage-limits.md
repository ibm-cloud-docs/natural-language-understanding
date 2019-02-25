---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-25"

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

## Concurrent request limit
{: #concurrent-requests}

Each {{site.data.keyword.nlushort}} service instance is limited to 30 concurrent requests. It's possible that this limit may decrease for service instances on the Lite and Standard plans when the system is experiencing exceptionally heavy traffic. For example, an application that makes 35 simultaneous requests from a single service instance will exceed the concurrent request limit by five requests, and five of those requests will return a `429: Too Many Requests` error.

To increase your concurrent request limit, [open a support ticket](https://ibm.biz/ibmcloudsupport).

## Custom model size limit for Lite pricing plans
{: #custom-models}

There is a size limit for {{site.data.keyword.knowledgestudioshort}} custom models that are deployed to {{site.data.keyword.nlushort}} service instances on Lite pricing plans. To remove the custom model size limit, upgrade your {{site.data.keyword.nlushort}} service instance to a paid pricing plan. You can find your service instances on the {{site.data.keyword.cloud_notm}} [resources page](https://{DomainName}/resources).

## Language support
{: #language-support}

Different language restrictions apply depending on how you use the service. For details, see the [Language support](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support) page.


