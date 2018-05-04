---

copyright:
  years: 2015, 2018
lastupdated: "2018-01-16"

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

Mithilfe von [{{site.data.keyword.knowledgestudiofull}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://ibm.biz/watsonknowledgestudio) können Sie
{{site.data.keyword.nlushort}} mit angepassten Modellen erweitern, die angepasste Entitäten und Beziehungen identifizieren, die für Ihre Domäne eindeutig sind.
{: shortdesc}

## Erste Schritte mit angepassten Modellen

> Der kostenlose Plan für {{site.data.keyword.nlushort}} begrenzt die Größe und die Leistung Ihres angepassten Modells. Um ein angepasstes Modell in vollem Umfang testen zu können, müssen Sie es mit dem Standardplan von {{site.data.keyword.nlushort}} verwenden.

1. Sofern noch nicht geschehen, machen Sie die [ersten Schritte](/docs/services/natural-language-understanding/getting-started.html) mit {{site.data.keyword.nlushort}}.
1. [Greifen Sie auf {{site.data.keyword.knowledgestudioshort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top) zu und melden Sie sich über das [Online-Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://gateway.watsonplatform.net/knowledge-studio/ui/dashboard/) an.
1. Lesen Sie die {{site.data.keyword.knowledgestudioshort}} [Dokumentation](/docs/services/knowledge-studio/index.html), um zu erfahren, wie ein angepasstes Modell (Annotator) erstellt und auf {{site.data.keyword.nlushort}} bereitgestellt wird.
1. Um Ihr Modell zu verwenden, geben Sie das `Modell` an, das Sie in der Option [Entities ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#entities){: new_window} oder [Relations ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#relations){: new_window} Ihrer API-Anforderung bereitgestellt haben:
    - Beispiel für eine *parameters.json*-Datei:

        ```json
        {
          "url": "www.url.example",
          "features": {
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
        curl -X POST \
        -H "Content-Type: application/json" \
        -u "{username}":"{password}" \
        -d @parameters.json \
        "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
        ```
        {: pre}

