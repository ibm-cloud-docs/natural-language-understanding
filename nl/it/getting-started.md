---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:go: .ph data-hd-programlang='go'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# Esercitazione introduttiva
{: #getting-started}

Questa breve esercitazione introduce l'API {{site.data.keyword.nlushort}} con richieste di esempi e collegamenti a risorse aggiunitve.
{:shortdesc}

## Prima di iniziare
{: #before-you-begin}

- {: hide-dashboard} Crea un'istanza del servizio:
    1.  Vai alla pagina [{{site.data.keyword.nlushort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/catalog/services/natural-language-understanding){: new_window} nel catalogo {{site.data.keyword.Bluemix_notm}}.
    2.  Registrati per un account {{site.data.keyword.Bluemix_notm}} gratuito o accedi.
    3.  Fai clic su **Crea**.
- Copia le credenziali per eseguire l'autenticazione presso la tua istanza del servizio:
    1.  Nella pagina **Gestisci**, fai clic su **Mostra** per visualizzare le tue credenziali.
    2.  Copia i valori di `Chiave API` e `URL`.
- Assicurati di avere il comando `curl`:
    - Gli esempi utilizzano il comando `curl` per richiamare i metodi dell'interfaccia HTTP. Installa la versione per il tuo sistema operativo da [curl.haxx.se ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://curl.haxx.se/){: new_window}. Installa la versione che supporta il protocollo SSL (Secure Sockets Layer). Assicurati di includere il file binario installato nella tua variabile di ambiente `PATH`.

Questa esercitazione ti mostra come utilizzare l'API {{site.data.keyword.nlushort}} da un'interfaccia riga di comando. Per scaricare le librerie client per diversi linguaggi di programmazione, controlla gli [SDK Watson](/docs/services/natural-language-understanding?topic=watson-using-sdks#using-sdks).
{:tip}

## Passo 1: Analizza una pagina web
{: #analyze-sample}

Esegui il seguente comando per analizzare una pagina web per ottenere il parere, i concetti, le categorie, le entità e le parole chiave. <span class="hide-dashboard">Sostituisci `{apikey}` e `{url}` con le tue credenziali di servizio.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--header "Content-Type: application/json" \
--data '{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver",
  "features": {
    "sentiment": {},
    "categories": {},
    "concepts": {},
    "entities": {},
    "keywords": {}
  }
}'
```
{: pre}

Il prossimo passo illustra come specificare le opzioni che personalizzano l'aalisi per ciascuna funzione.

## Passo 2: Analizza le frasi e le parole chiave di destinazione
{: #analyze-phrase}

{{site.data.keyword.nlushort}} può analizzare le frasi di destinazione nel contesto del testo circostante per risultati di pareri ed emozioni focalizzati. L'opzione **targets** per il parere nel seguente esempio indica al servizio di creare le destinazioni "apples", "oranges" e "broccoli". Poiché "apples" e "oranges" si trovano nel testo, per tali destinazioni vengono restituiti dei punteggi di parere.

Puoi anche ottenere dei risultati di parere ed emozione per le entità e le parole chiave rilevate nel tuo testo. Nell'esempio, l'opzione **emotion** per le parole chiave indica al servizio di analizzare ciascuna parola chiave rilevata per i risultati di emozione.

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--request POST \
--header "Content-Type: application/json" \
--data '{
  "text": "I love apples! I do not like oranges.",
  "features": {
    "sentiment": {
      "targets": [
        "apples",
        "oranges",
        "broccoli"
      ]
    },
    "keywords": {
      "emotion": true
    }
  }
}'
```
{: pre}

## Passi successivi
{: #next-steps}

- Visualizza la [Guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/natural-language-understanding){: new_window}.
- Impara a identificare [entità e relazioni personalizzate](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing).
