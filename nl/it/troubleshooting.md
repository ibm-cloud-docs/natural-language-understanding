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
{:download: .download}

# Risoluzione dei problemi
{: #troubleshooting}

Se hai problemi con {{site.data.keyword.nlushort}}, i seguenti suggerimenti per la risoluzione dei problemi potrebbero essere di aiuto.
{:shortdesc}

## Le entità e i tipi di entità delle relazioni non sono congruenti
{: #inconsistent-entity-types}

I sistemi di tipo di entità per le entità e le funzioni delle relazioni non sono sempre congruenti. Per alcune lingue e date della versione, i risultati conterranno dei tipi di entità diversi dai tipi di entità che compaiono nei risultati delle entità. Per ulteriori dettagli, vedi [Tipi e sottotipi di entità](/docs/services/natural-language-understanding?topic=natural-language-understanding-entity-type-systems) e [Tipi di relazione](/docs/services/natural-language-understanding?topic=natural-language-understanding-relation-type-systems). 

## Rilevamento della lingua non corretto
{: #incorrect-language-detection}

Il rilevamento della lingua automatico potrebbe non essere accurato per il testo che contiene meno di 100 caratteri. Se il servizio non rileva la lingua corretta del tuo testo, puoi  [sovrascrivere il rilevamento della lingua automatico ](/docs/services/natural-language-understanding?topic=natural-language-understanding-overriding-language-detection).

## Troppe richieste
{: #too-many requests}

Se stai vedendo un errore "429: Too many requests", è probabile che la tua istanza del servizio stia raggiungendo il limite di richieste simultanee. Per ulteriori informazioni, visualizza la pagina [Limiti di utilizzo](/docs/services/natural-language-understanding?topic=natural-language-understanding-usage-limits#concurrent-requests).

## Risultati imprevisti dall'analisi della pagina web
{: #unexpected-webpage-results}

In alcuni casi, l'analisi di una pagina web potrebbe restituire dei risultati imprevisti. Per investigare, prova a impostare il parametro **return_analyzed_text** su `true` per ispezionare il testo effettivo oggetto dell'analisi nella tua richiesta. Nei casi in cui la [pulitura delle pagine web](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#webpage-cleaning) non rimuove abbastanza testo indesiderato, considera l'utilizzo del parametro [**xpath**](/docs/services/natural-language-understanding?topic=natural-language-understanding-analyzing-webpages#xpath) per concentrare l'analisi su elementi specifici della pagina.

## Spiegazioni per specifici risultati
{: #explanations-for-results}

{{site.data.keyword.nlushort}} non fornisce strumenti di diagnostica per spiegare perché una specifica richiesta restituisce uno specifico risultato. Il servizio è progettato per fornire dei risultati accurati per il numero massimo di esempio di testo possibile ma, a causa della natura dei modelli di machine learning da noi utilizzati, non c'è alcuna garanzia che uno specifico risultato sembri corretto da una prospettiva umana.






