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

# Informazioni su
{: #about}

Con {{site.data.keyword.nlufull}}, gli sviluppatori possono analizzare le funzioni semantiche di un input di testo, compresi categorie, concetti, emozione, entità, parole chiave, metadati, relazioni, ruoli semantici e parere.
{: shortdesc}

## Funzioni
{: #features}

Invia richieste alla API con testo, HTML o un URL pubblico e specifica una o più delle seguenti funzioni da analizzare:

### Categorie
{: #categories}

Categorizza il tuo contenuto utilizzando una gerarchia di classificazione a cinque livelli. Visualizza l'elenco completo di categorie [qui](/docs/services/natural-language-understanding?topic=natural-language-understanding-categories-hierarchy). Ad esempio:

**Immissione**
> url: "www.cnn.com"

**Risposta**
> /news </br>
> /art and entertainment </br>
> /movies and tv/television </br>
> /news </br>
> /international news

### Concetti
{: #concepts}

Identifica i concetti di alto livello a cui non si fa necessariamente riferimento in modo diretto nel testo. Ad esempio:

**Input**
> text: "Natural Language Understanding uses natural language processing to analyze text."

**Risposta**
> Linguistics </br>
> Natural language processing </br>
> Natural language understanding

### Emozione
{: #emotion}

Analizza l'emozione trasmessa da specifiche frasi mirate o da un documento nel suo insieme. Puoi anche abilitare l'analisi delle emozioni per le entità e le parole chiave rilevate automaticamente dal servizio. Ad esempio:

**Input**
> text: "I love apples, but I hate oranges." </br>
> targets: "apples", and "oranges"

**Risposta**
> "apples": joy </br>
> "oranges": anger

### Entità
{: #entities}

Trova persona, posti, eventi e altri tipi di entità menzionati nel tuo contenuto. Visualizza l'elenco completo di tipi e sottotipi di entità [qui](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems). Ad esempio:

**Input**
> text: "IBM is an American multinational technology company headquartered in Armonk, New York, United States, with operations in over 170 countries."

**Risposta**
> IBM: Company </br>
> Armonk: Location </br>
> New York: Location </br>
> United States: Location

### Parole chiave
{: #keywords}

Cerca nel tuo contenuto delle parole chiave pertinenti. Ad esempio:

**Input**
>url: "[http://www-03.ibm.com/press/us/en/pressrelease/51493.wss](http://www-03.ibm.com/press/us/en/pressrelease/51493.wss)"

**Risposta**
>Australian Open </br>
>Tennis Australia </br>
>IBM SlamTracker analytics

### Metadati
{: #metadata}

Per l'input HTML e URL; ottieni l'autore della pagina web, il titolo della pagina e la data di pubblicazione. Ad esempio:

**Input**
>url: "https://www.ibm.com/blogs/think/2017/01/cognitive-grid/"

**Risposta**
>Author: Stephen Callahan </br>
>Title: Girding the Grid with Cognitive Computing - THINK Blog </br>
>Publication date: January 31, 2017

### Relazioni
{: #relations}

Riconosci quando due entità sono correlate e identifica il tipo di relazione. Ad esempio:

**Input**
>text: "The Nobel Prize in Physics 1921 was awarded to Albert Einstein."

**Risposta**
>"awardedTo" relation between "Noble Prize in Physics" and "Albert Einstein" </br>
>"timeOf" relation between "1921" and "awarded"

### Ruoli semantici
{: #semantic-roles}

Analizza le frasi in formato soggetto-azione-oggetto e identifica le entità e le parole chiave che sono soggetti od oggetti di un'azione. Ad esempio:

**Input**
>text: "In 2011, Watson competed on Jeopardy!"

**Risposta**
>Subject: Watson </br>
>Action: competed </br>
>Object: on Jeopardy

### Parere
{: #sentiment}

Analizza il parere su specifiche frasi mirate e il parere sul documento nel suo insieme. Puoi ottenere le informazioni sui pareri per le entità e le parole chiave rilevate abilitando l'opzione relativa al parere per queste funzioni. Ad esempio:

**Input**
>text: "Thank you and have a nice day!"

**Risposta**
>Positive sentiment (score: 0.91)

## Lingue supportate
{: #supported-languages}

Vedi la [documentazione del Supporto linguistico](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support) per i dettagli sulle lingue supportate in {{site.data.keyword.nlushort}}.
