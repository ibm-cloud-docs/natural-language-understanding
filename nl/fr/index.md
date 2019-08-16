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

# A propos
{: #about}

Avec {{site.data.keyword.nlufull}}, les développeurs peuvent analyser des caractéristiques sémantiques d'entrée de texte, notamment des catégories, des concepts, des émotions, des entités, des mots clés, des métadonnées, des relations, des rôles sémantiques et du sentiment.
{: shortdesc}

## Caractéristiques
{: #features}

Envoyez des demandes à l'API avec du texte, du code HTML ou une URL publique, et spécifiez une ou plusieurs des caractéristiques suivantes pour l'analyse :

### Catégories
{: #categories}

Catégorisez votre contenu en fonction d'une hiérarchie de classification à cinq niveaux. Consultez la liste complète des catégories [ici](/docs/services/natural-language-understanding?topic=natural-language-understanding-categories-hierarchy). Exemple :

**Entrée**
> url: "www.cnn.com"

**Réponse**
> /actualités </br>
> /art et divertissement </br>
> /cinéma et tv/télévision </br>
> /actualités </br>
> /actualités internationales

### Concepts
{: #concepts}

Identifiez les concepts généraux qui ne sont pas nécessairement référencés directement dans le texte. Exemple :

**Entrée**
> text: "Natural Language Understanding utilise le traitement automatique du langage naturel pour analyser un texte."

**Réponse**
> Linguistique </br>
> Traitement du langage naturel </br>
> Natural Language Understanding

### Emotion
{: #emotion}

Analysez les émotions exprimées par des phrases cible spécifiques ou par le document dans son ensemble. Vous pouvez aussi activer l'analyse des émotions pour des entités et des mots clés qui sont détectés automatiquement par le service. Exemple :

**Entrée**
> text: "J'aime les pommes, mais je déteste les oranges." </br>
> targets: "pommes" et "oranges"

**Réponse**
> "pommes": joie </br>
> "oranges": colère

### Entités
{: #entities}

Recherchez des personnes, des lieux, des événements et d'autres types d'entité mentionnés dans votre contenu. Consultez la liste complète des types et sous-types d'entité [ici](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems). Exemple :

**Entrée**
> text: "IBM est une entreprise de technologie multinationale américaine dont le siège social se trouve à Armonk, New York, aux Etats-Unis, et qui exerce ses activités dans plus de 170 pays."

**Réponse**
> IBM : Entreprise </br>
> Armonk : Emplacement </br>
> New York : Emplacement </br>
> Etats-Unis : Emplacement

### Mots clés
{: #keywords}

Recherchez des mots clés pertinents dans votre contenu. Exemple :

**Entrée**
>url: "[http://www-03.ibm.com/press/us/en/pressrelease/51493.wss](http://www-03.ibm.com/press/us/en/pressrelease/51493.wss)"

**Réponse**
>Open d'Australie </br>
>Tennis Australie </br>
>IBM SlamTracker analytics

### Métadonnées
{: #metadata}

Pour les entrées HTML et d'URL, identifiez l'auteur de la page Web, le titre de la page et la date de publication. Exemple :

**Entrée**
>url: "https://www.ibm.com/blogs/think/2017/01/cognitive-grid/"

**Réponse**
>Auteur : Stephen Callahan </br>
>Titre : Girding the Grid with Cognitive Computing - THINK Blog </br>
>Date de publication : 31 janvier 2017

### Relations
{: #relations}

Détectez la relation entre deux entités et identifiez le type de relation. Exemple :

**Entrée**
>text: "En 1921, le prix Nobel de physique a été attribué à Albert Einstein."

**Réponse**
>"awardedTo" relation entre "Prix Nobel de physique" et "Albert Einstein" </br>
>Relation "timeOf" entre "1921" and "attribué"

### Rôles sémantiques
{: #semantic-roles}

Analysez les phrases de forme sujet-action-objet et identifiez les entités et les mots clés qui sont les sujets ou les objets d'une action. Exemple :

**Entrée**
>text: "En 2011, Watson a joué à Jeopardy !"

**Réponse**
>Sujet : Watson </br>
>Action : joué </br>
>Objet : à Jeopardy

### Sentiment
{: #sentiment}

Analysez le sentiment qui émane de phrases cible spécifiques ainsi que le sentiment qui émane d'un document dans son ensemble. Vous pouvez également envoyer des informations sur le sentiment pour des entités et des mots clés détectés en activant l'option de sentiment pour ces caractéristiques. Exemple :

**Entrée**
>text: "Merci et bonne journée !"

**Réponse**
>Sentiment positif (score : 0,91)

## Langues prises en charge
{: #supported-languages}

Voir la [documentation relative à la prise en charge des langues](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support) pour des détails sur les langues prises en charge dans {{site.data.keyword.nlushort}}.
