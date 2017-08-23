---

copyright:
  years: 2015, 2017
lastupdated: "2017-06-09"

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

# Esercitazione introduttiva
In questa breve esercitazione, introduciamo {{site.data.keyword.nlushort}} analizzando la valutazione di un testo di esempio.
{:shortdesc}

## Passo 1: Effettua l'accesso, crea l'istanza del servizio e ottieni le tue credenziali
{: #create-service}

Se conosci già le tue credenziali per l'istanza del servizio {{site.data.keyword.nlushort}}, salta questo passo.
{: tip}

1.  Vai al [servizio {{site.data.keyword.nlushort}}](https://console.{DomainName}/catalog/services/natural-language-understanding/) e registrati per un account {{site.data.keyword.Bluemix_notm}} gratuito o effettua l'accesso.
1.  Dopo aver effettuato l'accesso, digita `sentiment-tutorial` nel campo **Nome servizio** e fai clic su **Crea**.
1.  Copia le tue credenziali.
    1.  Fai clic su **Credenziali del servizio**.
    1.  Sotto **Azioni**, fai clic su **Visualizza credenziali**.
    1.  Copia i valori di `username` e `password`.

## Passo 2: Analizza la valutazione del contenuto di esempio
{: #analyze-sample}

Per prima cosa, analizza la valutazione di un determinato testo di esempio. Immetti questo comando per richiamare il metodo `GET /v1/analyze`, che analizza il testo di esempio in merito a valutazione e parole chiave. Sostituisci `{username}` e `{password}` con le credenziali del servizio che hai copiato nel passo precedente:

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## Passo 3: Restituisci informazioni sulle parole chiave
{: #analyze-keywords}

La chiamata precedente ha restituito informazioni sulla valutazione per l'intero testo. Adesso, espandi i risultati per restituire l'analisi della valutazione specificamente su ciascuna delle parole chiave. Includi il parametro **keywords.sentiment** e impostalo su `true`. Sostituisci `{username}` e `{password}` con le tue informazioni.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## Passo 4: Specifica una frase
{: #analyze-phrase}

Adesso specifica un contenuto particolare per visualizzare un'analisi a livello di proposizione o a livello di frase (anziché un'analisi di documenti o di parole chiave) includendo la frase `the%20American%20dream%20` nel parametro **sentiment.targets**. Non dimenticare di sostituire `{username}` e `{password}` con le tue informazioni.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%20We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true&sentiment.targets=the%20American%20dream"
```
{:pre}

## Passi successivi
{: #next-steps}

Hai finito! Questa esercitazione offre solo un esempio di ciò che puoi realizzare con {{site.data.keyword.nlushort}}. Per ulteriori informazioni sulle funzioni dell'API, consulta queste risorse:

- Consulta la [Guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/ "Icona link esterno"){: new_window} per i dettagli e gli esempi di ciascun parametro.
- Impara a identificare [entità e relazioni personalizzate ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/customizing.html "Icona link esterno"){: new_window}.
