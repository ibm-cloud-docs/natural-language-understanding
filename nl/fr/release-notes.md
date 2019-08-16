---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-21"

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

# Notes sur l'édition
{: #release-notes}

Les nouvelles caractéristiques et les modifications apportées au service
ci-après sont disponibles.
{: shortdesc}

## Nouveau processus d'authentification d'API
{: #iam-auth-process }

Le 30 octobre 2018, les emplacements Dallas (Etats-Unis, Sud) et Francfort (Allemagne) ont commencé à utiliser l'authentification IAM (Identity and Access Management) par jeton. (Pour plus d'informations, voir la section relative à l'[authentification avec des jetons IAM ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](/docs/services/watson/getting-started-iam.html).)
{: important}

Le service {{site.data.keyword.nlushort}} inclut un nouveau processus d'authentification d'API pour les instances de service hébergées aux emplacements suivants :

- Dallas depuis le 30 octobre 2018
- Francfort depuis le 30 octobre 2018
- Londres
- Sydney depuis le 29 mai 2018
- Tokyo
- Washington, DC depuis le 12 juin 2018

{{site.data.keyword.cloud_notm}} migre vers l'authentification IAM (Identity and Access Management) par jeton. Avec certaines instances de service, vous vous authentifiez auprès de l'API en utilisant IAM.

- Avec les *nouvelles* instances de service créées sur les différents sites à partir de la date indiquée, vous vous authentifiez auprès de l'API en utilisant IAM. Vous pouvez transmettre un jeton bearer dans un en-tête d'autorisation ou une clé d'API. Les jetons prennent en charge les demandes authentifiées sans intégrer de données d'identification de service dans chaque appel. Les clés d'API utilisent l'authentification de base. Pour plus d'informations, voir [IAM](/docs/services/watson/getting-started-iam.html).

    Lorsque vous utilisez un kit SDK Watson, vous pouvez transmettre la clé d'API et laisser le kit SDK gérer le cycle de vie des jetons. Pour plus d'informations et pour avoir accès à des exemples, voir la rubrique relative à l'[authentification ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/natural-language-understanding/#authentication){: new_window} dans les références d'API.
- Pour les instances de service _existantes_ créées avant la date indiquée, vous continuez de vous authentifier en indiquant le nom d'utilisateur et le mot de passe pour l'instance de service. Il peut également être nécessaire de migrer ces instances de service vers l'authentification IAM. Des mises à jour concernant les dates et le processus de migration seront mises à disposition. Pour plus d'informations sur la migration, voir [Migration des instances de service Cloud Foundry vers un groupe de ressources](/docs/resources/instance_migration.html).

Pour savoir quelle méthode d'authentification utiliser, consultez les données d'identification de service en cliquant sur l'instance de service dans la page des ressources [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/resources){: new_window}.


## Gestion des versions d'API de service
{: #service-api-versioning}

**Version d'API actuelle** : 2019-06-04

Les demandes d'API requièrent un paramètre de version qui admet la date au format `version=AAAA-MM-JJ`. Envoyez le paramètre de version avec chaque demande d'API.

Lorsque nous changeons l'API et que celle-ci n'est plus compatible avec les versions antérieures, nous publions une nouvelle version mineure. Pour bénéficier des changements apportés dans une nouvelle version, remplacez la valeur du paramètre de version par la nouvelle date. Si vous n'êtes pas prêt à effectuer la mise à jour vers cette version, ne changez pas la date de votre version.

### Dates de version active
{: #active-version-dates}

Le tableau suivant indique les modifications de comportement du service pour chaque date de version. Le passage à une date de version ultérieure active toutes les modifications introduites dans les versions antérieures.

|Date de version|Récapitulatif des modifications|
|---|---|
|[`04-06-2019`](#4-june-2019)| <li>Le bogue qui amenait les demandes d'entités avec des modèles personnalisés à ignorer l'option `limit` a été corrigé.</li><li>La valeur par défaut de `limit` pour toutes les demandes d'entités est désormais 50 pour tous les modèles.</li><li>La valeur maximale de 250 entités pour `limit` a été supprimée.</li>|
|[`16-11-2018`](#16-november-2018)| <li>Système de type d'entité italien version 2.</li>|
|[`21-09-2018`](#21-september-2018)| <li>Système de type d'entité portugais version 2.</li>|
|[`16-03-2018`](#16-march-2018)| <li>Système de type d'entité français version 2.</li><li>Système de type d'entité allemand version 2.</li>| 
|[`27-02-2017`](#27-february-2017)| Version de base.| 

## Modifications
{: #changes}

### 21 juin 2019
{: #21-june-2019}

- La cote de confiance des entités est désormais renvoyée pour les demandes d'entités qui utilisent des modèles d'apprentissage automatique personnalisés.

### 4 juin 2019
{: #4-june-2019}

Les modifications suivantes sont activées lorsque vous utilisez la version datée du `2019-06-04` ou d'une date ultérieure.

- Le bogue qui amenait les demandes d'entités avec des modèles personnalisés à ignorer l'option `limit` a été corrigé.
- La valeur par défaut de `limit` pour toutes les demandes d'entités est désormais 50 pour tous les modèles.
- La valeur maximale de 250 entités pour `limit` a été supprimée.

### 29 mai 2019
{: #29-may-2019}

- Amélioration de l'analyse des sentiments en espagnol.
- Un bogue risquant d'affecter les résultats d'analyse des sentiments ciblés si la cible contient des caractères spéciaux a été corrigé.
- Les modifications suivantes sont activées pour les instances de service de Washington DC, Tokyo, Londres et Sydney:
  - L'option d'analyse des sentiments pour les demandes d'entités qui utilisent des modèles personnalisés est activée pour toutes les langues basées sur l'analyse des sentiments sauf le russe et l'arabe.


### 24 mai 2019
{: #24-may-2019}

- Amélioration des mots clés en allemand
- Editions de mises à jour de l'analyse des sentiments en anglais sur les instances de service dans tous les emplacements IBM Cloud autres que Dallas.

### 3 mai 2019
{: #3-may-2019}

- Amélioration de la détection des sentiments au niveau des documents en allemand.

### 25 avril 2019
{: #25-april-2019}

- Mentions d'entité activées pour les [modèles personnalisés](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing) basés sur des règles. Pour afficher les mentions dans vos résultats, définissez l'option `mentions` des entités sur `true`.
- Publication d'explications concernant les résultats des catégories en anglais. Pour afficher le texte approprié de la source qui a contribué aux résultats, définissez l'option `explanation` des catégories sur `true`.

### 19 mars 2019
{: #19-march-2019}

- Introduction de la prise en charge expérimentale pour les modèles de catégorie personnalisés créés avec {{site.data.keyword.knowledgestudioshort}}. Pour démarrer, voir [Création d'un modèle de catégorie personnalisé](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-create-categories-model)
- Amélioration des mots clés et des concepts en espagnol.

### 10 janvier 2019
{: #10-january-2019}

- Les demandes de **création de liste de modèles** et de **suppression de modèle** qui n'incluent pas de paramètre de date de version renvoient désormais des erreurs `400` et non des réponses indiquant que la demande a abouti.
- Amélioration des performances d'entité pour les langues autres que l'anglais.

### 14 décembre 2018
{: #14-december-2018}

- Vous pouvez désormais créer des instances de service {{site.data.keyword.nlushort}} à l'emplacement IBM Cloud de Londres.
- Ajout de la prise en charge des relations en portugais.
- Ajout de la prise en charge des relations en italien.
- Ajout d'un paramètre `limit` pour les demandes de catégories qui contrôle le nombre de catégories renvoyées (10 au maximum).
- Amélioration de la précision pour le sentiment en japonais et en allemand.

### 6 décembre 2018
{: #6-december-2018}

- Amélioration de la précision pour les catégories, les entités et les mots clés en italien.

### 27 novembre 2018
{: #27-november-2018}

- Amélioration de la qualité des résultats des mots clés pour les données entrées en anglais, français, japonais et en portugais.
- Les mêmes mots clés mais dans lesquels les minuscules et les majuscules sont utilisées différemment s'affichent désormais dans les résultats de la même manière.
- La méthode **Get models** renvoie désormais des zones supplémentaires que vous pouvez utiliser pour gérer des modèles personnalisés dans plusieurs déploiements.
  - `version` : chaîne de version fournie par l'utilisateur provenant de {{site.data.keyword.knowledgestudioshort}}
  - `version_description` : description fournie par l'utilisateur de cette version provenant de {{site.data.keyword.knowledgestudioshort}} (par exemple, modifications depuis la version précédente)
  - `workspace_id` : ID fourni par {{site.data.keyword.knowledgestudioshort}} qui reste constant pendant les différents déploiements à partir du même espace de travail {{site.data.keyword.knowledgestudioshort}}.
  - `created` : chaîne de date/heure qui indique le moment où le modèle a été déployé dans NLU.

### 16 novembre 2018
{: #16-november-2018}

- Publication de nouveaux algorithmes pour le sentiment et les mots clés en anglais afin d'améliorer la précision et les performances.
- Amélioration des performances et de la précision des mots clés pour les données entrées en anglais, français, japonais et portugais.
- Amélioration des performances et de la précision du sentiment en italien, notamment une meilleure précision pour les exemples de texte de grande taille.
- Correction d'un bogue qui provoquait l'apparition de texte codé en URL dans les résultats de clarification d'entité en espagnol.
- Publication d'un nouveau modèle d'entités en italien avec le dernier système de types d'entité. Pour plus d'informations sur ce système, consultez la page [Types et sous-types d'entité (Version 2)](entity-types-v2.html). Lorsque votre application est compatible avec le nouveau système de types, remplacez la valeur du paramètre de date de version dans vos demandes par `2018-11-16` afin d'utiliser le nouveau modèle.

### 9 novembre 2018
{: #9-november-2018}

- Amélioration importante en matière de précision pour les catégories de toutes les langues prises en charge

### 8 novembre 2018
{: #8-november-2018}

- Vous pouvez désormais créer des instances de service {{site.data.keyword.nlushort}} à l'emplacement IBM Cloud de Tokyo.

### 5 novembre 2018
{: #5-november-2018}

- Ajout du support des concepts en italien.

### 30 octobre 2018	
{: #30-october-2018}	

Depuis le 30 octobre 2018, les nouvelles instances de service créées dans les régions Allemagne et Sud des Etats-Unis utilisent l'[authentification IAM (Identity and Access Management)](#iam-auth-process).	

### 21 septembre 2018
{: #21-september-2018}

- Ajout de la prise en charge des concepts en français et en portugais.
- L'option de sentiment ciblé est désormais prise en charge pour les mots clés en français et en portugais.
- Amélioration des mots clés en français.
- Amélioration du sentiment en coréen.
- Amélioration du sentiment et des mots clés en portugais.
- Publication d'un nouveau modèle d'entités en portugais avec le dernier système de types d'entité. Pour plus d'informations sur ce système, consultez la page [Types et sous-types d'entité (Version 2)](entity-types-v2.html). Lorsque votre application est compatible avec le nouveau système de types, remplacez la valeur du paramètre de date de version dans vos demandes par `2018-09-21` afin d'utiliser le nouveau modèle. 

### 26 juin 2018
{: #26-june-2018}

Ajout de la prise en charge pour les mots clés et les entités en japonais.

- Pour les données entrées en japonais, les entités suivantes ne sont pas encore prises en charge :
  - Number
  - Percent
  - PhoneNumber
  - URL
- Les adresses IPv6 dans les données entrées en japonais ne sont pas encore détectables comme entités IPAddress.

### 12 juin 2018
{: #12-june-2018}

Depuis le 12 juin 2018, les nouvelles instances de service créées dans la région Est des Etats-Unis utilisent l'[authentification IAM (Identity and Access Management)](#iam-auth-process).

### 6 juin 2018
{: #06-june-2018}

- Amélioration mineures pour les résultats de catégorie en coréen

### 29 mai 2018
{: #29-may-2018}

Depuis le 29 juin 2018, les nouvelles instances de service créées dans la région Sydney utilisent l'[authentification IAM (Identity and Access Management)](#iam-auth-process).

### 9 mai 2018
{: #9-may-2018}

- Amélioration des entités en allemand.

### 4 mai 2018
{: #4-may-2018}

- Ajout de la prise en charge pour les rôles sémantiques et le sentiment en japonais.
- Amélioration des performances pour les demandes de métadonnées.
- Correction d'un bogue qui provoquait l'apparition des scores de pertinence `NAN` dans certains résultats d'entité.
- Correction d'un bogue qui provoquait la génération de codes d'erreur `400` dans les demandes de mot clé en allemand et en coréen alors que les codes d'erreur `500` étaient plus appropriés.


### 19 avril 2018
{: #19-april-2018}

- Ajout de la prise en charge des relations en italien.
- Amélioration des mots clés en allemand
- Correction d'un bogue qui provoquait le renvoi d'un texte de mention d'entité incorrect.
- Correction d'un bogue qui provoquait des résultats insuffisants pour le sentiment ciblé.
- Correction d'un bogue qui provoquait l'inclusion de caractères qui n'étaient pas encore analysés dans l'élément `analyzed_text`.


### 5 avril 2018
{: #05-april-2018}

- Amélioration de l'extraction du contenu de page Web. Si vous utilisez le paramètre `url` pour analyser des pages Web, vous pouvez obtenir de meilleurs résultats, principalement pour les pages Web qui utilisent des cadres et des cookies.
- Améliorations mineures apportées aux concepts en coréen.

### 16 mars 2018
{: #03-march-2018}

- Ajout de la prise en charge des catégories, des relations et des rôles sémantiques en allemand.
  - Un nouveau système de types de relation est utilisé pour les relations en allemand. Pour des détails, voir la page [Types de relation (version 2)](relations-v2.html).
- Amélioration des mots clés et du sentiment en allemand.
- Ajout de la prise en charge des catégories et des concepts en japonais.
- Amélioration de la détection de langue.
- Amélioration du nettoyage de page Web.
- Amélioration des modèles d'entité en français et en allemand. Les modèles utilisent un nouveau système de types d'entité. Découvrez les nouveaux types et sous-types d'entité dans la page [Types et sous-types d'entité (version 2)](entity-types-v2.html). Lorsque votre application est compatible avec le nouveau système de types, remplacez la valeur du paramètre de date de version dans vos demandes par `2018-03-16` afin d'utiliser le nouveau modèle. Vous trouverez ci-dessous les différences entre le système de types de _version 1_ et le système de types de _version 2_.
  - Nouveaux types d'entité :
    - Date
    - Duration
    - Measure
    - Money
    - Number&ast;
    - Percent&ast;
    - PhoneNumber&ast;
    - Ordinal
    - Time
    - URL&ast;
  - Types d'entité retirés :
    - Anatomy
    - Award
    - Broadcaster
    - Company
    - Crime
    - Drug
    - HealthCondition
    - Movie
    - MusicGroup
    - NaturalEvent
    - PrintMedia
    - Quantity
    - Sport
    - SportingEvent
    - TelevisionShow
    - Vehicle
  - Nouveau sous-type d'entité :
    - Quantity

&ast; Ce type d'entité n'est pas encore détectable en français.



### 25 janvier 2018
{: #25-january-2018}

- Désormais, la prise en charge des [modèles personnalisés](customizing.html) est disponible en chinois simplifié pour les entités et les relations.

### 12 janvier 2018
{: #12-january-2018}

- Ajout de la prise en charge des concepts en allemand.

### 15 décembre 2017
{: #15-december-2017}

- Désormais, la prise en charge des [modèles personnalisés](customizing.html) est disponible en néerlandais pour les entités et les relations.
- Désormais, les concepts sont pris en charge en [français](language-support.html#french).
- Le modèle de sentiment en français a été amélioré pour de meilleurs résultats.
- Le modèle de détection de langue est plus rapide et détecte davantage de langues. Pour la liste complète des langues, voir [Langues détectables](detectable-languages.html).

  Les langues suivantes ont été ajoutées à la liste :
  - Biélorusse (be)
  - Bihari (bh)
  - Maldivien (dv)
  - Galicien (gl)
  - Ganda (lg)
  - Inuktitut (iu)
  - Javanais (jv)
  - Kannada (kn)
  - Khmer (km)
  - Kinyarwanda (rw)
  - Lao (lo)
  - Malayalam (ml)
  - Marathe (mr)
  - Oriya (or)
  - Pendjabi (pa)
  - Gaélique écossais (gd)
  - Singhalais (si)
  - Tamoul (ta)
  - Télougou (te)
  - Yiddish (yi)

  Les langues suivantes ne sont plus détectées :
  - Breton (br)
  - Chamorro (ch)
  - Espéranto (eo)
  - Féroïen (po)
  - Haoussa (ha)
  - Ndébélé (nr)
  - Ojibwa (oj)

### 28 novembre 2017
{: #28-november-2017}

- **Mentions d'entité.** Obtenez les emplacements des mentions d'entité dans vos demandes `entities` en ajoutant l'option `"mentions": true`.
    
    Exemple de corps de demande `POST /analyze` :
    
    ```json
    {
      "text": "Intel planned to announce Monday a laptop-computer chip that combines an Intel processor and an AMD graphics unit.",
      "features": {
        "entities": {
          "mentions": true
        }
      }
    }
    ```
    {: codeblock}
    
    Exemple de réponse :
    
    ```json
    {
      "usage": {
        "text_units": 1,
        "text_characters": 114,
        "features": 1
      },
      "language": "en",
      "entities": [
        {
          "type": "Company",
          "text": "Intel",
          "relevance": 0.33,
          "mentions": [
            {
              "text": "Intel",
              "location": [
                0,
                5
              ]
            },
            {
              "text": "Intel",
              "location": [
                73,
                78
              ]
            }
          ],
          "disambiguation": {
            "subtype": [
              "OperatingSystemDeveloper",
              "ProcessorManufacturer",
              "SoftwareDeveloper"
            ],
            "name": "Intel",
            "dbpedia_resource": "http://dbpedia.org/resource/Intel"
          },
          "count": 2
        },
        {
          "type": "Company",
          "text": "AMD",
          "relevance": 0.33,
          "mentions": [
            {
              "text": "AMD",
              "location": [
                96,
                99
              ]
            }
          ],
          "disambiguation": {
            "subtype": [
              "ProcessorManufacturer"
            ],
            "name": "Advanced Micro Devices",
            "dbpedia_resource": "http://dbpedia.org/resource/Advanced_Micro_Devices"
          },
          "count": 1
        }
      ]
    }
    ```
    {: codeblock}
    
### 17 novembre 2017
{: #17-november-2017}

- **Désormais, les caractéristiques suivantes sont prises en charge en [coréen](language-support.html#korean)** :

    - Entités
    - Mots clés
    - Rôles sémantiques


### 30 juillet 2017
{: #30-july-2017}

- Vous pouvez contrôler les coûts à l'aide du paramètre facultatif `limit_text_characters` permettant de limiter le nombre de caractères traités. Exemple :

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

- Chaque caractère compte comme un caractère, qu'il s'agisse d'un caractère mono-octet ou multi-octet.

- Pour le décompte, 1 élément {{site.data.keyword.nlushort}} est toujours 1 caractéristique (aussi appelée enrichissement) par unité de texte. Une unité de texte correspond à 10000 caractères ou moins.

- Pour des informations de tarification détaillées, voir [{{site.data.keyword.nlushort}}](https://console.bluemix.net/catalog/services/natural-language-understanding) dans le catalogue {{site.data.keyword.cloud}}.

- En plus de l'ajout du paramètre `limit_text_characters`, les changements suivants ont été apportés aux limites de taille et à la troncature de texte :

  - Tout texte de plus de 50000 caractères sera tronqué avant son traitement. Auparavant, la troncature dépendait du nombre de kilooctets, où un kilooctet était égal à 1024 octets.

  - Un message d'information est renvoyé dans la réponse lorsqu'un texte de plus de 50000 caractères est tronqué.

  - La taille limite du texte pour les modèles personnalisés passe de 10000 caractères à 50000 caractères.

  - Des informations d'utilisation ont été ajoutées dans la réponse pour plus de clarté concernant le nombre d'éléments {{site.data.keyword.nlushort}} utilisés pour chaque demande. Exemple :

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


### 8 mai 2017
{: #8-may-2017}

- Mise à jour du modèle de score de ton et d'émotion. L'ensemble de données d'apprentissage a été étendu et l'ingénierie des caractéristiques a été modifiée. Par conséquent, le modèle présente une meilleure précision pour notre jeu de données de test.

### 27 mars 2017
{: #27-march-2017}

- Les modèles d'entité et de sentiment ont été améliorés ; ainsi, lorsque vous appelez ces caractéristiques, vous obtenez de meilleurs résultats.
- Désormais, les relations prennent en charge les modèles personnalisés {{site.data.keyword.knowledgestudioshort}} en français, allemand, italien et portugais.

### 15 mars 2017
{: #15-march-2017}

Nous avons publié des mises à jour pour le modèle de score de ton et d'émotion. L'ensemble de données d'apprentissage a été étendu et par conséquent, le modèle présente une meilleure précision pour notre jeu de données de test.

### 27 février 2017
{: #27-february-2017}

Disponibilité générale du service Natural Language Understanding.
