---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-08"

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

# Release notes

The following new features and changes to the service are available.
{: shortdesc}

## Service API versioning

**Current API version**: 2018-03-08

API requests require a version parameter that takes the date in the format `version=YYYY-MM-DD`. Send the version parameter with every API request.

When we change the API in a backwards-incompatible way, we release a new minor version. To take advantage of the changes in a new version, change the value of the version parameter to the new date. If you're not ready to update to that version, don't change your version date.

## Changes

### 08 March 2018
{: #03-march-2018}

- Added support for German categories.
- Added support for Japanese categories and concepts.
- Improvements for German sentiment and keywords.
- Language detection improvements.
- Improved webpage cleaning for requests that fetch content from URLs.
- An improved French entities model is now available. The model uses a new entity type system. Check out the new entity types and subtypes on the [Entity types and subtypes (v2)](entity-types-v2.html) page. When your application is compatible with the new type system, change the version date in your requests to `2018-03-08` to use the new model. The following are the differences between the `v1` type system and the `v2` type system.
  - New entity types:
    - Date
    - Duration
    - Measure
    - Money
    - Ordinal
    - Time
  - Removed entity types:
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
  - New entity subtype:
    - Quantity


### 25 January 2018
{: #25-january-2018}

- Chinese (Simplified) [custom model](customizing.html) support is now available for entities and relations.

### 12 January 2018
{: #12-january-2018}

- Added support for German concepts.

### 15 December 2017
{: #15-december-2017}

- Dutch [custom model](customizing.html) support is now available for entities and relations.
- [French language support](language-support.html#french) now includes concepts.
- The French sentiment model has been improved to deliver better results.
- The language detection model is faster and detects more languages overall. For the complete list of languages, see [Detectable languages](detectable-languages.html).

  The following languages are new additions to the list:
  - Belarusian (be)
  - Bihari (bh)
  - Dhivehi (dv)
  - Galician (gl)
  - Ganda (lg)
  - Inuktitut (iu)
  - Javanese (jv)
  - Kannada (kn)
  - Khmer (km)
  - Kinyarwanda (rw)
  - Laothian (lo)
  - Malayalam (ml)
  - Marathi (mr)
  - Oriya (or)
  - Punjabi (pa)
  - Scots Gaelic (gd)
  - Sinhalese (si)
  - Tamil (ta)
  - Telugu (te)
  - Yiddish (yi)

  The following languages are no longer detectable:
  - Breton (br)
  - Chamorro (ch)
  - Esperanto (eo)
  - Faroese (fo)
  - Hausa (ha)
  - Ndebele (nr)
  - Ojibwa (oj)

### 28 November 2017
{: #28-november-2017}

- **Entity mentions.** Get the locations of entity mentions in your `entities` requests by adding the option `"mentions": true`.
    
    Example `POST /analyze` request body:
    
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
    
    Example response:
    
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
    
### 17 November 2017
{: #17-november-2017}

- **[Korean language support](language-support.html#korean)** has expanded to include the following features:

    - Entities
    - Keywords
    - Semantic Roles


### 30 July 2017
{: #30-july-2017}

- You can control cost by using the optional `limit_text_characters` parameter to limit the number of characters that are processed. For example:

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

- Each character counts as one character, regardless of whether the character is a single-byte character or a multibyte character.

- For metering, one {{site.data.keyword.nlushort}} Item continues to be one feature (also known as an enrichment) per one text unit. One text unit is 10,000 characters or less.

- For detailed pricing information, see [{{site.data.keyword.nlushort}}](https://console.bluemix.net/catalog/services/natural-language-understanding) in the {{site.data.keyword.cloud}} Catalog.

- In addition to adding the `limit_text_characters` parameter, the following changes were made to text size limits and truncation:

  - All text greater than 50,000 characters will be truncated before processing. Previously, truncation was based on kilobytes, where one kilobyte equaled 1024 bytes.

  - An informational message is returned in the response when text beyond 50,000 characters is truncated.

  - Text limit size for custom models has been bumped from 10,000 characters to 50,000 characters.

  - Usage information is added to the response for clarity around number of {{site.data.keyword.nlushort}} Items used for each request. For example:

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


### 8 May 2017
{: #8-may-2017}

- Updated the emotion tone score model. The training dataset was expanded and feature engineering was altered and as a result, the model has higher precision on our benchmark dataset.

### 27 March 2017
{: #27-march-2017}

- The entity and sentiment models have been improved, which means that when you call those features, you'll get better results.
- Relations now supports {{site.data.keyword.knowledgestudioshort}} custom models in French, German, Italian, and Portuguese.

### 15 March 2017
{: #15-march-2017}

We released updates to the emotion tone score model. The training dataset was expanded and as a result, the model has higher precision on our benchmark dataset.

### 27 February 2017
{: #27-february-2017}

The Natural Language Understanding service is now GA.

