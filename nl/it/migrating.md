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

# Migrazione da AlchemyLanguage

A partire dal **7 aprile 2017**, non sarà più possibile creare una nuova istanza di AlchemyAPI su {{site.data.keyword.cloud}}. Le istanze del servizio esistenti verranno supportate fino al **7 marzo 2018**. Per continuare a utilizzare le funzioni di {{site.data.keyword.alchemylanguageshort}}, dovrai migrare il tuo codice a {{site.data.keyword.nlushort}}.
{: shortdesc}

{{site.data.keyword.nlushort}} offre un modello di prezzi più economico e una API consolidata che è molto più facile da utilizzare. Le funzioni esistenti sono ottimizzate per renderle più utili e di valore per le esigenze dei nostri clienti. {{site.data.keyword.nlushort}} facilita la gestione del tuo marchio, la raccolta di BI (Business Intelligence) e il raggruppamento di corrispondenze, ad-tech e consigli.

## Panoramica delle principali modifiche

- Nuova sintassi di richieste API: invia richieste all'endpoint `/analyze`
- Nuova struttura di risposta (il codice che analizza l'output {{site.data.keyword.alchemylanguageshort}} non funziona per l'output {{site.data.keyword.nlushort}})
- JSON è il solo formato di output
- L'*estrazione di testo* è abilitata impostando il parametro `return_analyzed_text` su `true`
- I *microformati* non sono supportati
- L'*estrazione di dati* non è supportata (la *data di pubblicazione* è ancora supportata nella funzione *Metadati*)
- Le opzioni "quotations" per le entità non sono supportate
- "knowledgeGraph" non è supportato per concetti, parole chiave o entità
- Le query di vincoli visuali (utilizzate con il parametro `cquery`) non sono supportate
- Le callback JSONP non sono supportate
- *Relazioni con tipi* da {{site.data.keyword.alchemylanguageshort}} diventa *Relazioni* in {{site.data.keyword.nlushort}}
- *Relazioni* da {{site.data.keyword.alchemylanguageshort}} diventa *Regole semantiche* in {{site.data.keyword.nlushort}}
- I tipi di entità sono stati modificati (vedi i nuovi tipi di entità [qui](/docs/services/natural-language-understanding/entity-types.html))
- Le seguenti parole erano scritte in modo errato nei risultati della tassonomia AlchemyLanguage. Sono state corrette nei risultati delle categorie Natural Language Understanding.
  - `offence` -> `offense`
  - `civl` -> `civil`
  - `phyiscs` -> `physics`

## Passi di migrazione

1. [Introduzione](/docs/services/natural-language-understanding/getting-started.html) al servizio {{site.data.keyword.nlushort}}.
1. Se utilizzi i modelli personalizzati da Watson Knowledge Studio, ridistribuiscili alla tua nuova istanza del servizio {{site.data.keyword.nlushort}}. Attieniti alla procedura per la distribuzione di [strumenti di aggiunta di annotazioni basati sulle regole](/docs/services/knowledge-studio/rule-annotator-model-use.html#wks_rule_publish) o [strumenti di aggiunta di annotazioni di apprendimento automatico](/docs/services/knowledge-studio/publish-ml.html#wks_manlu) e seleziona il servizio {{site.data.keyword.nlushort}} come destinazione per la distribuzione.
1. Migra il tuo codice.
    Se usi gli SDK Watson Developer Cloud per interagire con {{site.data.keyword.alchemylanguageshort}}, devi modificare il tuo codice SDK. Fai clic sui seguenti link per visualizzare degli esempi SDK {{site.data.keyword.nlushort}} in GitHub:
    - [Node.js ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/watson-developer-cloud/node-sdk#natural-language-understanding){: new_window}
    - [Python ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/watson-developer-cloud/python-sdk/blob/master/examples/natural_language_understanding_v1.py){: new_window}
    - [Swift ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/watson-developer-cloud/swift-sdk#natural-language-understanding){: new_window}

Inoltre, devi riconfigurare l'eventuale logica nella tua applicazione che prevede l'output delle richieste {{site.data.keyword.alchemylanguageshort}}. Assicurati che il tuo codice sia regolato per elaborare la nuova struttura di output di {{site.data.keyword.nlushort}}.

### Metodi AlchemyLanguage e funzioni Natural Language Understanding corrispondenti
Le richieste {{site.data.keyword.alchemylanguageshort}} sono associate all'endpoint {{site.data.keyword.nlushort}} `/analyze`. Le richieste a `/analyze` sono simili alle richieste di chiamata combinata (Combined Call) da {{site.data.keyword.alchemylanguageshort}}, ma la sintassi è diversa e puoi specificare opzioni come `limit` singolarmente per ciascuna funzione. Le operazioni POST a `/analyze` accettano un corpo JSON che contiene l'input e i parametri per la richiesta e le operazioni GET a `/analyze` accettano i parametri di query analoghi alla sintassi dei parametri JSON.

| Metodo {{site.data.keyword.alchemylanguageshort}} | Endpoint {{site.data.keyword.alchemylanguageshort}} | Funzione {{site.data.keyword.nlushort}} |
|------------------------|--------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| Autori | `/text/TextGetAuthors`<br/>`/url/URLGetAuthors` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadata</a> |
| Concetti | `/html/HTMLGetRankedConcepts`<br/>`/text/TextGetRankedConcepts`<br/>`/url/URLGetRankedConcepts` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#concepts">Concepts</a> |
| Estrazione data | `/html/HTMLExtractDates`<br/>`/text/TextExtractDates`<br/>`/url/URLExtractDates` | Non supportato |
| Analisi emozioni | `/html/HTMLGetEmotion`<br/>`/text/TextGetEmotion`<br/>`/url/URLGetEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">Emotion</a> |
| Emozione mirata | `/html/HTMLGetTargetedEmotion`<br/>`/text/TextGetTargetedEmotion`<br/>`/url/URLGetTargetedEmotion` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#emotion">Emotion</a> (utilizza con l'opzione `targets`) |
| Entità | `/html/HTMLGetRankedNamedEntities`<br/>`/text/TextGetRankedNamedEntities`<br/>`/url/URLGetRankedNamedEntities` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#entities">Entities</a> |
| Rilevamento feed | `/html/HTMLGetFeedLinks`<br/>`/url/URLGetFeedLinks` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadata</a> |
| Parole chiave | `/html/HTMLGetRankedKeywords`<br/>`/text/TextGetRankedKeywords`<br/>`/url/URLGetRankedKeywords` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#keywords">Keywords</a> |
| Rilevamento lingua | `/html/HTMLGetLanguage`<br/>`/text/TextGetLanguage`<br/>`/url/URLGetLanguage` | Il rilevamento della lingua di base è gratuito in ogni richiesta. I metadati della lingua diversi dal codice ISO non sono restituiti. |
| Microformati | `/html/HTMLGetMicroformatData`<br/>`/url/URLGetMicroformatData` | Non supportato |
| Data di pubblicazione | `/html/HTMLGetPubDate`<br/>`/url/URLGetPubDate` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadata</a> |
| Relazioni | `/html/HTMLGetRelations`<br/>`/text/TextGetRelations`<br/>`/url/URLGetRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#semantic-roles">Semantic Roles</a> |
| Relazioni con tipo | `/html/HTMLGetTypedRelations`<br/>`/text/TextGetTypedRelations`<br/>`/url/URLGetTypedRelations` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#relations">Relations</a> |
| Analisi delle valutazioni | `/html/HTMLGetTextSentiment`<br/>`/text/TextGetTextSentiment`<br/>`/url/URLGetTextSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">Sentiment</a> |
| Valutazione mirata | `/html/HTMLGetTargetedSentiment`<br/>`/text/TextGetTargetedSentiment`<br/>`/url/URLGetTargetedSentiment` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#sentiment">Sentiment</a> (utilizza l'opzione `targets`) |
| Tassonomia | `/html/HTMLGetRankedTaxonomy`<br/>`/text/TextGetRankedTaxonomy`<br/>`/url/URLGetRankedTaxonomy` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#categories">Categories</a> |
| Testo (pulito) | `/html/HTMLGetText`<br/>`/url/URLGetText` | Imposta `return_analyzed_text` su `true` in qualsiasi richiesta valida a `/analyze` |
| Testo (non elaborato) | `/html/HTMLGetRawText`<br/>`/url/URLGetRawText` | Imposta `return_analyzed_text` su `true` e `clean` su `false` in qualsiasi richiesta valida a `/analyze` |
| Estrazione di titoli | `/html/HTMLGetTitle`<br/>`/url/URLGetTitle` | <a href="https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/index.html#metadata">Metadata</a> |

Quindi, se stai facendo questa chiamata combinata:

```bash
curl -X POST \
-d "outputMode=json" \
-d "extract=entities,keywords" \
-d "sentiment=1" \
-d "limit=1" \
-d "url=https://www.ibm.com/us-en/" \
"https://gateway.watsonplatform.net/calls/url/URLGetCombinedData?apikey=$API_KEY"
```
{: pre}

si presenterebbe ora così in {{site.data.keyword.nlushort}}:

```bash
curl -X POST \
-H "Content-Type: application/json" \
-u "{username}":"{password}" \
-d @parameters.json "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
```
{: pre}

Con questo parameters.json:

```json
{
  "url": "https://www.ibm.com/us-en/",
  "features": {
    "entities": {
      "sentiment": true,
      "limit": 1
    },
    "keywords": {
      "sentiment": true,
      "limit": 1
    }
  }
}
```
{: codeblock}

## Armonizzazione delle entità

Se stai usando i modelli pubblici dal metodo TypedRelations di {{site.data.keyword.alchemylanguageshort}}, dovrai modificare l'eventuale codice che prevede i tipi di entità da questi modelli. La seguente tabella mostra l'associazione dei tipi di entità TypedRelations ai tipi di entità {{site.data.keyword.nlushort}}.

| Tipo di entità TypedRelations | Tipo di entità di relazioni {{site.data.keyword.nlushort}}|
|----------------------------|------------------------------------------------------|
| AGE | Age |
| ANIMAL | Animal |
| AWARD | Award |
| CARDINAL | Cardinal |
| DATE | Date |
| DEGREE | Degree |
| DISEASE | HealthCondition |
| DURATION | Duration |
| EMAIL | EmailAddress |
| EVENT | Event |
| FACILITY | Facility |
| FOOD | Food |
| GEOLOGICALOBJ | GeographicFeature |
| GPE | GeopoliticalEntity |
| LAW | Law |
| LOCATION | Location |
| MEASURE | Measure |
| MONEY | Money |
| ORDINAL | Ordinal |
| ORGAN | Anatomy |
| ORGANIZATION | Organization |
| PEOPLE | Person |
| PERCENT | Percent |
| PERSONPEOPLE | Person |
| PERSON | Person |
| PHONE | Phone |
| PLANT | Plant |
| PRODUCT | Product |
| SUBSTANCE | Substance |
| TICKER | Ticker |
| TIME | Time |
| TITLEWORK | TitleWork |
| VEHICLE | Vehicle |
| WEAPON | Weapon |
| WEATHER | Weather |
| WEB | Web |
| EVENT_AWARD | Award |
| EVENT_BUSINESS | EventBusiness |
| EVENT_COMMUNICATION | EventCommunication |
| EVENT_CRIME | Crime |
| EVENT_CUSTODY | EventCustody |
| EVENT_DEMONSTRATION | EventDemonstration |
| EVENT_DISASTER | NaturalEvent |
| EVENT_EDUCATION | EventEducation |
| EVENT_ELECTION | EventElection |
| EVENT_LEGAL | EventLegal |
| EVENT_LEGISLATION | EventLegislation |
| EVENT_MEETING | EventMeeting |
| EVENT_GATHERING | EventGathering |
| EVENT_PERFORMANCE | EventPerformance |
| EVENT_PERSONNEL | EventPersonnel |
| EVENT_SPORTS | SportingEvent |
| EVENT_VIOLENCE | EventViolence |
| EVENT | Event |
