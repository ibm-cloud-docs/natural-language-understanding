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

