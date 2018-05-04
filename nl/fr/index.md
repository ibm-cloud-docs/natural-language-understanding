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

# A propos 
{: #about}

Avec {{site.data.keyword.nlufull}}, les développeurs peuvent analyser des caractéristiques sémantiques d'entrée de texte, notamment des catégories, des concepts, des émotions, des entités, des mots clés, des métadonnées, des relations, des rôles sémantiques et du sentiment.
{: shortdesc}

## Caractéristiques 
{: #features}

Envoyez des demandes à l'API avec du texte, du code HTML ou une URL publique, et spécifiez une ou plusieurs des caractéristiques suivantes pour l'analyse :

### Catégories
{: #categories}

Catégorisez votre contenu en fonction d'une hiérarchie de classification à cinq niveaux. Consultez la liste complète des catégories [ici](/docs/services/natural-language-understanding/categories.html). Exemple :

**Entrée**
> url: "www.cnn.com"

**Réponse**
> /news </br>
> /art and entertainment </br>
> /movies and tv/television </br>
> /news </br>
> /international news

### Concepts
{: #concepts}

Identifiez les concepts généraux qui ne sont pas nécessairement référencés directement dans le texte. Exemple :

**Entrée**
> text: "Natural Language Understanding uses natural language processing to analyze text."

**Réponse**
> Linguistics </br>
> Natural language processing </br>
> Natural language understanding

### Emotion
{: #emotion}

Analysez les émotions exprimées par des phrases cible spécifiques ou par le document dans son ensemble. Vous pouvez aussi activer l'analyse des émotions pour des entités et des mots clés qui sont détectés automatiquement par le service. Exemple :

**Entrée**
> text: "I love apples, but I hate oranges." </br>
> targets: "apples", and "oranges"

**Réponse**
> "apples": joy </br>
> "oranges": anger


### Entités
{: #entities}

Recherchez des personnes, des lieux, des événements et d'autres types d'entité mentionnés dans votre contenu. Consultez la liste complète des types et sous-types d'entité [ici](/docs/services/natural-language-understanding/entity-types.html). Exemple :

**Entrée**
> text: "IBM is an American multinational technology company headquartered in Armonk, New York, United States, with operations in over 170 countries."

**Réponse**
> IBM: Company </br>
> Armonk: Location </br>
> New York: Location </br>
> United States: Location

### Mots clés 
{: #keywords}

Recherchez des mots clés pertinents dans votre contenu. Exemple :

**Entrée**
>url: "[http://www-03.ibm.com/press/us/en/pressrelease/51493.wss](http://www-03.ibm.com/press/us/en/pressrelease/51493.wss)"

**Réponse**
>Australian Open </br>
>Tennis Australia </br>
>IBM SlamTracker analytics

### Métadonnées
{: #metadata}

Pour les entrées HTML et d'URL, identifiez l'auteur de la page Web, le titre de la page et la date de publication. Exemple :

**Entrée**
>url: "https://www.ibm.com/blogs/think/2017/01/cognitive-grid/"

**Réponse**
>Author: Stephen Callahan </br>
>Title: Girding the Grid with Cognitive Computing - THINK Blog </br>
>Publication date: January 31, 2017

### Relations
{: #relations}

Détectez la relation entre deux entités et identifiez le type de relation. Exemple :

**Entrée**
>text: "The Nobel Prize in Physics 1921 was awarded to Albert Einstein."

**Réponse**
>"awardedTo" relation between "Noble Prize in Physics" and "Albert Einstein" </br>
>"timeOf" relation between "1921" and "awarded"

### Rôles sémantiques 
{: #semantic-roles}

Analysez les phrases de forme sujet-action-objet et identifiez les entités et les mots clés qui sont les sujets ou les objets d'une action. Exemple :

**Entrée**
>text: "In 2011, Watson competed on Jeopardy!"

**Réponse**
>Subject: Watson </br>
>Action: competed </br>
>Object: on Jeopardy

### Sentiment
{: #sentiment}

Analysez le sentiment qui émane de phrases cible spécifiques ainsi que le sentiment qui émane d'un document dans son ensemble. Vous pouvez également envoyer des informations sur le sentiment pour des entités et des mots clés détectés en activant l'option de sentiment pour ces caractéristiques. Exemple :

**Entrée**
>text: "Thank you and have a nice day!"

**Réponse**
>Positive sentiment (score: 0.91)

## Langues prises en charge
{: #supported-languages}

Voir la [documentation relative à la prise en charge des langues](/docs/services/natural-language-understanding/language-support.html) pour des détails sur les langues prises en charge dans {{site.data.keyword.nlushort}}. 

## Tarification
{: #pricing}

Pour les informations de tarification, voir le [service {{site.data.keyword.nlushort}}](https://console.bluemix.net/catalog/services/natural-language-understanding) dans la catalogue {{site.data.keyword.cloud}}. 
