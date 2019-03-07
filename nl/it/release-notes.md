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

# Note sulla release
{: #release-notes}

Sono disponibili le seguenti nuove funzioni e modifiche per il servizio.
{: shortdesc}

## Nuovo processo di autenticazione API
{: #iam-auth-process }

Il 30 ottobre 2018, le ubicazioni Dallas (Stati Uniti Sud) e Francoforte sono passate all'utilizzo dell'autenticazione IAM (Identity and Access Management) basata sui token. (Per ulteriori informazioni, vedi il documento relativo all'[autenticazione con i token IAM ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/watson/getting-started-iam.html)).
{: important}

Il servizio {{site.data.keyword.nlushort}} ha un nuovo processo di autenticazione API per le istanze del servizio ospitate nelle seguenti ubicazioni:

- Dallas a partire dal 30 ottobre 2018
- Francoforte a partire dal 30 ottobre 2018
- Londra
- Sydney a partire dal 29 maggio 2018
- Tokyo
- Washington, DC a partire dal 12 giugno 2018

{{site.data.keyword.cloud_notm}} sta eseguendo la migrazione all'autenticazione IAM (Identity and Access Management) basata sui token. Con alcune istanze del servizi, esegui l'autenticazione presso l'API utilizzando IAM.

- Con le *nuove* istanze del servizio che crei nelle ubicazioni in coincidenza o successivamente alle date elencate, esegui l'autenticazione presso l'API utilizzando IAM. Puoi passare un token bearer in un'intestazione Authentication o una chiave API. I token supportano le richieste autenticazione senza l'integrazione di credenziali di servizio in ogni chiamata. Le chiavi API utilizzano l'autenticazione di base. Qui puoi trovare ulteriori informazioni su [IAM](/docs/services/watson/getting-started-iam.html).

    Quando utilizzi uno qualsiasi degli SDK Watson, puoi passare la chiave API e lasciare che SDK gestisca il ciclo di vita dei token. Per ulteriori informazioni ed esempi, vedi [Autenticazione ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/natural-language-understanding/#authentication){: new_window} nella guida di riferimento API.
- Per le istanze del servizio _esistenti_ che hai creato prima della data indicata, puoi continuare ad eseguire l'autenticazione fornendo il nome utente e la password per l'istanza del servizio. Prima o poi dovrai eseguire la migrazione di queste istanze del servizio all'autenticazione IAM. Verranno forniti degli aggiornamenti sul processo e le date di migrazione. Per ulteriori informazioni sulla migrazione, vedi [Migrazione di istanze del servizio Cloud Foundry a un gruppo di risorse](/docs/resources/instance_migration.html).

Per appurare quale sia l'autenticazione da utilizzare, visualizza le credenziali del servizio facendo clic sull'istanza del servizio nel [Dashboard ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/dashboard/apps?watson){: new_window}.


## Controllo versioni della API di servizio
{: #service-api-versioning}

**Versione API corrente**: 16-11-2018

Le richieste API richiedono un parametro di versione che assume la data nel formato `version=YYYY-MM-DD`. Invia il parametro di versione con ogni richiesta API.

Quando modifichiamo l'API in un modo non compatibile con le versioni precedenti, rilasciamo una nuova versione secondaria. Per avvalerti delle modifiche in una nuova versione, modifica il valore del parametro di versione nella nuova data. Se non sei pronto ad aggiornare la versione in oggetto, non modificare la data della versione.

## Modifiche
{: #changes}

### 10 gennaio 2019
{: #10-january-2019}

- Le richieste **Elencare i modelli** ed **Eliminare un modello** che non includono un parametro di data di versione ora restituiscono degli errori `400` invece di risposte di esito positivo.
- Prestazioni delle entità migliorate per le lingue diverse dall'inglese

### 14 dicembre 2018
{: #14-december-2018}

- Puoi ora creare delle istanze del servizio nell'ubicazione Londra di IBM Cloud.{{site.data.keyword.nlushort}}.
- È stato aggiunto il supporto per le relazioni in lingua portoghese.
- È stato aggiunto il supporto per le relazioni in lingua italiana.
- È stato aggiunto un parametro `limit` per le richieste di categorie che controlla il numero di categorie restituito fino a un massimo di 10.
- Accuratezza migliorata per il parere per il giapponese e il tedesco.

### 6 dicembre 2018
{: #6-december-2018}

- Accuratezza migliorata per le categorie, le parole chiave, le entità e le categorie in lingua italiana.

### 27 novembre 2018
{: #27-november-2018}

- Qualità migliorata dei risultati delle password per l'input in inglese, francese, giapponese e portoghese.
- Le parole chiave con maiuscole/minuscole differenti sono ora presenti nei risultati come la stessa parola chiave.
- Il metodo **Elencare i modelli** ora restituisce dei campi aggiuntivi che puoi utilizzare per gestire i modelli personalizzati in diverse distribuzioni.
  - `version`:la stringa di versione fornita dall'utente da {{site.data.keyword.knowledgestudioshort}}
  - `version_description`: la descrizione fornita dall'utente di questa versione da {{site.data.keyword.knowledgestudioshort}} (ad esempio, cosa è cambiato rispetto alla versione precedente)
  - `workspace_id`: un ID fornito da {{site.data.keyword.knowledgestudioshort}} che rimane costante su ripetute distribuzioni dallo stesso spazio di lavoro {{site.data.keyword.knowledgestudioshort}}.
  - `create`:una stringa di data/ora che indica quando il modello è stato distribuito a NLU.

### 16 novembre 2018
{: #16-november-2018}

- Sono stati rilasciati dei nuovi algoritmi per le parole chiave e il parere in lingua inglese per migliorare l'accuratezza e le prestazioni.
- Sono state migliorate l'accuratezza e le prestazioni delle parole chiave per l'input in inglese, francese, giapponese e portoghese.
- Sono state migliorate l'accuratezza e e le prestazioni in lingua italiana, compresa una migliore accuratezza per degli esempi di testo di grandi dimensioni.
- È stato corretto un bug che causava la visualizzazione di testo con codifica URL nei risultati di disambiguazione delle entità in lingua spagnola.
- È stato rilasciato un nuovo modello di entità in lingua italiana con il sistema di tipi di entità più recente. Puoi saperne di più sul sistema di tipi più recente nella pagina [Tipi e sottotipi di entità (versione 2)](entity-types-v2.html). Quando la tua applicazione è compatibile con il nuovo sistema di tipi, modifica il parametro di data della versione nelle tue richieste in `2018-11-16` per utilizzare il nuovo modello. 

### 9 novembre 2018
{: #9-november-2018}

- Notevole miglioramento nell'accuratezza per le categorie in tutte le lingue supportate.

### 8 novembre 2018
{: #8-november-2018}

- Puoi ora creare delle istanze del servizio nell'ubicazione Tokyo di IBM Cloud.{{site.data.keyword.nlushort}}.

### 5 novembre 2018
{: #5-november-2018}

- È stato aggiunto il supporto per i concetti in lingua italiana.

### 30 ottobre 2018	
{: #30-october-2018}	

A partire dal 30 ottobre 2018, le nuove istanze del servizio create nelle regioni Germania e Stati Uniti Sud utilizzano l'[autenticazione IAM (Identity and Access Management)](#iam-auth-process).	

### 21 settembre 2018
{: #21-september-2018}

- È stato aggiunto il supporto per le relazioni in lingua francese e i concetti in lingua portoghese.
- L'opzione di parere mirato è ora supportata per le parole chiave in francese e portoghese.
- Sono stati migliorati le parole chiave per la lingua francese.
- È stato migliorato il parere in lingua coreana.
- Sono stati migliorati le parole chiave e il parere in lingua portoghese.
- È stato rilasciato un nuovo modello di entità in lingua portoghese con il sistema di tipi di entità più recente. Puoi saperne di più sul sistema di tipi più recente nella pagina [Tipi e sottotipi di entità (versione 2)](entity-types-v2.html). Quando la tua applicazione è compatibile con il nuovo sistema di tipi, modifica il parametro di data della versione nelle tue richieste in `2018-09-21` per utilizzare il nuovo modello. 

### 26 giugno 2018
{: #26-june-2018}

È stato aggiunto il supporto per le entità e le parole chiave in lingua giapponese.

- Per l'input in lingua giapponese, le seguenti entità non sono ancora supportate:
  - Number
  - Percent
  - PhoneNumber
  - URL
- Gli indirizzi IPv6 nell'input in lingua giapponese non sono ancora rilevabili come entità IPAddress.

### 12 giugno 2018
{: #12-june-2018}

A partire dal 12 giugno 2018, le nuove istanze del servizio create nella regione Stati Uniti Est utilizzando l'[autenticazione IAM (Identity and Access Management)](#iam-auth-process).

### 6 giugno 2018
{: #06-june-2018}

- Miglioramenti secondari per i risultati delle categorie in lingua coreana.

### 29 maggio 2018
{: #29-may-2018}

A partire dal 29 maggio 2018, le nuove istanze del servizio create nella regione Sydney utilizzano l'[autenticazione IAM (Identity and Access Management)](#iam-auth-process).

### 9 maggio 2018
{: #9-may-2018}

- Sono state migliorate le entità in lingua tedesca.

### 4 maggio 2018
{: #4-may-2018}

- È stato aggiunto il supporto per il parere e le regole semantiche in lingua giapponese.
- Sono state migliorate le prestazioni per le richieste di metadati.
- È stato corretto un bug che causava la visualizzazione di risultai della rilevanza `NAN` in alcuni risultati delle entità.
- È stato corretto un bug che ha restituito dei codici di errore `400` nelle richieste di parole chiave in lingua tedesca e coreana laddove dei codici di errore `500` sarebbero stati più appropriati.


### 19 aprile 2018
{: #19-april-2018}

- È stato aggiunto il supporto per le relazioni in lingua giapponese.
- Sono stati migliorati le parole chiave per la lingua tedesca.
- È stato corretto un bug che causava la restituzione di testo di citazione dell'entità non corretto.
- È stato corretto un bug che poteva causare degli scarsi risultati per il parere mirato.
- È stato corretto un bug a causa del quale il `analyzed_text` restituito includeva dei caratteri che non venivano analizzati.


### 5 aprile 2018
{: #05-april-2018}

- È stato migliorato il recupero del contenuto delle pagine web. Se utilizzi il parametro `url` per analizzare le pagine web, vedrai dei risultati migliori, in particolar modo dalle pagine web che utilizzano i set di frame e i cookie.
- Miglioramenti secondari per i concetti in lingua coreana.

### 16 marzo 2018
{: #03-march-2018}

- È stato aggiunto il supporto per le categorie, le relazioni e i ruoli semantici per la lingua tedesca.
  - Per le relazioni del tedesco è stato utilizzato un nuovo sistema di tipi di relazioni. Per visualizzare i dettagli, vedi [Tipi di relazione (versione 2)](relations-v2.html).
- Sono stati migliorati le parole chiave e il parere per la lingua tedesca.
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
- Il modello di parere per la lingua francese è stato migliorato per offrire risultati migliori.
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

- I modelli di entità e parere sono stati migliorati; questo significa che, quando richiami queste funzioni, otterrai dei risultati migliori.
- Le relazioni ora supportano i modelli personalizzati {{site.data.keyword.knowledgestudioshort}} in francese, tedesco, italiano e portoghese.

### 15 marzo 2017
{: #15-march-2017}

Abbiamo rilasciato degli aggiornamenti al modello di punteggio del tono dell'emozione. Il dataset di formazione è stato ampliato e, di conseguenza, il modello ha una precisione più elevata sul nostro dataset di benchmark.

### 27 febbraio 2017
{: #27-february-2017}

Il servizio Natural Language Understanding è ora GA.
