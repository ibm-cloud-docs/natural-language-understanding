---

copyright:
  years: 2015, 2022
lastupdated: "2022-08-02"

subcollection: natural-language-understanding

---

{:shortdesc: .shortdesc}
{:external: target="_blank" .external}
{:tip: .tip}
{:note: .note}
{:beta: .beta}
{:pre: .pre}
{:important: .important}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Overview - Customizing models
{: #customizing}

You can extend {{site.data.keyword.nlushort}} with custom models for supported feature and language combinations.
{: shortdesc}

## Before you begin
{: #customizing-before-you-begin}

1. If you haven't done so already, [get started](/docs/natural-language-understanding?topic=natural-language-understanding-getting-started) with {{site.data.keyword.nlushort}}.
1. Check [Language support for custom models](#language-support-for-custom-models) to make sure that the custom model you want to create is supported.
1. Follow the customization instructions for one of the following features.
   - [Entities and relations](/docs/natural-language-understanding?topic=natural-language-understanding-entities-and-relations)
   - [Categories (Beta)](/docs/natural-language-understanding?topic=natural-language-understanding-categories)
   - [Classifications](/docs/natural-language-understanding?topic=natural-language-understanding-classifications)

## Language support for custom models
{: #language-support-for-custom-models}

Check the *Custom model support* columns in the tables on the [Language support](/docs/natural-language-understanding?topic=natural-language-understanding-language-support) page to see the features that support custom models for each language.

## Specifying training parameters for custom models
{: #training-for-custom-models}

As part of the request to create or update a custom model, you may optionally include a training parameters object that specifies attributes of the model. For details, see feature-specific [Classifications training parameters](/docs/natural-language-understanding?topic=natural-language-understanding-classifications#classification-training-parameters).

## Targeted sentiment for custom model entities
{: #targeted-sentiment-for-custom-entities}

For English only, you can get sentiment scores for each custom model entity that is detected by the service by setting the `sentiment: true` option in the entities object. No other languages support targeted sentiment for custom model entities.

## Usage restrictions for custom models
{: #usage-restrictions-for-custom-models}

The maximum number of models that can be trained via the {{site.data.keyword.nlushort}} customization API in parallel is 3.
