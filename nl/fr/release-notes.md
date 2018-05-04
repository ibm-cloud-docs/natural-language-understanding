---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-16"

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

Les nouvelles caractéristiques et les modifications apportées au service
ci-après sont disponibles.
{: shortdesc}

## Gestion des versions d'API de service 

**Version d'API en cours** : 16 mars 2018 

Les demandes d'API requièrent un paramètre de version qui admet la date au format `version=AAAA-MM-JJ`. Envoyez le paramètre de version avec chaque demande d'API.

Lorsque nous changeons l'API et que celle-ci n'est plus compatible avec les versions antérieures, nous publions une nouvelle version mineure. Pour bénéficier des changements apportés dans une nouvelle version, remplacez la valeur du paramètre de version par la nouvelle date. Si vous n'êtes pas prêt à effectuer la mise à jour vers cette version, ne changez pas la date de votre version. 

## Modifications

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

