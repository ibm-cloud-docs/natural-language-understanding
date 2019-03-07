---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-08"

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

# Prezzi
{: #pricing}

{{site.data.keyword.nlushort}} ha tre piani di prezzo: Lite, Standard e Premium.

Questa pagina contiene le informazioni sui prezzi in USD. Per visualizzare le informazioni sui prezzi nella tua valuta locale, consulta la pagina [{{site.data.keyword.nlushort}}](https://{DomainName}/catalog/services/natural-language-understanding) nel catalogo {{site.data.keyword.cloud}}.
{: tip}

## Lite
{: #lite}

Il piano Lite è gratuito per gli utenti che intendono provare Natural Language Understanding o creare un modello di verifica (PoC, proof-of-concept).

**Prezzi**
- 30.000 elementi NLU gratuiti/mese

**Modello personalizzato**
- 1 modello personalizzato gratuito

## Standard
{: #standard}

Un piano con "pagamento a consumo" consigliato quando sei pronto a spostare la tua applicazione dal modello di verifica (PoC, proof-of-concept) alla produzione.

**Prezzi** (fatturazione mensile)
- Livello 1: $0,003/elemento NLU per i primi 1-250.000 elementi NLU
- Livello 2: $0,001/elemento NLU per 250.001-5.000,000 di elementi NLU
- Livello 3: $0,0002/elemento NLU per gli elementi NLU aggiuntivi dopo quota 5.000.000

**Modello personalizzato** ($/modello personalizzato/mese)
- $800 per tutti i livelli

## Premium
{: #premium}

Un piano che offre un livello più elevato di sicurezza e isolamento per aiutare i clienti con requisiti di dati sensibili.

_Per i dettagli, ti invitiamo a [contattare il settore Vendite](https://www.ibm.com/account/reg/us-en/signup?formid=MAIL-watson)._

## Cos'è un elemento NLU?
{: #nlu-items}

L'utilizzo dell'API viene misurato in **elementi NLU**. Un elemento NLU è una singola **unità di testo** (fino a 10.000 caratteri di testo) che viene analizzata per una **funzione**, come ad esempio il parere.

Per tenere traccia del numero di elementi NLU nella tua richiesta, puoi esaminare l'oggetto `usage` nella risposta. Ad esempio, l'analisi di 15.000 caratteri di testo per parere, emozione e parole chiave restituirà le seguenti informazioni di utilizzo.

```json
"usage": {
  "text_units": 2,
  "text_characters": 15000,
  "features": 3
}
```
{: code}
  
Ci sono **2** unità di testo e **3** funzioni nella richiesta, quindi ci sono **2 × 3 = 6** elementi NLU.

Le unità di testo sono conteggiate in modo separato per ogni richiesta. Se una richiesta analizza 15.000 caratteri e un'altra richiesta analizza 3.000 caratteri, questo conta come un totale di 3 unità di testo. La prima richiesta ha 2 unità di testo e la seconda richiesta ha 1 unità di testo.

## Domande frequenti (FAQ) 
{: #faq}

### Voglio capire il parere su 20.000 tweet. Come stimo quanto pagherò con il piano Standard?

- Passo 1. Calcola il numero di unità di testo per ogni richiesta.<br>
A partire da novembre 2018, il numero massimo di caratteri consentiti in un tweet è 280.<br>
Questo si traduce in un'unica unità di testo per ogni richiesta.

- Passo 2. Calcola il numero di funzioni per ogni richiesta<br>
Una funzione, parare, è abilitata in ciascuna richiesta.

- Passo 3: Calcola il numero di elementi NLU per ogni richiesta <br>
Elementi NLU = (Numero di unità di testo) × (Numero di funzioni)<br>
Elementi NLU = 1 unità di testo × 1 funzione = 1 elemento NLU

- Passo 4: Calcola il numero totale di elementi NLU<br>
Numero totale di elementi NLU = (Numero di richieste) × (Numero di voci NLU per ogni richiesta)<br>
Numero totale di elementi NLU = 20.000 richieste × 1 elemento NLU per ogni richiesta = 20.000 elementi NLU in totale

- Passo 5: Stima il prezzo per il numero totale di elementi NLU<br>
Per il piano dei prezzi Standard, i primi 250.000 elementi dell'NLU sono addebitati a $0,003 per ogni elemento<br>
Prezzo stimato = (Numero di elementi NLU) × (Prezzo per ogni elemento NLU) <br>
Prezzo stimato = 20,000 elementi NLU × $0,003 = $60

**Costo totale = $60**

### Voglio estrarre entità, parole chiave e categorie per 50.000 documenti con una media di 12.000 caratteri per ogni documento. Quale sarà il mio prezzo stimato sul piano Standard?
- Passo 1. Calcola il numero di unità di testo per ogni richiesta.<br>
Unità di testo = Numero di gruppi di 10000 caratteri o meno <br>
12.000 caratteri per ogni richiesta = 2 unità di testo per ogni richiesta

- Passo 2. Calcola il numero di funzioni per ogni richiesta<br>
Entità, parole chiave, categorie = 3 funzioni

- Passo 3: Calcola il numero di elementi NLU per ogni richiesta <br>
Elementi NLU = (Numero di unità di testo) × (Numero di funzioni) <br>
Elementi NLU = 2 unità di dati × 3 arricchimenti = 6 elementi NLU

- Passo 4: Calcola il numero totale di elementi NLU<br>
Numero totale di elementi NLU = (Numero di richieste o documenti) × (Numero di elementi NLU) <br>
Numero totale di elementi NLU = 50.000 richieste × 6 elementi NLU = 300.000 elementi NLU

- Passo 5: Stima il prezzo per il numero totale di elementi NLU <br>
I primi 250.000 elementi dell'NLU sono addebitati a $0,003 per ogni elemento<br>
Ulteriori elementi NLU fino al 5.000.000esimo elemento NLU sono addebitati a $0,001 per ogni elemento<br>
Prezzo stimato = (250.000 elementi NLU × $0,003) + (50.000 elementi NLU × $0,001) <br>
Prezzo stimato = $750 + $50


**Costo totale = $800**

### Come calcolare il prezzo del piano Standard per 15.000 elementi NLU?
- Poiché i primi 250.000 elementi NLU hanno un prezzo di $0,003/elemento, i tuoi 15.000 elementi NLU sono addebitati a $0,003 per ogni elemento (Livello 1). Il tuo prezzo stimato sarà pari a $45. 

### Come calcolare il prezzo del piano Standard per 6.000.000 elementi NLU?
- Poiché hai più di 5.000.000 di elementi NLU, i tuoi primi 250.000 elementi NLU sono addebitati a $0.003 per ogni elemento (Livello 1), i successivi 4.750.000 elementi NLU sono addebitati a $0,001 per ogni elemento (livello 2) e il restante 1.000.000 di elementi NLU sono addebitati a $0,0002 per ogni elemento (Livello 3). Il tuo prezzo stimato sarà pari a $5,700. 



