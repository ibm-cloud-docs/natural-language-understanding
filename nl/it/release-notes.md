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

# Note sulla release

Sono disponibili le seguenti nuove funzioni e modifiche per il servizio.
{: shortdesc}

## Controllo versioni della API di servizio

**Versione API corrente**: 2018-03-16

Le richieste API richiedono un parametro di versione che assume la data nel formato `version=YYYY-MM-DD`. Invia il parametro di versione con ogni richiesta API.

Quando modifichiamo l'API in un modo non compatibile con le versioni precedenti, rilasciamo una nuova versione secondaria. Per avvalerti delle modifiche in una nuova versione, modifica il valore del parametro di versione nella nuova data. Se non sei pronto ad aggiornare la versione in oggetto, non modificare la data della versione.

## Modifiche

### 16 marzo 2018
{: #03-march-2018}

- È stato aggiunto il supporto per le categorie, le relazioni e i ruoli semantici per la lingua tedesca.
  - Per le relazioni del tedesco è stato utilizzato un nuovo sistema di tipi di relazione. Per visualizzare i dettagli, vedi [Tipi di relazione (versione 2)](relations-v2.html).
- Sono stati migliorati le parole chiave e le valutazioni per la lingua tedesca.
- È stato aggiunto il supporto per le categorie e i concetti per la lingua giapponese.
- Sono stati apportati dei miglioramenti al rilevamento della lingua.
- È stata migliorata la pulitura delle pagine web.
- Sono stati migliorati i modelli di entità per le lingue francese e tedesca. I modelli utilizzano un nuovo sistema di tipi di entità. Controlla i nuovi tipi e sottotipi di entità nella pagina [Tipi e sottotipi di entità (versione 2)](entity-types-v2.html). Quando la tua applicazione è compatibile con il nuovo sistema di tipi, modifica il parametro di data della versione nelle tue richieste in `2018-03-16` per utilizzare il nuovo modello. Sono qui di seguito indicate le differenze tra il sistema di tipi _versione 1_ e il sistema di tipi _versione 2_.
  - Nuovi tipi di entità:
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
  - Tipi di entità rimossi:
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
  - Nuovo sottotipo di entità:
    - Quantity

&ast; Questo tipo di entità non è ancora rilevabile in testo in francese.



### 25 gennaio 2018
{: #25-january-2018}

- Il supporto del [modello personalizzato](customizing.html) per il cinese (semplificato) è ora disponibile per entità e relazioni.

### 12 gennaio 2018
{: #12-january-2018}

- È stato aggiunto il supporto per i concetti per la lingua tedesca.

### 15 dicembre 2017
{: #15-december-2017}

- Il supporto del [modello personalizzato](customizing.html) per l'olandese è ora disponibile per entità e relazioni.
- [Il supporto della lingua francese](language-support.html#french) ora include i concetti.
- Il modello di valutazione per la lingua francese è stato migliorato per offrire risultati migliori.
- Il modello di rilevamento della lingua è più rapido e rileva più lingue, complessivamente. Per l'elenco completo di lingue, vedi [Lingue rilevabili](detectable-languages.html).

  Le seguenti lingue sono delle nuove aggiunte all'elenco:
  - Bielorusso (be)
  - Bihari (bh)
  - Dhivehi (dv)
  - Gallego (gl)
  - Ganda (lg)
  - Inuktitut (iu)
  - Giavanese (jv)
  - Kannada (kn)
  - Khmer (km)
  - Kinyarwanda (rw)
  - Laotiano (lo)
  - Malayalam (ml)
  - Marathi (mr)
  - Oriya (or)
  - Punjabi (pa)
  - Gaelico scozzese (gd)
  - Singalese (si)
  - Tamil (ta)
  - Telugu (te)
  - Yiddish (yi)

  Le seguenti lingue non sono più rilevabili:
  - Bretone (br)
  - Chamorro (ch)
  - Esperanto (eo)
  - Faroese (fo)
  - Hausa (ha)
  - Ndebele (nr)
  - Ojibwa (oj)

### 28 novembre 2017
{: #28-november-2017}

- **Citazioni delle entità.** Ottieni le ubicazioni delle citazioni di entità nelle tue richieste `entities` aggiungendo l'opzione `"mentions": true`.
    
    Corpo della richiesta `POST /analyze` di esempio:
    
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
    
    Risposta di esempio:
    
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

- Il **[supporto per la lingua coreana](language-support.html#korean)** è stato ampliato per includere le seguenti funzioni:

    - Entità
    - Parole chiave
    - Ruoli semantici


### 30 luglio 2017
{: #30-july-2017}

- Puoi controllare il costo utilizzando il parametro `limit_text_characters` facoltativo per limitare il numero di caratteri elaborati. Ad esempio:

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

- Ogni carattere conta come un carattere, indipendentemente dal fatto che sia a byte singolo o multibyte.

- Per la misurazione, un singolo elemento {{site.data.keyword.nlushort}} continua a essere una singola funzione (nota anche come arricchimento) per una singola unità di testo. Una singola unità di testo è 10.000 caratteri o meno.

- Per informazioni dettagliate sui prezzi, vedi [{{site.data.keyword.nlushort}}](https://console.bluemix.net/catalog/services/natural-language-understanding) nel catalogo {{site.data.keyword.cloud}}.

- Oltre all'aggiunta del parametro `limit_text_characters`, sono state apportate le seguenti modifiche ai limiti di dimensione e al troncamento del testo:

  - Tutto il testo superiore ai 50.000 caratteri verrà troncato prima dell'elaborazione. In precedenza, il troncamento era basato sui kilobyte, dove un kilobyte equivaleva a 1024 byte.

  - Nella risposta viene restituito un messaggio informativo quando il testo oltre i 50.000 caratteri viene troncato.

  - La dimensione del limite di testo per i modelli personalizzati è stata portata da 10.000 caratteri a 50.000 caratteri.

  - Alla risposta sono state aggiunte le informazioni sull'utilizzo per rendere chiaro il numero di elementi {{site.data.keyword.nlushort}} utilizzato per ciascuna richiesta. Ad esempio:

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


### 8 maggio 2017
{: #8-may-2017}

- È stato aggiornato il modello del punteggio del tono dell'emozione. Il dataset di formazione è stato ampliato e i meccanismi delle funzioni sono stati modificati; di conseguenza, il modello ha una precisione più elevata sul nostro dataset di benchmark.

### 27 marzo 2017
{: #27-march-2017}

- I modelli di entità e valutazione sono stati migliorati; questo significa che, quando richiami queste funzioni, otterrai dei risultati migliori.
- Le relazioni ora supportano i modelli personalizzati {{site.data.keyword.knowledgestudioshort}} in francese, tedesco, italiano e portoghese.

### 15 marzo 2017
{: #15-march-2017}

Abbiamo rilasciato degli aggiornamenti al modello di punteggio del tono dell'emozione. Il dataset di formazione è stato ampliato e, di conseguenza, il modello ha una precisione più elevata sul nostro dataset di benchmark.

### 27 febbraio 2017
{: #27-february-2017}

Il servizio Natural Language Understanding è ora GA.

