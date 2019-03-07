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

# Limiti di utilizzo
{: #usage-limits}

All'istanza del servizio di {{site.data.keyword.nlushort}} si applicano i seguenti limiti e le seguenti restrizioni di utilizzo.
{: shortdesc}

## Limite del testo analizzato
{: #analyzed-text}

{{site.data.keyword.nlushort}} tronca il testo analizzato che contiene più di 50.000 caratteri a singolo byte o multibyte. Per visualizzare il testo di cui si tiene conto nel calcolo di questo limite nelle tue richieste, imposta il parametro `return_analyzed_text` su `true`.

Puoi impostare un limite di caratteri inferiore con il parametro `limit_text_characters`. Se sei interessato ad analizzare solo una piccola parte del contenuto, questo può aiutarti a evitare costi eccessivi.

Oggetto parametri di esempio:
```json
{
  "url": "ibm.com",
  "limit_text_characters": 10000,
  "return_analyzed_text": true,
  "features": {
    "concepts": {}
  }
}
```

## Limite di richieste simultanee
{: #concurrent-requests}

Ogni istanza del servizio {{site.data.keyword.nlushort}} è limitata a 30 richieste simultanee. E' possibile che questo limite diminuisca per le istanze del servizio nei piani Lite e Standard quando il sistema sta riscontrando un traffico particolarmente intenso. Ad esempio, un'applicazione che fa 35 richieste simultanee da una singola istanza del servizio supererà il limite di richieste simultanee di cinque richieste e cinque di queste richieste restituiranno un errore `429: Too Many Requests`.

Per aumentare il limite di richieste simultanee, [apri un ticket di supporto](https://ibm.biz/ibmcloudsupport).

## Limite di dimensione del modello personalizzato per i piani di prezzo Lite
{: #custom-models}

Esiste un limite di dimensione per i modelli personalizzati {{site.data.keyword.knowledgestudioshort}} distribuiti nelle istanze del servizio {{site.data.keyword.nlushort}} dui piani di prezzo Lite. Per rimuovere il limite di dimensione di modello personalizzato, esegui l'upgrade della tua istanza del servizio {{site.data.keyword.nlushort}} a un piano di prezzo a pagamento. Puoi trovare le tue istanze del servizio nella {{site.data.keyword.cloud_notm}} [pagina delle risorse](https://{DomainName}/resources).

## Supporto linguistico
{: #language-support}

Si applicano differenti restrizioni relative alle lingue, a seconda di come usi il servizio. Per i dettagli, vedi la pagina [Supporto linguistico](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support) .


