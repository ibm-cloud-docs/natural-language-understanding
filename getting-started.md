---

copyright:
  years: 2015, 2019
lastupdated: "2019-07-25"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:go: .ph data-hd-programlang='go'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# Getting started tutorial
{: #getting-started}

This short tutorial introduces the {{site.data.keyword.nlushort}} API with example requests and links to additional resources.
{:shortdesc}

## Before you begin
{: #before-you-begin}

- {: hide-dashboard} Create an instance of the service:
    1.  Go to the [{{site.data.keyword.nlushort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/catalog/services/natural-language-understanding){: new_window} page in the {{site.data.keyword.Bluemix_notm}} Catalog.
    2.  Sign up for a free {{site.data.keyword.Bluemix_notm}} account or log in.
    3.  Click **Create**.
- Copy the credentials to authenticate to your service instance:
    1.  On the **Manage** page, click **Show** to view your credentials.
    2.  Copy the `API Key` and `URL` values.
- Make sure that you have the `curl` command:
    - The examples use `curl` command to call methods of the HTTP interface. Install the version for your operating system from [curl.haxx.se ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://curl.haxx.se/){: new_window}. Install the version that supports the Secure Sockets Layer (SSL) protocol. Make sure to include the installed binary file on your `PATH` environment variable.

This tutorial shows you how to use the {{site.data.keyword.nlushort}} API from a command-line interface. To download client libraries for various programming languages, check out the [Watson SDKs](/docs/services/natural-language-understanding?topic=watson-using-sdks#using-sdks).
{:tip}

## Step 1: Analyze a webpage
{: #analyze-sample}

Run the following command to analyze a webpage to get sentiment, concepts, categories, entities, and keywords. <span class="hide-dashboard">Replace `{apikey}` and `{url}` with your service credentials.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2019-07-12"{: url} \
--header "Content-Type: application/json" \
--data '{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver",
  "features": {
    "sentiment": {},
    "categories": {},
    "concepts": {},
    "entities": {},
    "keywords": {}
  }
}'
```
{: pre}

The next step demonstrates how to specify options that customize the analysis for each feature.

## Step 2: Analyze target phrases and keywords
{: #analyze-phrase}

{{site.data.keyword.nlushort}} can analyze target phrases in context of the surrounding text for focused sentiment and emotion results. The **targets** option for sentiment in the following example tells the service to search for the targets "apples", "oranges", and "broccoli". Since "apples" and "oranges" are located in the text, sentiment scores are returned for those targets.

You can also get sentiment and emotion results for entities and keywords that are detected in your text. In the example, the **emotion** option for keywords tells the service to analyze each detected keyword for emotion results.

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2019-07-12"{: url} \
--request POST \
--header "Content-Type: application/json" \
--data '{
  "text": "I love apples! I do not like oranges.",
  "features": {
    "sentiment": {
      "targets": [
        "apples",
        "oranges",
        "broccoli"
      ]
    },
    "keywords": {
      "emotion": true
    }
  }
}'
```
{: pre}

## Next steps
{: #next-steps}

- View the [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/apidocs/natural-language-understanding){: new_window}.
- Learn how to identify [custom entities and relations](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing).
