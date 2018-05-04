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

# Personalizzazione

Con [{{site.data.keyword.knowledgestudiofull}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://ibm.biz/watsonknowledgestudio), puoi estendere {{site.data.keyword.nlushort}} con i modelli personalizzati che identificano entità e relazioni personalizzati univoci per il tuo dominio.
{: shortdesc}

## Introduzione ai modelli personalizzati

> Il piano {{site.data.keyword.nlushort}} gratuito limita la dimensione e le prestazioni del tuo modello personalizzato. Per testare un modello personalizzato alla sua piena estensione, dovrai utilizzarlo con il piano {{site.data.keyword.nlushort}} standard.

1. Se non lo hai già fatto, [inizia a lavorare](/docs/services/natural-language-understanding/getting-started.html) con {{site.data.keyword.nlushort}}.
1. [Ottieni l'accesso a {{site.data.keyword.knowledgestudioshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/us-en/marketplace/supervised-machine-learning/purchase#product-header-top) e accedi tramite il dashboard online[ ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://gateway.watsonplatform.net/knowledge-studio/ui/dashboard/).
1. Visualizza la {{site.data.keyword.knowledgestudioshort}}documentazione di [](/docs/services/knowledge-studio/index.html) per apprendere a creare un modello personalizzato (strumento di aggiunta di annotazioni) e distribuirlo a {{site.data.keyword.nlushort}}.
1. Per utilizzare il tuo modello, specifica il modello (`model`) che hai distribuito nelle opzioni di
[entità ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#entities){: new_window} o
[relazioni ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/#relations){: new_window} della tua richiesta API:
    - File *parameters.json* di esempio:

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
    
    - Richiesta curl di esempio:

        ```bash
        curl -X POST \
        -H "Content-Type: application/json" \
        -u "{username}":"{password}" \
        -d @parameters.json \
        "https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27"
        ```
        {: pre}

