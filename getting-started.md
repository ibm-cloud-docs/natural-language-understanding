---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-02"

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

# Getting started tutorial
In this short tutorial, we introduce {{site.data.keyword.nlushort}} by analyzing some sample text for sentiment.
{:shortdesc}

## Step 1: Log in, create the service instance, and get your credentials
{: #create-service}

If you already know your credentials for the {{site.data.keyword.nlushort}} service instance, skip this step.
{: tip}

1.  Go to the [{{site.data.keyword.nlushort}} service](https://console.{DomainName}/catalog/services/natural-language-understanding/) and either sign up for a free {{site.data.keyword.Bluemix_notm}} account or log in.
1.  After you log in, type `sentiment-tutorial` in the **Service name** field, and click **Create**.
1.  Copy your credentials:
    1.  Click **Service credentials**.
    1.  Click **View credentials** under **Actions**.
    1.  Copy the `username` and `password` values.

## Step 2: Analyze sample content for sentiment
{: #analyze-sample}

Now you're ready to send requests to the service. Open a command-line interface and use [curl](https://curl.haxx.se/download.html) to run the example commands that appear in the following steps.

First, analyze the sentiment of some sample text. Issue this command to call the `GET /v1/analyze` method, which analyzes the sample text for sentiment and keywords. Replace `{username}` and `{password}` with the service credentials you copied in the previous step:

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## Step 3: Return keyword information
{: #analyze-keywords}

The previous call returned sentiment information for the whole text. Now expand the results to return sentiment analysis specifically on each of the keywords. Include the **keywords.sentiment** parameter and set it to `true`. Replace `{username}` and `{password}` with your information.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## Step 4: Target a phrase
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
