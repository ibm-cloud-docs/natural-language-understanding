---

copyright:
  years: 2015, 2017
lastupdated: "2018-04-27"

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

# Getting started tutorial
In this short tutorial, we introduce {{site.data.keyword.nlushort}} by analyzing some sample text for sentiment.
{:shortdesc}

## Before you begin
{: #before-you-begin}

- Create an instance of the service:
    1.  Go to the [{{site.data.keyword.nlushort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.{DomainName}/catalog/services/natural-language-understanding){: new_window} page in the {{site.data.keyword.Bluemix_notm}} Catalog.
    1.  Sign up for a free {{site.data.keyword.Bluemix_notm}} account or log in.
    1.  Click **Create**.
- Copy the credentials to authenticate to your service instance:
    1.  On the service dashboard, click the **Service credentials** tab.
    1.  Click **Show** to view your credentials.
    1.  Copy the `username`, `password`, and `url` values.
- Make sure you have cURL:
    - The examples use cURL to call methods of the HTTP interface. Install the version for your operating system from [curl.haxx.se ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://curl.haxx.se/){: new_window}. Install the version that supports the Secure Sockets Layer (SSL) protocol. Make sure to include the installed binary file on your `PATH` environment variable.

## Step 1: Analyze sample content for sentiment
{: #analyze-sample}

First, analyze the sentiment of some sample text. Open a command-line interface and run the following command to call the `GET /v1/analyze` method, which analyzes the sample text for sentiment and keywords. Replace `{username}` and `{password}` with the service credentials you copied in the previous step:

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## Step 2: Return keyword information
{: #analyze-keywords}

The previous call returned sentiment information for the whole text. Now expand the results to return sentiment analysis specifically on each of the keywords. Include the **keywords.sentiment** parameter and set it to `true`. Replace `{username}` and `{password}` with your information.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## Step 3: Target a phrase
{: #analyze-phrase}

Now target specific content to see a sentence-level or phrase-level analysis (instead of a document or keyword analysis) by including the phrase `the%20American%20dream%20` in the **sentiment.targets** parameter. Don't forget to replace `{username}` and `{password}` with your information.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%20We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true&sentiment.targets=the%20American%20dream"
```
{:pre}

## Next steps
{: #next-steps}

You're done! This tutorial barely scratches the surface of what you can accomplish with {{site.data.keyword.nlushort}}. For more information about the features of the API, see these resources:

- View the [API Reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/){: new_window} for details and examples of each of the parameters.
- Learn how to identify [custom entities and relations](/docs/services/natural-language-understanding/customizing.html).
