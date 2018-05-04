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

# Releaseinformationen

Folgende neue Funktionen und Änderungen am Service sind verfügbar.
{: shortdesc}

## Service-API-Versionierung

**Aktuelle API-Version**: 2018-03-16

API-Anforderungen erfordern einen Versionsparameter, der das Datum im Format `version=JJJJ-MM-TT` erfasst. Senden Sie mit jeder API-Anforderung auch den Versionsparameter.

Wenn wir die API auf abwärts-inkompatible Art ändern, geben wir eine neue Unterversion heraus. Um die Änderungen der neuen Version nutzen zu können, ändern Sie den Wert des Versionsparameters in das neue Datum. Wenn Sie zur Aktualisierung auf diese Version nicht bereit sind, ändern Sie Ihr Versionsdatum nicht.

## Änderungen

### 16. März 2018
{: #03-march-2018}

- Unterstützung für deutsche Kategorien, Beziehungen und semantische Rollen hinzugefügt.
  - Für deutsche Beziehungen wird ein neues System von Beziehungstypen verwendet. Details hierzu finden Sie auf der Seite [Beziehungstypen (Version 2)](relations-v2.html).
- Deutsche Schlüsselwörter und Stimmung verbessert.
- Unterstützung für japanische Kategorien und Konzepte hinzugefügt.
- Verbesserungen an der Spracherkennung.
- Verbesserte Webseitenbereinigung.
- Verbesserungen an den französischen und deutschen Entitätsmodellen. Die Modelle verwenden ein neues System von Entitätstypen. Informationen über die neuen Entitätstypen und -untertypen finden Sie auf der Seite [Entitätstypen und -untertypen (Version 2)](entity-types-v2.html). Wenn Ihre Anwendung mit dem neuen Typsystem kompatibel ist, ändern Sie den Parameter für das Versionsdatum in Ihren Anforderungen in `2018-03-16`, sodass das neue Modell verwendet wird. Nachstehend sind die Unterschiede zwischen dem Typsystem _Version 1_ und dem Typsystem _Version 2_ aufgeführt.
  - Neue Entitätstypen:
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
  - Entfernte Entitätstypen:
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
  - Neuer Entitäts-Untertyp:
    - Quantity

&ast; Dieser Entitätstyp wird in französischem Text noch nicht erkannt.



### 25. Januar 2018
{: #25-january-2018}

- Unterstützung für chinesische (vereinfacht) [angepasste Modelle](customizing.html) ist jetzt für Entitäten und Beziehungen verfügbar.

### 12. Januar 2018
{: #12-january-2018}

- Unterstützung für deutsche Konzepte hinzugefügt.

### 15. Dezember 2017
{: #15-december-2017}

- Unterstützung für niederländische [angepasste Modelle](customizing.html) ist jetzt für Entitäten und Beziehungen verfügbar.
- Die [französische Sprachunterstützung](language-support.html#french) enthält jetzt Konzepte.
- Das französische Stimmungsmodell wurde verbessert und liefert jetzt bessere Ergebnisse.
- Das Spracherkennungsmodell ist schneller und erkennt insgesamt mehr Sprachen. Eine vollständige Liste der Sprachen finden Sie unter [Erkannte Sprachen](detectable-languages.html).

  Folgende Sprachen wurden der Liste neu hinzugefügt:
  - Weißrussisch (be)
  - Biharisch (bh)
  - Dhivehi (dv)
  - Galizisch (gl)
  - Ganda (lg)
  - Inuktitut (iu)
  - Javanisch (jv)
  - Kannada (kn)
  - Khmer (km)
  - Kinyarwanda (rw)
  - Laotisch (lo)
  - Malajalam (ml)
  - Marathi (mr)
  - Orija (or)
  - Pundjabisch (pa)
  - Schottisches Gälisch (gd)
  - Singhalesisch (si)
  - Tamilisch (ta)
  - Telugu (te)
  - Jiddisch (yi)

  Folgende Sprachen werden nicht mehr erkannt:
  - Bretonisch (br)
  - Chamorro (ch)
  - Esperanto (eo)
  - Färöisch (fo)
  - Haussa (ha)
  - Ndebele (nr)
  - Ojibwa (oj)

### 28. November 2017
{: #28-november-2017}

- **Entitätserwähnungen.** Sie können die Positionen der Entitätserwähnungen in Ihren `entities`-Anforderungen abrufen, indem Sie die Option `"mentions": true` hinzufügen.
    
    Beispiel für einen `POST /analyze`-Anforderungshauptteil:
    
    ```json
    {
      "text": "Intel hat für Montag die Ankündigung eines Laptop-Computerchips geplant, der einen Intel-Prozessor und eine AMD-Grafikeinheit kombiniert.",
      "features": {
        "entities": {
          "mentions": true
        }
      }
    }
    ```
    {: codeblock}
    
    Beispielantwort:
    
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
    
### 17. November 2017
{: #17-november-2017}

- **Die [Sprachunterstützung für Koreanisch](language-support.html#korean)** wurde erweitert und enthält jetzt die folgenden Features:

    - Entities
    - Keywords
    - Semantic Roles


### 30. Juli 2017
{: #30-july-2017}

- Sie können die Kosten kontrollieren, indem Sie den optionalen Parameter `limit_text_characters` zur Begrenzung der Anzahl zu verarbeitender Zeichen verwenden. Beispiel:

```
{
  "text": "Die Vereinigten Staaten von Amerika, kurz auch Vereinigte Staaten (USA) genannt, häufig auch verkürzt zu Amerika, sind eine föderale Republik, die aus 50 Bundesstaaten, einem Bundesdistrikt (der Hauptstadt Washington, D.C.), fünf größeren Territorien und etlichen Inselterritorien besteht. Die 48 zusammenhängenden Continental United States und Alaska liegen in Nordamerika, zwischen Kanada und Mexico. Der Staat Alaska liegt im Nordwesten des nordamerikanischen Kontinents, grenzt im Osten an Kanada und im Westen an die Beringstraße, die vor Russland liegt.",
  "features": {
    "entities": {}
  },
  "limit_text_characters": 50,
  "return_analyzed_text": true
}
```

- Jedes Zeichen gilt als genau ein Zeichen, unabhängig davon, ob es ein Einzelbyte- oder ein Mehrbytezeichen ist.

- Für Messungen ist ein {{site.data.keyword.nlushort}}-Element weiterhin ein Feature (auch als Aufbereitung bezeichnet) pro Texteinheit. Eine Texteinheit besteht aus maximal 10.000 Zeichen.

- Ausführliche Preisinformationen finden Sie im {{site.data.keyword.cloud}}-Katalog unter [{{site.data.keyword.nlushort}}](https://console.bluemix.net/catalog/services/natural-language-understanding).

- Zusätzlich zur Hinzufügung des Parameters `limit_text_characters` wurden folgende Änderungen an den Textumfangbegrenzungen und Abschneidungen vorgenommen:

  - Aller Text, der mehr als 50.000 Zeichen enthält, wird vor der Verarbeitung abgeschnitten. Bisher beruhte die Abschneidung auf Kilobyte, wobei ein Kilobyte 1024 Byte entsprach.

  - Wird ein über 50.000 Zeichen hinausgehender Text abgeschnitten, so wird in der Antwort eine Informationsnachricht zurückgegeben.

  - Die Textbegrenzung für angepasste Modelle wurde von 10.000 auf 50.000 Zeichen erhöht.

  - Zwecks Übersichtlichkeit werden um die Zahl der {{site.data.keyword.nlushort}}-Elemente, die für jede Anforderung verwendet werden, Nutzungsinformationen zur Antwort hinzugefügt. Beispiel:

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


### 8. Mai 2017
{: #8-may-2017}

- Das Emotion/Ton-Score-Modell wurde aktualisiert. Der Trainingsdatensatz wurde erweitert und die Feature-Entwicklung geändert. Im Ergebnis verfügt das Modell über höhere Präzision in unserem Benchmark-Datensatz.

### 27. März 2017
{: #27-march-2017}

- Das Entitäts- und das Stimmungsmodell wurden verbessert, sodass Sie beim Aufruf dieser Features jetzt bessere Ergebnisse erhalten.
- 'Relations' unterstützt jetzt angepasste {{site.data.keyword.knowledgestudioshort}}-Modelle auf Französisch, Deutsch, Italienisch und Portugiesisch.

### 15. März 2017
{: #15-march-2017}

Es wurden Aktualisierungen am Emotion/Ton-Score-Modell freigegeben. Der Trainingsdatensatz wurde erweitert. Im Ergebnis verfügt das Modell über höhere Präzision in unserem Benchmark-Datensatz.

### 27. Februar 2017
{: #27-february-2017}

Der Service 'Natural Language Understanding' ist jetzt allgemein verfügbar (GA).

