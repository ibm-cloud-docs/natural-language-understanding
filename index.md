---

copyright:
  years: 2015, 2024
lastupdated: "2024-07-22"

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

# About
{: #about}

With {{site.data.keyword.nlufull}}, developers can analyze semantic features of text input, including categories, concepts, emotion, entities, keywords, metadata, relations, semantic roles, and sentiment.
{: shortdesc}

## Features
{: #features}

Send requests to the API with text, HTML, or a public URL, and specify one or more of the following features to analyze:

### Categories
{: #categories}

Categorize your content using a five-level classification hierarchy. View the complete list of categories [here](/docs/natural-language-understanding?topic=natural-language-understanding-categories-hierarchy). For example:

**Input**
> url: "www.cnn.com"

**Response**
> /news </br>
> /art and entertainment </br>
> /movies and tv/television </br>
> /news </br>
> /international news

### Concepts
{: #concepts}

Identify high-level concepts that aren't necessarily directly referenced in the text. For example:

**Input**
> text: "Natural Language Understanding uses natural language processing to analyze text."

**Response**
> Linguistics </br>
> Natural language processing </br>
> Natural language understanding

### Emotion
{: #emotion}

Analyze emotion conveyed by specific target phrases or by the document as a whole. You can also enable emotion analysis for entities and keywords that are automatically detected by the service. For example:

**Input**
> text: "I love apples, but I hate oranges." </br>
> targets: "apples", and "oranges"

**Response**
> "apples": joy </br>
> "oranges": anger

### Entities
{: #entities}

Find people, places, events, and other types of entities mentioned in your content. View the complete list of entity types and subtypes [here](/docs/natural-language-understanding?topic=natural-language-understanding-entity-type-systems). For example:

**Input**
> text: "IBM is an American multinational technology company headquartered in Armonk, New York, United States, with operations in over 170 countries."

**Response**
> IBM: Company </br>
> Armonk: Location </br>
> New York: Location </br>
> United States: Location

### Keywords
{: #keywords}

Search your content for relevant keywords. For example:

**Input**
>url: "[http://www-03.ibm.com/press/us/en/pressrelease/51493.wss](http://www-03.ibm.com/press/us/en/pressrelease/51493.wss)"

**Response**
>Australian Open </br>
>Tennis Australia </br>
>IBM SlamTracker analytics

### Metadata
{: #metadata}

For HTML and URL input, get the author of the webpage, the page title, and the publication date. For example:

**Input**
>url: "https://www.ibm.com/blogs/think/2017/01/cognitive-grid/"

**Response**
>Author: Stephen Callahan </br>
>Title: Girding the Grid with Cognitive Computing - THINK Blog </br>
>Publication date: January 31, 2017

### Relations
{: #relations}

Recognize when two entities are related, and identify the type of relation. For example:

**Input**
>text: "The Nobel Prize in Physics 1921 was awarded to Albert Einstein."

**Response**
>"awardedTo" relation between "Noble Prize in Physics" and "Albert Einstein" </br>
>"timeOf" relation between "1921" and "awarded"

### Semantic Roles
{: #semantic-roles}

Parse sentences into subject-action-object form, and identify entities and keywords that are subjects or objects of an action. For example:

**Input**
>text: "In 2011, Watson competed on Jeopardy!"

**Response**
>Subject: Watson </br>
>Action: competed </br>
>Object: on Jeopardy

### Sentiment
{: #sentiment}

Analyze the sentiment toward specific target phrases and the sentiment of the document as a whole. You can also get sentiment information for detected entities and keywords by enabling the sentiment option for those features. For example:

**Input**
>text: "Thank you and have a nice day!"

**Response**
>Positive sentiment (score: 0.91)

### Syntax
{: #syntax}

Identify the sentences and tokens in your text. For example:

**Input**
>text: "I love apples! I do not like oranges."

**Response**


|  Sentence | Location | 
| --- | --- |
| "I love apples!" | `[0, 14]` |
| "I do not like oranges." | `[15,37]` |

<br>

|  Token    | Lemma    | Part of Speech | Location   | 
|-----------|----------|----------------|------------|
| "I"       | "I"      | `PRON`         | `[0, 1]`   |
| "love"    | "love"   | `VERB`         | `[2, 6]`   |
| "apples"  | "apple"  | `NOUN`         | `[7, 13]`  |
| "!"       |          | `PUNCT`        | `[13, 14]` |
| "I"       |  "I"     | `PRON`         | `[15, 16]` |
| "do"      | "do"     | `AUX`          | `[17, 19]` |
| "not"     | "not"    | `PART`         | `[20, 23]` |
| "like"    | "like"   | `VERB`         | `[24, 28]` |
| "oranges" | "orange" | `NOUN`         | `[29, 36]` |
| "."       |          | `NOUN`         | `[36, 37]` |

### Summarization (Experimental)
{: #summarization}

Summarization is an experimental feature, and is not intended for use in production deployments. The details of the API, or the behavior of the underlying algorithm, may change with little notice.
{: important:}

In this Experimental release, Summarization is supported for English only.
{: note}

In this Experimental release, Summarization is supported only for instances hosted in the Dallas region/US-South data center.
{: note}

Return a summary of input source content. The summarization feature analyzes sets of sentences from a summarized document, and then chooses the set of sentences that best combines 3 objectives:

- Sentences that are the most similar to many other sentences in the document
- Sentences that cover the most frequent words in the document
- The set of sentences that are the least distant from the beginning of the document

See additional information in the [API reference](https://cloud.ibm.com/apidocs/natural-language-understanding#summarization). For example:

**Input**
>url: "https://www.ibm.com/cloud/watson-natural-language-understanding"

**Response**

>"Watson Natural Language Understanding is a cloud native product that uses deep learning to extract metadata from text such as entities, keywords, categories, sentiment, emotion, relations, and syntax. Get underneath the topics mentioned in your data by using text analysis to extract keywords, concepts, categories and more. Train Watson to understand the language of your business and extract customized insights with Watson Knowledge Studio."

## Supported languages
{: #supported-languages}

See the [Language support documentation](/docs/natural-language-understanding?topic=natural-language-understanding-language-support) for details about supported languages in {{site.data.keyword.nlushort}}.
