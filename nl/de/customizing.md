---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-20"

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

# Anpassen
{: #customizing}

Mithilfe von [{{site.data.keyword.knowledgestudiofull}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/services/knowledge-studio/) können Sie
{{site.data.keyword.nlushort}} mit angepassten Modellen erweitern, die angepasste Entitäten,
Beziehungen und Kategorien identifizieren, die für Ihre Domäne eindeutig sind.
{: shortdesc}

## Erste Schritte mit angepassten Modellen
{: #getting-started-with-custom-models}

> Der kostenlose Plan für {{site.data.keyword.nlushort}} begrenzt die Größe und die Leistung Ihres angepassten Modells. Um ein angepasstes Modell in vollem Umfang testen zu können, müssen Sie es mit dem Standardplan von {{site.data.keyword.nlushort}} verwenden.

1. Sofern noch nicht geschehen, machen Sie die [ersten Schritte](/docs/services/natural-language-understanding?topic=natural-language-understanding-getting-started) mit {{site.data.keyword.nlushort}}.
2. Machen Sie sich mit der [Einführung in {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#wks_tutintro) vertraut.
3. Erstellen Sie ein angepasstes Modell.
   1. Informationen zum Erstellen eines angepassten Entitäts- und Beziehungsmodells finden Sie im Abschnitt zur [Erstellung eines Modells für maschinelles Lernen](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro). 
   2. Sie können auch ein angepassten Entitätsmodell mit einem regelbasierten Modell erstellen. Details finden Sie im Abschnitt zur [Erstellung eines regelbasierten Modells](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutrule_intro).
   3. Informationen zum Erstellen eines angepassten Kategoriemodells finden Sie im Abschnitt zur [Erstellung eines angepassten Kategoriemodells](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-create-categories-model).
4. Schließlich können Sie das [Modell in {{site.data.keyword.nlushort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#wks_manlu) bereitstellen.
5. Um Ihr Modell zu verwenden, geben Sie das Modell (`model`) an, das Sie in der Option
[entities ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/natural-language-understanding#entities){: new_window},
[relations ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/natural-language-understanding#relations){: new_window} oder [categories ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/natural-language-understanding#categories){: new_window} Ihrer API-Anforderung bereitgestellt haben:
    - Beispiel für eine *parameters.json*-Datei:

        ```json
        {
          "url": "www.url.example",
          "features": {
            "categories": {
              "model": "your-model-id-here"
            },
            "entities": {
              "model": "your-model-id-here"
            },
            "relations": {
              "model": "your-model-id-here"
            }
          }
        }
        ```
        {: codeblock}

    - Beispiel für eine cURL-Anforderung:

        ```bash
        curl --user "apikey":"{apikey}" \
        "{url}/v1/analyze?version=2018-11-16" \
        --request POST \
        --header "Content-Type: application/json" \
        --data @parameters.json
        ```
        {: pre}

## Angepasstes Modell löschen
{: #deleting-a-custom-model}

Die Anzahl der angepassten Modelle, die Sie in {{site.data.keyword.nlushort}} bereitstellen, wirkt sich entsprechend Ihrem [Preisstrukturplan](https://www.ibm.com/cloud/watson-natural-language-understanding/pricing) auf Ihre {{site.data.keyword.nlushort}}-Rechnung aus. Um Gebühren für ein Modell zu vermeiden, das Sie nicht mehr verwenden, sollten Sie die [Bereitstellung des Modells mit {{site.data.keyword.knowledgestudioshort}} zurücknehmen](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#undeploy-view-model) oder das **[Modell löschen](https://{DomainName}/apidocs/natural-language-understanding#delete-model)**.

Beispiel für eine cURL-Anforderung:

```bash
curl --user "apikey":"{apikey}" \
"{url}/v1/models/{model_id}?version=2018-10-30" \
--request DELETE
```
{: pre}


## Sprachunterstützung für angepasste Modelle
{: #language-support-for-custom-models}

Prüfen Sie in den Tabellen auf der Seite [Sprachunterstützung](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support) die Angaben in der Spalte *Angepasstes Modell - Unterstützung*, um zu erfahren, welche angepassten Modelle für die einzelnen Sprachen unterstützt werden.

### Anvisierte Stimmung bei Entitäten angepasster Modelle
{: #targeted-sentiment-for-custom-entities}

Sie können (ausschließlich für Englisch) Stimmungsbewertungen für jede angepasste Modellentität abrufen, die vom Service erkannt wird, indem Sie im Entitätsobjekt die Option `sentiment: true` festlegen. Für andere Sprachen wird die anvisierte Stimmung für angepasste Modellentitäten nicht unterstützt.
