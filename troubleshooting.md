---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-16"

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
{:download: .download}

# Troubleshooting

If you have problems with {{site.data.keyword.nlushort}}, the following troubleshooting tips might help.
{:shortdesc}

## Entities and relations entity types are not consistent
{: #inconsistent-entity-types}

The entity type systems for the entities and relations features are not always consistent. For some languages and version dates, relations results will contain entity types that are different from the entity types that appear in entities results. See [Entity types and subtypes](entity-types.html) and [Relation types](relations.html) for more details. 

## Incorrect language detection
{: #incorrect-language-detection}

The automatic language detection might not be accurate for text that contains fewer than 100 characters. If the service doesn't detect the correct language of your text, you can [override automatic language detection](overriding-language-detection.html).

## Too many requests
{: #too-many requests}

If you are seeing a "429: Too many requests" error, your service instance is likely hitting the concurrent requests limit. View the [Usage limits](usage-limits.html#concurrent-requests) page for more information.

## Unexpected results from webpage analysis
{: #unexpected-webpage-results}

Analyzing a webpage might return unexpected results in some cases. To investigate, try setting the **return_analyzed_text** parameter to `true` to inspect the actual text that is being analyzed in your request. In cases where [webpage cleaning](analyzing-webpages.html#webpage-cleaning) does not remove enough unwanted text, consider using the [**xpath**](analyzing-webpages.html#xpath) parameter to focus the analysis on specific elements of the page.

## Explanations for particular results
{: #explanations-for-results}

{{site.data.keyword.nlushort}} does not provide any diagnostic tools to explain why a particular request returns a particular result. The service is designed to provide accurate results for as many text samples as possible, but due to the nature of the machine learning models we use, there is no guarantee that any particular result will look correct from a human perspective.




