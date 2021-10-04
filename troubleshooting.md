---

copyright:
  years: 2015, 2021
lastupdated: "2021-10-04"

subcollection: natural-language-understanding

content-type: troubleshoot

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
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
{:download: .download}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Troubleshooting
{: #troubleshoot}

If you have problems with {{site.data.keyword.nlushort}}, the following troubleshooting tips might help.
{: shortdesc}

## Entities and relations entity types are not consistent
{: #inconsistent-entity-types}
{: troubleshoot}

The entity type systems for the entities and relations features are not always consistent. For some languages and version dates, relations results will contain entity types that are different from the entity types that appear in entities results. See [Entity types and subtypes](/docs/natural-language-understanding?topic=natural-language-understanding-entity-type-systems) and [Relation types](/docs/natural-language-understanding?topic=natural-language-understanding-relation-type-systems) for more details. 

## Incorrect language detection
{: #incorrect-language-detection}
{: troubleshoot}

The automatic language detection might not be accurate for text that contains fewer than 100 characters. If the service doesn't detect the correct language of your text, you can [override automatic language detection](/docs/natural-language-understanding?topic=natural-language-understanding-overriding-language-detection).

## Too many requests
{: #too-many-requests}
{: troubleshoot}

If you are seeing a "429: Too many requests" error, your service instance is likely hitting the concurrent requests limit. View the [Usage limits](/docs/natural-language-understanding?topic=natural-language-understanding-usage-limits#concurrent-requests) page for more information.

## Unable to analyze more than one URL
{: #multiple-webpages}
{: troubleshoot}

You can specify only one publicly accessible URL in your API request, therefore you cannot extract sentiment scoring from several URLs.  You could, however, compile the text from multiple web pages and then pass that entire compiled text for sentiment analysis.

## Unexpected results from webpage analysis
{: #unexpected-webpage-results}
{: troubleshoot}

Analyzing a webpage might return unexpected results in some cases. To investigate, try setting the **return_analyzed_text** parameter to `true` to inspect the actual text that is being analyzed in your request. In cases where [webpage cleaning](/docs/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#webpage-cleaning) does not remove enough unwanted text, consider using the [**xpath**](/docs/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#xpath) parameter to focus the analysis on specific elements of the page.

## Explanations for particular results
{: #explanations-for-results}
{: troubleshoot}

{{site.data.keyword.nlushort}} does not provide any diagnostic tools to explain why a particular request returns a particular result. The service is designed to provide accurate results for as many text samples as possible, but due to the nature of the machine learning models we use, there is no guarantee that any particular result will look correct from a human perspective.
