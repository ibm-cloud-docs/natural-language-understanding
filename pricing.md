---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-08"

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

# Pricing
{: #pricing}

{{site.data.keyword.nlushort}} has three pricing plans: Lite, Standard and Premium.

This page contains pricing information in USD. To view pricing information in your local currency, see the [{{site.data.keyword.nlushort}}](https://{DomainName}/catalog/services/natural-language-understanding) page in the {{site.data.keyword.cloud}} catalog.
{: tip}

## Lite
{: #lite}

The Lite plan is free for users who are looking to try out Natural Language Understanding or build a proof-of-concept.

**Pricing**
- Free 30,000 NLU items/month

**Custom Model**
- 1 free custom model

## Standard
{: #standard}

A "pay-as-you-go" plan that is recommended once you are ready to move your application from proof-of-concept to production.

**Pricing** (billed monthly)
- Tier 1: $0.003/NLU item for the first 1-250,000 NLU items
- Tier 2: $0.001/NLU item for 250,001 to 5,000,000 NLU items
- Tier 3: $0.0002/NLU item for additional NLU items past 5,000,000

**Custom Model** ($/custom model/month)
- $800 for all tiers

## Premium
{: #premium}

A plan that offers a higher level of security and isolation to help customers with sensitive data requirements.

_Please [contact sales](https://www.ibm.com/account/reg/us-en/signup?formid=MAIL-watson) for details._

## What is an NLU item?
{: #nlu-items}

API usage is measured in **NLU items**. One NLU item is one **text unit** (up to 10,000 characters of text) that is analyzed for one **feature**, such as sentiment.

To keep track of the number of NLU items in your request, you can examine the `usage` object in the response. For example, analyzing 15,000 characters of text for sentiment, emotion, and keywords will return the following usage information.

```json
"usage": {
  "text_units": 2,
  "text_characters": 15000,
  "features": 3
}
```
{: code}
  
There are **2** text units and **3** features in the request, so there are **2 × 3 = 6** NLU items.

Text units are counted seperately for each request. If one request analyzes 15,000 characters and another request analyzes 3,000 characters, that counts as 3 text units total. The first request has 2 text units and the second request has 1 text unit.

## FAQ
{: #faq}

### I want to understand sentiment across 20,000 tweets. How can I estimate what I will pay on the Standard plan?

- Step 1: Calculate the number of text units per request<br>
As of November 2018, the maximum number of characters allowed in a tweet are 280.<br>
That translates to one text unit per request.

- Step 2: Calculate the number of features per request<br>
One feature, sentiment, is enabled in each request.

- Step 3: Calculate the number of NLU items per request<br>
NLU items = (Number of text units) × (Number of features)<br>
NLU items = 1 text unit × 1 feature = 1 NLU item

- Step 4: Calculate total number of NLU items <br>
Total number of NLU items = (Number of requests) × (Number of NLU items per request) <br>
Total number of NLU items = 20,000 requests × 1 NLU item per request = 20,000 total NLU items

- Step 5: Estimate the price for total number of NLU items<br>
For the Standard pricing plan, the first 250,000 NLU items are charged at $0.003 per item<br>
Estimated price = (Number of NLU items) × (Price per NLU item) <br>
Estimated price = 20,000 NLU items × $0.003 = $60

**Total cost = $60**

### I want to extract Entities, Keywords and Categories for 50,000 documents with an average of 12,000 characters per document. What will be my estimated price on the Standard plan?
- Step 1: Calculate number of text units per request <br>
Text units = Number of groups of 10,000 characters or less <br>
12,000 characters per request = 2 text units per request

- Step 2: Calculate the number of features per request<br>
Entities, Keywords, Categories = 3 features

- Step 3: Calculate number of NLU items per request <br>
NLU items = (Number of text unit) × (Number of features) <br>
NLU items = 2 data units × 3 enrichments = 6 NLU items

- Step 4: Calculate total number of NLU items <br>
Total number of NLU items = (Number of requests or documents) × (Number of NLU items) <br>
Total number of NLU items = 50,000 requests × 6 NLU items = 300,000 NLU items

- Step 5: Estimate the price for the total number of NLU items <br>
The first 250,000 NLU items are charged at $0.003 per item<br>
Additional NLU items until the 5,000,000th NLU item are charged at $0.001 per item<br>
Estimated price = (250,000 NLU items × $0.003) + (50,000 NLU items × $0.001) <br>
Estimated price = $750 + $50


**Total cost = $800**

### How do I calculate the Standard Plan price for 15,000 NLU items?
- Since the first 250,000 NLU items are priced at $0.003/item - your 15,000 NLU items are charged at $0.003 per item (Tier 1). Your estimated price would be $45. 

### How do I calculate the Standard Plan price for 6,000,000 NLU items?
- Since you have more than 5,000,000 NLU items, your first 250,000 NLU items are charged at $0.003 per item (Tier 1), your next 4,750,000 NLU items are charged at $0.001 per item (Tier 2), and your remaining 1,000,000 NLU items are charged at $0.0002 per item (Tier 3). Your estimated price would be $5,700. 



