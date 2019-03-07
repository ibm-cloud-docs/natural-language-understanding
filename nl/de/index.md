---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-25"

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

Kategorisieren Sie Ihren Inhalt mithilfe einer fünfstufigen Klassifikationshierarchie. Die vollständige Liste der Kategorien finden Sie [hier](/docs/services/natural-language-understanding?topic=natural-language-understanding-categories-hierarchy). Beispiel:

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
> Text: "Natural Language Understanding verwendet für die Textanalyse die Verarbeitung natürlicher Sprache."

**Antwort**
> Linguistics </br>
> Natural language processing </br>
> Natural language understanding

### Emotion
{: #emotion}

Analysieren Sie Emotionen, die von bestimmten Zielausdrücken oder vom Dokument insgesamt getragen sind. Sie können auch die Emotionsanalyse für Entitäten und Schlüsselwörter aktivieren, die automatisch vom Service erkannt werden. Beispiel:

**Eingabe**
> Text: "Ich liebe Äpfel, aber ich hasse Orangen." </br>
> Ziele: "Äpfel" und "Orangen"

**Antwort**
> "Äpfel": joy </br>
> "Orangen": anger

### Entitäten
{: #entities}

Suchen Sie Personen, Orte, Ereignisse und andere Typen von Entitäten, die in Ihrem Inhalt erwähnt werden. Die vollständige Liste der Entitätstypen und -untertypen finden Sie [hier](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems). Beispiel:

**Eingabe**
> Text: "IBM ist ein amerikanisches multinationales Technologieunternehmen mit Hauptsitz in Armonk, New York, Vereinigte Staaten, und Unternehmensaktivitäten in über 170 Ländern."

**Antwort**
> IBM: Company </br>
> Armonk: Location </br>
> New York: Location </br>
> Vereinigte Staaten: Location

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
>Publication date: 31. Januar 2017

### Relations
{: #relations}

Erkennen Sie, wo zwei Entitäten zusammengehörig sind, und ermitteln Sie den Typ der Beziehung. Beispiel:

**Eingabe**
>Text: "Der Nobelpreis für Physik 1921 wurde Albert Einstein zuerkannt."

**Antwort**
>Beziehung "awardedTo" zwischen "Nobelpreis für Physik" und "Albert Einstein" </br>
>Beziehung "timeOf" zwischen "1921" und "awarded"

### Semantische Rollen
{: #semantic-roles}

Analysieren Sie Sätze in die Form "Subjekt-Aktion-Objekt" und ermitteln Sie Entitäten und Schlüsselwörter, die Subjekte oder Objekte einer Aktion sind. Beispiel:

**Eingabe**
>Text: "Im Jahr 2011 gewann Watson in Jeopardy."

**Antwort**
>Subjekt: Watson </br>
>Aktion: gewann </br>
>Objekt: in Jeopardy

### Stimmung
{: #sentiment}

Analysieren Sie die Stimmung gegenüber bestimmten Zielausdrücken und die Stimmung des Dokuments insgesamt. Sie können auch Stimmungsinformationen für erkannte Entitäten und Schlüsselwörter abrufen, indem Sie die Option 'sentiment' für diese Features aktivieren. Beispiel:

**Eingabe**
>Text: "Danke und auf Wiedersehen!"

**Antwort**
>Positive Stimmung (Score: 0,91)

## Unterstützte Sprachen
{: #supported-languages}

In der [Dokumentation der Sprachunterstützung](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support) finden Sie Einzelheiten zu den in {{site.data.keyword.nlushort}} unterstützten Sprachen.
