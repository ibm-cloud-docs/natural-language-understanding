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

# Personalizzazione
{: #customizing}

Con [{{site.data.keyword.knowledgestudiofull}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/services/knowledge-studio/), puoi estendere {{site.data.keyword.nlushort}} con i modelli personalizzati che identificano entità, relazioni e categorie personalizzati univoci per il tuo dominio.
{: shortdesc}

## Introduzione ai modelli personalizzati
{: #getting-started-with-custom-models}

> Il piano {{site.data.keyword.nlushort}} gratuito limita la dimensione e le prestazioni del tuo modello personalizzato. Per testare un modello personalizzato alla sua piena estensione, dovrai utilizzarlo con il piano {{site.data.keyword.nlushort}} standard.

1. Se non lo hai già fatto, [inizia a lavorare](/docs/services/natural-language-understanding?topic=natural-language-understanding-getting-started) con {{site.data.keyword.nlushort}}.
2. [Introduzione a {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutintro#wks_tutintro).
3. Crea un modello personalizzato.
   1. Per creare un modello di entità e relazioni personalizzato, vedi [Creazione di un modello di machine learning](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutml_intro) 
   2. Puoi anche creare un modello di entità personalizzato con un modello basato sulle regole. Per i dettagli, vedi [Creazione di un modello basato sulle regole](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-wks_tutrule_intro).
   3. Per creare un modello di categorie personalizzato, vedi [Creazione di un modello di categorie personalizzato](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-create-categories-model).
4. [Distribuzione del tuo modello a {{site.data.keyword.nlushort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#wks_manlu)
5. Per utilizzare il tuo modello, specifica il modello (`model`) che hai distribuito nelle opzioni di
[entità ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/natural-language-understanding#entities){: new_window},
[relazioni ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/natural-language-understanding#relations){: new_window} o [categorie ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/apidocs/natural-language-understanding#categories){: new_window} della tua richiesta API:
    - File *parameters.json* di esempio:

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

    - Richiesta curl di esempio:

        ```bash
        curl --user "apikey":"{apikey}" \
        "{url}/v1/analyze?version=2018-11-16" \
        --request POST \
        --header "Content-Type: application/json" \
        --data @parameters.json
        ```
        {: pre}

## Eliminazione di un modello personalizzato
{: #deleting-a-custom-model}

Il numero di modelli personalizzati che distribuisci a {{site.data.keyword.nlushort}} influisce sulla tua fattura {{site.data.keyword.nlushort}} in vase al tuo [piano di prezzo](https://www.ibm.com/cloud/watson-natural-language-understanding/pricing). Per evitare addebiti per un modello che non utilizzi più, [annulla la distribuzione del modello con {{site.data.keyword.knowledgestudioshort}}](/docs/services/watson-knowledge-studio?topic=watson-knowledge-studio-publish-ml#undeploy-view-model) oppure annulla la distribuzione del modello con il metodo **[Eliminare un modello](https://{DomainName}/apidocs/natural-language-understanding#delete-model)**.

Richiesta curl di esempio:

```bash
curl --user "apikey":"{apikey}" \
"{url}/v1/models/{model_id}?version=2018-10-30" \
--request DELETE
```
{: pre}


## Supporto linguistico per i modelli personalizzati
{: #language-support-for-custom-models}

Controlla le colonne *Custom model support* nelle tabelle nella pagina [Supporto linguistico](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support) per visualizzare i modelli personalizzati supportati per ciascuna lingua.

### Parere mirato per le entità modello personalizzate
{: #targeted-sentiment-for-custom-entities}

Solo per la lingua inglese, puoi ottenere dei punteggi di parere per ogni entità di modello personalizzata rilevata dal servizio impostando l'opzione `sentiment: true` nell'oggetto delle entità. Nessun'altra lingua supporta il parere mirato per le entità di modello personalizzate.
