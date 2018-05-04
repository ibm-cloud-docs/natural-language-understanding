---

copyright:
  years: 2015, 2017
lastupdated: "2017-11-03"

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

# Esercitazione introduttiva
In questa breve esercitazione, introduciamo {{site.data.keyword.nlushort}} analizzando la valutazione di un testo di esempio.
{:shortdesc}

## Prima di iniziare
{: #before-you-begin}

- Crea un'istanza del servizio:
    - {: download} Se stai vedendo questo, hai creato la tua istanza del servizio. Ora ottieni le tue credenziali.
    - Crea un progetto da un servizio:
        1.  Vai alla pagina della {{site.data.keyword.watson}} Developer Console [Services ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.{DomainName}/developer/watson/services){: new_window}.
        1.  Seleziona {{site.data.keyword.nlushort}}, fai clic su **Add Services** e registrati per un account {{site.data.keyword.Bluemix_notm}} gratuito oppure esegui l'accesso.
        1.  Immetti `sentiment-tutorial` come nome progetto e fai clic su **Create Project**.
- Copia le credenziali per eseguire l'autenticazione presso la tua istanza del servizio:
    - {: download} Dal dashboard dei servizi (quello che stai guardando):
        1.  Fai clic sulla scheda **Service credentials**.
        1.  Fai clic su **View credentials** sotto **Actions**.
        1.  Copia i valori `username`, `password` e `url`.
        {: download}
    - Dal tuo progetto **sentiment-tutorial** nella Developer Console, copia i valori `username`, `password` e `url` per `"natural_language_understanding"` dalla sezione **Credentials**.
- Assicurati di avere cURL:
    - Gli esempi utilizzano cURL per richiamare i metodi dell'interfaccia HTTP. Installa la versione per il tuo sistema operativo da [curl.haxx.se ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://curl.haxx.se/){: new_window}. Installa la versione che supporta il protocollo SSL (Secure Sockets Layer). Assicurati di includere il file binario installato nella tua variabile di ambiente `PATH`.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Se utilizzi {{site.data.keyword.Bluemix_dedicated_notm}}, crea la tua istanza del servizio dalla pagina[{{site.data.keyword.nlushort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.{DomainName}/catalog/services/natural-language-understanding/){: new_window} nel catalogo. Per i dettagli su come trovare le tue credenziali del servizio, consulta [Credenziali del servizio per i servizi Watson ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Passo 1: Analizza il contenuto di esempio per la valutazione
{: #analyze-sample}

Per prima cosa, analizza la valutazione di un determinato testo di esempio. Apri un'interfaccia riga di comando ed esegui questo comando per richiamare il metodo `GET /v1/analyze`, che analizza il testo di esempio per la valutazione e le parole chiave. Sostituisci `{username}` e `{password}` con le credenziali del servizio che hai copiato nel passo precedente:

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## Passo 2: Restituisci informazioni sulle parole chiave
{: #analyze-keywords}

La chiamata precedente ha restituito informazioni sulla valutazione per l'intero testo. Adesso, espandi i risultati per restituire l'analisi della valutazione specificamente su ciascuna delle parole chiave. Includi il parametro **keywords.sentiment** e impostalo su `true`. Sostituisci `{username}` e `{password}` con le tue informazioni.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## Passo 3: Specifica una frase
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

- Consulta la [Guida di riferimento API ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/){: new_window} per i dettagli e gli esempi di ciascun parametro.
- Impara a identificare [entità e relazioni personalizzate](/docs/services/natural-language-understanding/customizing.html).
