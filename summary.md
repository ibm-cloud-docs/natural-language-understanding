---

copyright:
  years: 2015, 2020
lastupdated: "2020-08-17"

subcollection: natural-language-understanding

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:deprecated: .deprecated}
{:important: .important}
{:note: .note}
{:tip: .tip}
{:preview: .preview}
{:beta: .beta}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}

# Summarization
{: #summary-overview}

Summarization is an experimental feature, and is not intended for use in production deployments. The details of the API, or the behavior of the underlying algorithm, may change with little notice.
{: important:}

In this Experimental release, Summarization is supported for English only.
{: note}

This feature allows you to return a summary of content from your input source.

## Request
{: #summary-request}

The following request example analyzes an article from the IBM Newsroom

```curl
curl -X POST -u "apikey:{apikey}" \
--header "Content-Type: application/json" \
--data '{
  "url": "newsroom.ibm.com/Five-Things-IBM-Workday",
  "features": {
    "summarization": {}
  }
}' \
"{url}/v1/analyze?version=2020-08-01"
```

## Response
{: #summary-response}

```
{
  "usage": {
    "text_units": 1,
    "text_characters": 2922,
    "features": 0
  },
  "summarization": {
    "text": "Today, IBM and Workday, a leading provider of enterprise applications for human resources and finance, announced a joint solution designed to help companies begin the process of safely re-opening their workplaces. Here are five key takeaways from the announcement. The two companies, which have had a partnership since 2011, announced a new solution to help businesses and communities determine when and how to safely open up their workplaces during the ongoing COVID-19 pandemic."
  },
  "retrieved_url": "https://newsroom.ibm.com/Five-Things-IBM-Workday",
  "language": "en"
```
