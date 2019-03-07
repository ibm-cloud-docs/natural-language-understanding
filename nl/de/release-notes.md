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

# Releaseinformationen
{: #release-notes}

Folgende neue Funktionen und Änderungen am Service sind verfügbar.
{: shortdesc}

## Neuer Authentifizierungsprozess für die API
{: #iam-auth-process }

Am 30. Oktober 2018 hat die Überführung der Standorte 'Dallas' (Vereinigte Staaten - Süden) und Frankfurt (Deutschland) zur Verwendung des tokenbasierten Identitäts- und Zugriffsmanagements mit Identity and Access Management (IAM) stattgefunden. (Weitere Informationen finden Sie in [Mit IAM-Token authentifizieren ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/watson/getting-started-iam.html).)
{: important}

Der {{site.data.keyword.nlushort}}-Service verfügt für Serviceinstanzen, die an den folgenden Standorten per Hosting bereitgestellt werden, über einen neuen API-Authentifizierungsprozess: 

- Dallas, ab 30. Oktober 2018
- Frankfurt, ab 30. Oktober 2018
- London
- Sydney, ab 29. Mai 2018
- Tokio
- Washington DC, ab 12. Juni 2018

{{site.data.keyword.cloud_notm}} wird auf das tokenbasierte Identitäts- und Zugriffsmanagement mit Identity and Access Management (IAM) migriert. Bei manchen Serviceinstanzen erfolgt Ihre Authentifizierung gegenüber der API unter Verwendung von IAM.

- Bei *neuen* Serviceinstanzen, die Sie an oder nach den aufgelisteten Daten an den Standorten erstellen, authentifizieren Sie sich mit IAM bei der API. Sie können entweder ein Trägertoken in einem Berechtigungsheader oder einen API-Schlüssel übergeben. Token unterstützen authentifizierte Anforderungen, ohne Serviceberechtigungsnachweise in jeden Aufruf einzubetten. API-Schlüssel verwenden die Basisauthentifizierung. Weitere Informationen finden Sie in [IAM](/docs/services/watson/getting-started-iam.html).

Wenn Sie eines der Watson-SDKs verwenden, können Sie den API-Schlüssel übergeben und dem SDK die Verwaltung des Lebenszyklus für die Token überlassen. Weitere Informationen und Beispiele finden Sie in der API-Referenz unter [Authentifizierung ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/natural-language-understanding/#authentication){: new_window}.
- Bei _vorhandenen_ Serviceinstanzen, die vor dem angegebenen Datum erstellt wurden, erfolgt die Authentifizierung weiterhin durch Angabe des Benutzernamens und des entsprechenden Kennworts für die Serviceinstanz. Irgendwann werden Sie diese Serviceinstanzen ebenfalls auf die Authentifizierung mit IAM migrieren müssen. Es werden Aktualisierungen zum Migrationsprozess und den Daten bereitgestellt. Weitere Informationen zur Migration enthält [Cloud Foundry-Serviceinstanzen in eine Ressourcengruppe migrieren](/docs/resources/instance_migration.html). 

Um herauszufinden, welche Authentifizierung verwendet werden soll, Seiten Sie die Berechtigungsnachweise an, indem Sie im [Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/dashboard/apps?watson){: new_window} auf die Serviceinstanz klicken. 


## Service-API-Versionierung
{: #service-api-versioning}

**Aktuelle API-Version**: 2018-11-16

API-Anforderungen erfordern einen Versionsparameter, der das Datum im Format `version=JJJJ-MM-TT` erfasst. Senden Sie mit jeder API-Anforderung auch den Versionsparameter.

Wenn wir die API auf abwärts-inkompatible Art ändern, geben wir eine neue Unterversion heraus. Um die Änderungen der neuen Version nutzen zu können, ändern Sie den Wert des Versionsparameters in das neue Datum. Wenn Sie zur Aktualisierung auf diese Version nicht bereit sind, ändern Sie Ihr Versionsdatum nicht.

## Änderungen
{: #changes}

### 10. Januar 2019
{: #10-january-2019}

- Für Anforderungen vom Typ **List models** und **Delete model** zum Auflisten bzw. Löschen von Modellen, bei denen kein Parameter für das Versionsdatum enthalten ist, werden jetzt an Stelle erfolgreicher Antworten Fehler vom Typ `400` zurückgegeben.
- Die Leistung von Entitäten für andere Sprachen als Englisch wurde verbessert.

### 14. Dezember 2018
{: #14-december-2018}

- Es ist jetzt möglich, {{site.data.keyword.nlushort}}-Serviceinstanzen am IBM Cloud-Standort London zu erstellen.
- Unterstützung für portugiesische Beziehungen hinzugefügt.
- Unterstützung für italienische Beziehungen hinzugefügt.
- Es wurde ein Parameter `limit` für Kategorieanforderungen hinzugefügt, der die Anzahl der zurückgegebenen Kategorien steuert und auf maximal 10 begrenzt.
- Verbesserte Genauigkeit für die japanische und die deutsche Stimmung.

### 6. Dezember 2018
{: #6-december-2018}

- Verbesserte Genauigkeit für italienische Kategorien, Schlüsselwörter, Entitäten und Kategorien.

### 27. November 2018
{: #27-november-2018}

- Verbesserte Qualität der Ergebnisse für Schlüsselwörter für die Eingabe in Englisch, Französisch, Japanisch und Portugiesisch. 
- Schlüsselwörter mit unterschiedlicher Groß-/Kleinschreibung werden in den Ergebnissen nun als dasselbe Schlüsselwort aufgeführt. 
- Die Methode **Get models** zum Abrufen von Modellen gibt nun zusätzliche Felder zurück, mit denen Sie angepasste Modelle über mehrere Bereitstellungen hinweg verwalten können. 
  - `version`: vom Benutzer bereitgestellte Versionszeichenfolge aus {{site.data.keyword.knowledgestudioshort}}
  - `version_description`: vom Benutzer bereitgestellte Beschreibung dieser Version aus {{site.data.keyword.knowledgestudioshort}} (zum Beispiel eine Beschreibung der Änderungen seit der Vorgängerversion)
  - `workspace_id`: Eine von {{site.data.keyword.knowledgestudioshort}} gelieferte ID, die über wiederholte Bereitstellungen aus demselben {{site.data.keyword.knowledgestudioshort}}-Arbeitsbereich konstant bleibt.
  - `created`: Zeichenfolge für Datum/Uhrzeit, die angibt, wann das Modell in NLU bereitgestellt wurde.

### 16. November 2018
{: #16-november-2018}

- Neue Algorithmen für englische Schlüsselwörter und Stimmungen zur Verbesserung von Genauigkeit und Leistung freigegeben.
- Verbesserte Genauigkeit und Leistung von Schlüsselwörtern für die Eingabe in Englisch, Französisch, Japanisch und Portugiesisch.
- Verbesserte Genauigkeit und Leistung der Stimmung in Italienisch, einschließlich einer besseren Genauigkeit bei umfangreichen Textbeispielen. 
- Es wurde ein Fehler behoben, der bewirkte, dass URL-kodierter Text in den Begriffsklärungsergebnissen der spanischen Entität angezeigt wurde. 
- Es wurde ein neues italienisches Entitätsmodell mit dem neuesten Entitätstypsystem freigegeben. Mehr zum neuesten Typsystem erfahren Sie auf der Seite [Entitätstypen und -untertypen (Version 2)](entity-types-v2.html). Wenn Ihre Anwendung mit dem neuen Typsystem kompatibel ist, ändern Sie den Parameter für das Versionsdatum in Ihren Anforderungen in `2018-11-16`, sodass das neue Modell verwendet wird. 

### 9. November 2018
{: #9-november-2018}

- Deutliche Verbesserung bei der Genauigkeit für Kategorien in allen unterstützten Sprachen.

### 8. November 2018
{: #8-november-2018}

- Es ist jetzt möglich, {{site.data.keyword.nlushort}}-Serviceinstanzen am IBM Cloud-Standort Tokio zu erstellen.

### 5. November 2018
{: #5-november-2018}

- Unterstützung für italienische Konzepte hinzugefügt.

### 30. Oktober 2018	
{: #30-october-2018}	

Mit Wirkung ab 30. Oktober 2018 verwenden neue Serviceinstanzen, die in den Regionen 'Deutschland' und 'Vereinigte Staaten (Süden)' erstellt werden, die [Authentifizierung mit Identity and Access Management (IAM)](#iam-auth-process).	

### 21. September 2018
{: #21-september-2018}

- Unterstützung für französische Beziehungen und portugiesische Konzepte hinzugefügt.
- Die Option für die anvisierte Stimmung wird jetzt für französische und portugiesische Schlüsselwörter unterstützt.
- Französische Schlüsselwörter verbessert.
- Koreanische Stimmung verbessert.
- Portugiesische Schlüsselwörter und Stimmung verbessert.
- Es wurde ein neues portugiesisches Entitätsmodell mit dem neuesten Entitätstypsystem freigegeben. Mehr zum neuesten Typsystem erfahren Sie auf der Seite [Entitätstypen und -untertypen (Version 2)](entity-types-v2.html). Wenn Ihre Anwendung mit dem neuen Typsystem kompatibel ist, ändern Sie den Parameter für das Versionsdatum in Ihren Anforderungen in `2018-09-21`, sodass das neue Modell verwendet wird.  

### 26. Juni 2018
{: #26-june-2018}

Unterstützung für japanische Entitäten und Schlüsselwörter hinzugefügt.

- Für die japanische Eingabe werden die folgenden Entitäten noch nicht unterstützt: 
  - Number
  - Percent
  - PhoneNumber
  - URL
- IPv6-Adressen in japanischen Eingaben sind derzeit noch nicht als Entitäten vom Typ 'IPAddress' erkennbar. 

### 12. Juni 2018
{: #12-june-2018}

Mit Wirkung ab 12. Juni 2018 verwenden neue Serviceinstanzen, die in der Region 'Vereinigte Staaten (Osten)' erstellt werden, die [Authentifizierung mit Identity and Access Management (IAM)](#iam-auth-process).

### 6. Juni 2018
{: #06-june-2018}

- Geringfügige Verbesserungen der koreanischen Ergebnisse für Kategorien.

### 29. Mai 2018
{: #29-may-2018}

Mit Wirkung ab 29. Juni 2018 verwenden neue Serviceinstanzen, die in der Region 'Sydney' erstellt werden, die [Authentifizierung mit Identity and Access Management (IAM)](#iam-auth-process).

### 9. Mai 2018
{: #9-may-2018}

- Deutsche Entitäten verbessert.

### 4. Mai 2018
{: #4-may-2018}

- Unterstützung für japanische Stimmung und semantische Rollen hinzugefügt.
- Verbesserte Leistung für Metadatenanforderungen.
- Es wurde ein Fehler behoben, der bewirkte, dass in den Ergebnissen mancher Entitäten die Relevanzbewertung `NAN` zurückgegeben wurde.
- Es wurde ein Fehler behoben, der bewirkte, dass in deutschen und koreanischen Schlüsselwortanforderungen der Fehlercode `400` zurückgegeben wurde, obwohl der Fehlercode `500` angemessener gewesen wäre.


### 19. April 2018
{: #19-april-2018}

- Unterstützung für japanische Beziehungen hinzugefügt.
- Deutsche Schlüsselwörter verbessert.
- Es wurde ein Fehler behoben, durch den falscher Text mit Entitätserwähnung zurückgegeben wurde.
- Es wurde ein Fehler behoben, der zu schlechten Ergebnissen bei anvisierter Stimmung führen könnte.
- Es wurde ein Fehler behoben, durch den der zurückgegebene `analyzed_text` Zeichen enthielt, die nicht analysiert worden sind.


### 5. April 2018
{: #05-april-2018}

- Das Abrufen des Inhalts von Webseiten wurde verbessert. Wenn zum Analysieren von Webseiten der Parameter `url` verwendet wird, werden bessere Ergebnisse angezeigt, insbesondere bei Webseiten, die Framesets und Cookies verwenden.
- Geringfügige Verbesserungen an koreanischen Konzepten.

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
  - Neuer Entitätsuntertyp:
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
