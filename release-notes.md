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

# Release notes

The following new features and changes to the service are available.
{: shortdesc}

## Service API versioning

**Current API version**: 2017-02-27

API requests require a version parameter that takes the date in the format `version=YYYY-MM-DD`. Send the version parameter with every API request.

When we change the API in a backwards-incompatible way, we release a new minor version. To take advantage of the changes in a new version, change the value of the version parameter to the new date. If you're not ready to update to that version, don't change your version date.

## Changes

### 30 July 2017
{: #30-july-2017}

- You can control cost by using the optional `limit_text_characters` parameter to limit the number of characters that are processed. For example:

```
{
  "text": "The United States of America, commonly known as the United States (U.S.) or America, is a federal republic composed of 50 states, a federal district, five major self-governing territories, and various possessions. Forty-eight of the fifty states and the federal district are contiguous and located in North America between Canada and Mexico. The state of Alaska is in the northwest corner of North America, bordered by Canada to the east and across the Bering Strait from Russia to the west.",
  "features": {
    "entities": {}
  },
  "limit_text_characters": 50,
  "return_analyzed_text": true
}
```

- Each character counts as one character, regardless of whether the character is a single-byte character or a multibyte character.

- For metering, one {{site.data.keyword.nlushort}} Item continues to be one feature (also known as an enrichment) per one text unit. One text unit is 10,000 characters or less.

- For detailed pricing information, see [{{site.data.keyword.nlushort}}](https://console.ng.bluemix.net/catalog/services/natural-language-understanding) in the {{site.data.keyword.Bluemix}} Catalog.

- In addition to adding the `limit_text_characters` parameter, the following changes were made to text size limits and truncation:

  - All text greater than 50,000 characters will be truncated before processing. Previously, truncation was based on kilobytes, where one kilobyte equaled 1024 bytes.

  - An informational message is returned in the response when text beyond 50,000 characters is truncated.

  - Text limit size for custom models has been bumped from 10,000 characters to 50,000 characters.

  - Usage information is added to the response for clarity around number of {{site.data.keyword.nlushort}} Items used for each request. For example:

```
{
  "usage": {
    "text_units": 5,
    "text_characters": 41186,
    "features": 1
  },
  ...
}
```

### 8 May 2017
{: #8-may-2017}

- Updated the emotion tone score model. The training dataset was expanded and feature engineering was altered and as a result, the model has higher precision on our benchmark dataset.

### 27 March 2017
{: #27-march-2017}

- The entity and sentiment models have been improved, which means that when you call those features, you'll get better results.
- Relations now supports {{site.data.keyword.knowledgestudioshort}} custom models in French, German, Italian, and Portuguese.

### 15 March 2017
{: #15-march-2017}

We released updates to the emotion tone score model. The training dataset was expanded and as a result, the model has higher precision on our benchmark dataset.

### 27 February 2017
{: #27-february-2017}

The Natural Language Understanding service is now GA.

