---

copyright:
  years: 2015, 2018
lastupdated: "2018-10-30"

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
{:download: .download}


# Analisi delle pagine web
{: #analyzing-webpages}

{{site.data.keyword.nlushort}} ti consente di analizzare il testo da pagine web in modo programmatico. Quando fornisci HTML non elaborato in un URL accessibile pubblicamente nella tua richiesta API, il servizio prova a concentrare l'analisi sul contenuto principale della pagina, come ad esempio il testo da un articolo di giornale o un post di un blog.

**Come funziona:**

1. Specifica un URL accessibile in modo pubblico con il parametro **url** o inviare un HTML non elaborato nel parametro **html**.
2. Per impostazione predefinita, il servizio [ripulisce](#webpage-cleaning) la pagina web per rimuovere il testo generalmente indesiderato, come ad esempio gli annunci pubblicitari.
3. Se specifichi una [query XPath](#xpath) con il parametro **xpath**, il servizio utilizza la query per selezionare gli elementi specifici della pagina da includere nell'analisi. Se **clean** è impostato su `false` quando usi **xpath**, verrà analizzato solo il risultato della query XPath.

## Pulitura di pagine web
{: #webpage-cleaning}

Per impostazione predefinita, il servizio "ripulisce" le pagine web prima che vengano analizzate. La pulitura di pagine web prova a rimuovere il contenuto generalmente indesiderato, come ad esempio gli annunci pubblicitari e altro testo che potrebbe interferire con l'analisi del contenuto principale della pagina.

Per disabilitare la pulitura delle pagine web, imposta il parametro **clean** su `false`. Il seguente esempio disabilita la pulitura delle pagine web.

```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data '{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver"
  "features": {
    "concepts": {}
  },
  "return_analyzed_text": true,
  "clean": false
}'
```
{: pre}


## Analisi di elementi specifici di una pagina web con XPath
{: #xpath}

Il parametro **xpath** ti consente di utilizzare una query XPath per analizzare parti specifiche di una pagina web. Per ulteriori informazioni su XPath, controlla le seguenti risorse.

  - [Esercitazione W3Schools XPath](https://www.w3schools.com/xml/xpath_intro.asp)
  - [XPath su Wikipedia](https://wikipedia.org/wiki/XPath)

La modalità di funzionamento del parametro **xpath** dipende dal valore del parametro **clean**: 

  - **clean** = `true` (valore predefinito): i risultati della query XPath saranno accodati al testo della pagina web ripulito prima che il testo combinato venga analizzato.
  - **clean** = `false`: verranno analizzati solo i risultati della query XPath.

### Inclusione di testo da elementi specifici nell'analisi
{: #analyze-cleaned-and-xpath}

Per impostazione predefinita, il parametro **clean** è impostato su `true` e i risultati di una query XPath sono accodati al testo della pagina web ripulito dopo un carattere di nuova riga prima che il testo combinato venga analizzato. Ciò può essere utile se desideri includere elementi nell'analisi che saranno altrimenti rimossi dalla pulitura delle pagine web. Il seguente esempio utilizza il parametro **xpath** per includere il titolo e il sottotitolo della pagina di esempio nell'analisi.

**File *parameters.json* di esempio**
```json
{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver",
  "features": {
    "concepts": {}
  },
  "return_analyzed_text": true,
  "xpath": "//div[@class='wd_title wd_language_left' or @class='wd_subtitle wd_language_left']"
}
```
{: codeblock}

**Richiesta di esempio**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}


### Analisi del testo solo da elementi specifici
{: #analyze-xpath-results-only}

Per analizzare solo il risultato di una query XPath, utilizza il parametro **xpath** e imposta il parametro **clean** su `false`. Il seguente esempio analizza solo il titolo e il sottotitolo della pagina web di esempio.

**File *parameters.json* di esempio**
```json
{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver",
  "features": {
    "concepts": {}
  },
  "return_analyzed_text": true,
  "xpath": "//div[@class='wd_title wd_language_left' or @class='wd_subtitle wd_language_left']",
  "clean": false
}
```
{: codeblock}

**Richiesta di esempio**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}
