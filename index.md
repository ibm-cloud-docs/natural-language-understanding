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

# About

With {{site.data.keyword.nlufull}}, developers can analyze semantic features of text input, including categories, concepts, emotion, entities, keywords, metadata, relations, semantic roles, and sentiment.
{: shortdesc}

## Features
Send requests to the API with text, HTML, or a public URL, and specify one or more of the following features to analyze:

### Categories
Categorize your content using a five-level classification hierarchy. View the complete list of categories [here](/docs/services/natural-language-understanding/categories.html). For example:

**Input**
> url: "www.cnn.com"

**Response**
> /news </br>
> /art and entertainment </br>
> /movies and tv/television </br>
> /news </br>
> /international news

### Concepts
Identify high-level concepts that aren't necessarily directly referenced in the text. For example:

**Input**
> text: "Natural Language Understanding uses natural language processing to analyze text."

**Response**
> Linguistics </br>
> Natural language processing </br>
> Natural language understanding

### Emotion
Analyze emotion conveyed by specific target phrases or by the document as a whole. You can also enable emotion analysis for entities and keywords that are automatically detected by the service. For example:

**Input**
> text: "I love apples, but I hate oranges." </br>
> targets: "apples", and "oranges"

**Response**
> "apples": joy </br>
> "oranges": anger

### Entities
Find people, places, events, and other types of entities mentioned in your content. View the complete list of entity types and subtypes [here](/docs/services/natural-language-understanding/entity-types.html). For example:

**Input**
> text: "IBM is an American multinational technology company headquartered in Armonk, New York, United States, with operations in over 170 countries."

**Response**
> IBM: Company </br>
> Armonk: Location </br>
> New York: Location </br>
> United States: Location

### Keywords
Search your content for relevant keywords. For example:

**Input**
>url: "[http://www-03.ibm.com/press/us/en/pressrelease/51493.wss](http://www-03.ibm.com/press/us/en/pressrelease/51493.wss)"

**Response**
>Australian Open </br>
>Tennis Australia </br>
>IBM SlamTracker analytics

### Metadata
For HTML and URL input, get the author of the webpage, the page title, and the publication date. For example:

**Input**
>url: "https://www.ibm.com/blogs/think/2017/01/cognitive-grid/"

**Response**
>Author: Stephen Callahan </br>
>Title: Girding the Grid with Cognitive Computing - THINK Blog </br>
>Publication date: January 31, 2017

### Relations
Recognize when two entities are related, and identify the type of relation. For example:

**Input**
>text: "The Nobel Prize in Physics 1921 was awarded to Albert Einstein."

**Response**
>"awardedTo" relation between "Noble Prize in Physics" and "Albert Einstein" </br>
>"timeOf" relation between "1921" and "awarded"

### Semantic Roles
Parse sentences into subject-action-object form, and identify entities and keywords that are subjects or objects of an action. For example:

**Input**
>text: "In 2011, Watson competed on Jeopardy!"

**Response**
>Subject: Watson </br>
>Action: competed </br>
>Object: on Jeopardy

### Sentiment
Analyze the sentiment toward specific target phrases and the sentiment of the document as a whole. You can also get sentiment information for detected entities and keywords by enabling the sentiment option for those features. For example:

**Input**
>text: "Thank you and have a nice day!"

**Response**
>Positive sentiment (score: 0.91)

## Supported languages
The following table shows the supported languages for each feature. {{site.data.keyword.nlushort}} [automatically detects the language](/docs/services/natural-language-understanding/detectable-languages.html) of your source text by default. You can [override automatic language detection](/docs/services/natural-language-understanding/detectable-languages.html#overriding-language-detection) if you want to specify the language manually.

|            | Categories | Concepts | Emotion | Entities&#42; | Keywords | Metadata | Relations&#42; | Semantic Roles | Sentiment | 
|------------|------------|----------|---------|----------|----------|----------|-----------|----------------|-----------| 
| Arabic     | X&#42;&#42;&#42;       |          |         |          |          | X        | X         |                | X         | 
| English    | X          | X        | X       | X        | X        | X        | X         | X              | X         | 
| French     | X&#42;&#42;&#42;       |          |         | X        | X        | X        | X&#42;&#42;       |                | X         | 
| German     |            |          |         | X        | X        | X        | X&#42;&#42;       |                | X         | 
| Italian    | X&#42;&#42;&#42;       |          |         | X        | X        | X        | X&#42;&#42;       |                | X         | 
| Japanese   |            |          |         |          |          | X        |           |                |           | 
| Portuguese | X&#42;&#42;&#42;       |          |         | X        | X        | X        | X&#42;&#42;       |                | X         | 
| Russian    |            |          |         | X        | X        | X        |           |                | X         | 
| Spanish    | X&#42;&#42;&#42;       | X        |         | X        | X        | X        | X         | X              | X         | 
| Swedish    |            |          |         | X        | X        | X        |           |                |           | 


&#42;You can build {{site.data.keyword.knowledgestudiofull}} custom models for  <tt>entities</tt> and <tt>relations</tt> in English, French, German, Italian, Portuguese, and Spanish. You can use some of these languages in {{site.data.keyword.nlushort}} or you can customize the models.

&#42;&#42;These languages are only supported through custom models in [{{site.data.keyword.knowledgestudioshort}}](https://ibm.biz/watsonknowledgestudio).

&#42;&#42;&#42;These languages are supported in the public service, but not in Bluemix Dedicated.

## Pricing
For pricing information, see the [Natural Language Understanding service](https://console.ng.bluemix.net/catalog/services/natural-language-understanding) in Bluemix.
