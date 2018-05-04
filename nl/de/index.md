---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-28"

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

# Produktinfo
{: #about}

Mit {{site.data.keyword.nlufull}} können Entwickler semantische Merkmale von Texteingaben, einschließlich Kategorien, Konzepten, Emotionen, Entitäten, Schlüsselwörtern, Metadaten, Beziehungen, semantischen Rollen und Stimmung analysieren.
{: shortdesc}

## Features
{: #features}

Senden Sie an die API Anforderungen mit Text, HTML oder einer öffentlichen URL und geben Sie mindestens eins der folgenden Features für die Analyse an:

### Kategorien
{: #categories}

Kategorisieren Sie Ihren Inhalt mithilfe einer fünfstufigen Klassifikationshierarchie. Die vollständige Liste der Kategorien finden Sie [hier](/docs/services/natural-language-understanding/categories.html). Beispiel:

**Eingabe**
> URL: "www.cnn.com"

**Antwort**
> /news </br>
> /art and entertainment </br>
> /movies and tv/television </br>
> /news </br>
> /international news

### Konzepte
{: #concepts}

Ermitteln Sie übergeordnete Konzepte, die nicht notwendigerweise im Text direkt referenziert sind. Beispiel:

**Eingabe**
> text: "Natural Language Understanding uses natural language processing to analyze text."

**Antwort**
> Linguistics </br>
> Natural language processing </br>
> Natural language understanding

### Emotion
{: #emotion}

Analysieren Sie Emotionen, die von bestimmten Zielausdrücken oder vom Dokument insgesamt getragen sind. Sie können auch die Emotionsanalyse für Entitäten und Schlüsselwörter aktivieren, die automatisch vom Service erkannt werden. Beispiel:

**Eingabe**
> text: "I love apples, but I hate oranges." </br>
> targets: "apples", and "oranges"

**Antwort**
> "apples": joy </br>
> "oranges": anger

### Entitäten
{: #entities}

Suchen Sie Personen, Orte, Ereignisse und andere Typen von Entitäten, die in Ihrem Inhalt erwähnt werden. Die vollständige Liste der Entitätstypen und -untertypen finden Sie [hier](/docs/services/natural-language-understanding/entity-types.html). Beispiel:

**Eingabe**
> text: "IBM is an American multinational technology company headquartered in Armonk, New York, United States, with operations in over 170 countries."

**Antwort**
> IBM: Company </br>
> Armonk: Location </br>
> New York: Location </br>
> United States: Location

### Schlüsselwörter
{: #keywords}

Durchsuchen Sie Ihren Inhalt nach relevanten Schlüsselwörtern. Beispiel:

**Eingabe**
>URL: "[http://www-03.ibm.com/press/us/en/pressrelease/51493.wss](http://www-03.ibm.com/press/us/en/pressrelease/51493.wss)"

**Antwort**
>Australian Open </br>
>Tennis Australia </br>
>IBM SlamTracker analytics

### Metadaten
{: #metadata}

Für HTML- und URL-Eingaben rufen Sie den Autor der Webseite, den Seitentitel und das Veröffentlichungsdatum ab. Beispiel:

**Eingabe**
>URL: "https://www.ibm.com/blogs/think/2017/01/cognitive-grid/"

**Antwort**
>Author: Stephen Callahan </br>
>Title: Girding the Grid with Cognitive Computing - THINK Blog </br>
>Publication date: January 31, 2017

### Relations
{: #relations}

Erkennen Sie, wo zwei Entitäten zusammengehörig sind, und ermitteln Sie den Typ der Beziehung. Beispiel:

**Eingabe**
>text: "The Nobel Prize in Physics 1921 was awarded to Albert Einstein."

**Antwort**
>Beziehung "awardedTo" zwischen "Nobel Prize in Physics" und "Albert Einstein" </br>
>Beziehung "timeOf" zwischen "1921" und "awarded"

### Semantische Rollen
{: #semantic-roles}

Analysieren Sie Sätze in die Form "Subjekt-Aktion-Objekt" und ermitteln Sie Entitäten und Schlüsselwörter, die Subjekte oder Objekte einer Aktion sind. Beispiel:

**Eingabe**
>text: "In 2011, Watson competed on Jeopardy!"

**Antwort**
>Subject: Watson </br>
>Action: competed </br>
>Object: on Jeopardy

### Stimmung
{: #sentiment}

Analysieren Sie die Stimmung gegenüber bestimmten Zielausdrücken und die Stimmung des Dokuments insgesamt. Sie können auch Stimmungsinformationen für erkannte Entitäten und Schlüsselwörter abrufen, indem Sie die Option 'sentiment' für diese Features aktivieren. Beispiel:

**Eingabe**
>text: "Thank you and have a nice day!"

**Antwort**
>Positive sentiment (score: 0.91)

## Unterstützte Sprachen
{: #supported-languages}

In der [Dokumentation der Sprachunterstützung](/docs/services/natural-language-understanding/language-support.html) finden Sie Einzelheiten zu den in {{site.data.keyword.nlushort}} unterstützten Sprachen.

## Preisstruktur
{: #pricing}

Preisinformationen finden Sie im [{{site.data.keyword.nlushort}}-Service](https://console.bluemix.net/catalog/services/natural-language-understanding) des {{site.data.keyword.cloud}}-Katalogs.
