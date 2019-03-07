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


# Webseiten analysieren
{: #analyzing-webpages}

{{site.data.keyword.nlushort}} ermöglicht Ihnen, Text von Webseiten programmgesteuert zu analysieren. Wenn Sie in Ihrer API-Anforderung unformatierte HTML oder eine öffentlich zugängliche URL angeben, versucht der Service, die Analyse schwerpunktmäßig auf den Hauptinhalt der Seite zu richten, wie zum Beispiel auf den Text aus einem Nachrichtenartikel oder Blogbeitrag. 

**Funktionsweise:**

1. Geben Sie eine öffentlich zugängliche URL mit dem Parameter **url** an oder senden Sie unformatierte HTML im Parameter **html**.
2. Der Service [bereinigt](#webpage-cleaning) die Webseite standardmäßig, um allgemein unerwünschten Text wie etwa Werbung zu entfernen. 
3. Wenn Sie eine [XPath-Abfrage](#xpath) mit dem Parameter **xpath** angeben, wählt der Service anhand der Abfrage bestimmte Elemente der Seite aus und bindet diese in die Analyse ein. Wenn bei Verwendung von **xpath** für **clean** der Wert `false` festgelegt ist, wird nur das Ergebnis der XPath-Abfrage analysiert. 

## Webseitenbereinigung
{: #webpage-cleaning}

Standardmäßig 'bereinigt' der Service Webseiten, bevor sie analysiert werden. Bei der Webseitenbereinigung wird versucht, allgemein unerwünschte Inhalte wie etwa Werbung oder sonstigen Text zu entfernen, der die Analyse des Seitenhauptinhalts beeinträchtigen könnte. 

Die Webseitenbereinigung kann inaktiviert werden, indem Sie für den Parameter **clean** den Wert `false` festlegen. Im folgenden Beispiel wird die Webseitenbereinigung inaktiviert. 

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


## Bestimmte Elemente einer Webseite mit XPath analysieren
{: #xpath}

Der Parameter **xpath** ermöglicht die Verwendung einer XPath-Abfrage, um bestimmte Teile einer Webseite zu analysieren. Wenn Sie mehr über XPath erfahren wollen, prüfen Sie den Inhalt der folgenden Ressourcen. 

  - [Lernprogramm zu XPath von W3Schools](https://www.w3schools.com/xml/xpath_intro.asp)
  - [XPath in Wikipedia](https://wikipedia.org/wiki/XPath)

Das Verhalten des Parameters **xpath** hängt von dem Wert des Parameters **clean** ab:  

  - **clean** = `true` (Standardeinstellung): Die Ergebnisse der XPath-Abfrage werden an den bereinigten Webseitentext angehängt, bevor der kombinierte Text analysiert wird.
  - **clean** = `false`: Es werden nur die Ergebnisse der XPath-Abfrage analysiert.

### Text aus bestimmten Elementen in die Analyse einbeziehen
{: #analyze-cleaned-and-xpath}

Standardmäßig ist für den Parameter **clean** der Wert `true` festgelegt und die Ergebnisse einer XPath-Abfrage werden nach einem Zeilenvorschubzeichen an den bereinigten Webseitentext angehängt, bevor der kombinierte Text analysiert wird. Dies kann nützlich sein, wenn Sie Elemente in die Analyse einbeziehen wollen, die andernfalls im Rahmen der Webseitenbereinigung entfernt würden. Im folgenden Beispiel wird der Parameter **xpath** verwendet, um den Titel und Untertitel der Beispielwebseite in die Analyse einzubeziehen.

**Beispiel für eine *parameters.json*-Datei**
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

**Beispielanforderung**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}


### Nur Text aus bestimmten Elementen analysieren
{: #analyze-xpath-results-only}

Wenn nur das Ergebnis einer XPath-Abfrage analysiert werden soll, verwenden Sie den Parameter **xpath** und legen Sie für den Parameter **clean** den Wert `false` fest. Bei dem folgenden Beispiel wird nur der Titel und der Untertitel der Beispielwebseite analysiert. 

**Beispiel für eine *parameters.json*-Datei**
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

**Beispielanforderung**
```bash
curl --user "apikey:{apikey}" \
"{url}/v1/analyze?version=2018-09-21" \
--request POST \
--header "Content-Type: application/json" \
--data @parameters.json
```
{: pre}
