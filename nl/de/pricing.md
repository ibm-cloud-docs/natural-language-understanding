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

# Preisstruktur
{: #pricing}

Für {{site.data.keyword.nlushort}} werden drei Preistarife angeboten: Lite, Standard und Premium.

Diese Seite enthält Preisinformationen in USD. Preisinformationen in Ihrer lokalen Währung finden Sie im Katalog von {{site.data.keyword.cloud}} auf der [Seite für {{site.data.keyword.nlushort}}](https://{DomainName}/catalog/services/natural-language-understanding).
{: tip}

## Lite
{: #lite}

Der Preisstrukturplan 'Lite' ist kostenlos für Benutzer, die Natural Language Understanding ausprobieren möchten oder einen Machbarkeitsnachweis erbringen wollen.

**Preisstruktur**
- 30.000 NLU-Elemente pro Monat kostenlos

**Angepasstes Modell**
- 1 kostenloses angepasstes Modell

## Standard
{: #standard}

Ein nutzungsabhängiger Preistarif, der empfohlen wird, sobald Sie soweit sind, dass Sie Ihre Anwendung vom Machbarkeitsnachweis in die Produktion befördern wollen.

**Preisstruktur** (monatliche Rechnungsstellung)
- Preisstufe 1: $ 0,003/NLU-Element für die ersten 1-250.000 NLU-Elemente
- Preisstufe 2: $ 0,001/NLU-Element für 250.001 bis 5.000.000 NLU-Elemente
- Preisstufe 3: $ 0,0002/NLU-Element für zusätzliche NLU-Elemente jenseits 5.000.000

**Angepasstes Modell** ($/angepasstes Modell/Monat)
- $ 800 für alle Preisstufen

## Premium
{: #premium}

Dieser Preistarif bietet ein höheres Maß an Sicherheit und Isolation und ist für Kunden mit speziellen Anforderungen aufgrund sensibler Daten konzipiert.

_Bitte [wenden Sie sich an den Vertrieb](https://www.ibm.com/account/reg/us-en/signup?formid=MAIL-watson), um entsprechende Details zu erhalten._

## Was ist ein NLU-Element?
{: #nlu-items}

Die API-Nutzung wird in **NLU-Elementen** gemessen. Ein NLU-Element entspricht einer **Texteinheit** (d. h. bis zu 10.000 Textzeichen), die auf ein **Feature** wie zum Beispiel die Stimmung analysiert werden.

Um die Anzahl der NLU-Elemente in Ihrer Anforderung nicht aus dem Blick zu verlieren, können Sie das Objekt `usage` in der Antwort untersuchen. Bei der Analyse von 15.000 Textzeichen auf Stimmung, Emotion und Schlüsselwörter werden zum Beispiel die folgenden Nutzungsinformationen zurückgegeben.

```json
"usage": {
  "text_units": 2,
  "text_characters": 15000,
  "features": 3
}
```
{: code}
  
Da die Anforderung **2** Texteinheiten und **3** Features enthält, umfasst sie **2 × 3 = 6** NLU-Elemente.

Texteinheiten werden für jede Anforderung jeweils getrennt gezählt. Wenn bei einer Anforderung 15.000 Zeichen analysiert werden und bei einer weiteren Anforderung 3.000 Zeichen, so zählt dies insgesamt als 3 Texteinheiten. Die erste Anforderung umfasst 2 Texteinheiten und die zweite Anforderung umfasst eine 1 Texteinheit.

## Häufig gestellte Fragen - FAQs
{: #faq}

### Ich möchte die Stimmung in 20.000 Tweets verstehen. Wie kann ich abschätzen, mit welchen Kosten ich schätzungsweise im Rahmen des Preistarifs 'Standard' zu rechnen habe?

- Schritt 1: Anzahl von Texteinheiten pro Anforderung berechnen<br>
Mit Wirkung ab November 2018 ist die maximal zulässige Anzahl von Zeichen in einem Tweet auf 280 beschränkt.<br>
Dies entspricht einer Texteinheit pro Anforderung.

- Schritt 2: Anzahl von Features pro Anforderung berechnen<br>
In jeder Anforderung ist ein Feature aktiviert, nämlich die Stimmung.

- Schritt 3: Anzahl von NLU-Elementen pro Anforderung berechnen<br>
NLU-Elemente = (Anzahl von Texteinheiten) × (Anzahl von Features)<br>
NLU-Elemente = 1 Texteinheit × 1 Feature = 1 NLU-Element

- Schritt 4: Gesamtzahl von NLU-Elementen berechnen <br>
Gesamtzahl von NLU-Elementen = (Anzahl von Anforderungen) × (Anzahl von NLU-Elementen pro Anforderung) <br>
Gesamtzahl von NLU-Elementen = 20.000 Anforderungen × 1 NLU-Element pro Anforderung = 20.000 Gesamtzahl von NLU-Elementen

- Schritt 5: Voraussichtlichen Preis für die Gesamtzahl von NLU-Elementen als Kostenschätzung berechnen<br>
Beim Preistarif 'Standard' werden die ersten 250.000 NLU-Elemente jeweils mit $ 0,003 pro Element berechnet.<br>
Geschätzter Preis = (Anzahl von NLU-Elementen) × (Preis pro NLU-Element) <br>
Geschätzter Preis = 20.000 NLU-Elemente × $ 0,003 = $ 60

**Gesamtkosten = $ 60**

### Ich möchte Entitäten, Schlüsselwörter und Kategorien für 50.000 Dokumente mit einem Durchschnitt von 12.000 Zeichen pro Dokument extrahieren. Mit welchem Preis habe ich im Rahmen des Preistarifs 'Standard' schätzungsweise zu rechnen?
- Schritt 1: Anzahl von Texteinheiten pro Anforderung berechnen <br>
Texteinheiten = Anzahl von Gruppen von 10.000 Zeichen oder weniger <br>
12.000 Zeichen pro Anforderung = 2 Texteinheiten pro Anforderung

- Schritt 2: Anzahl von Features pro Anforderung berechnen<br>
Entitäten, Schlüsselwörter, Kategorien = 3 Features

- Schritt 3: Anzahl von NLU-Elementen pro Anforderung berechnen <br>
NLU-Elemente = (Anzahl von Texteinheiten) × (Anzahl von Features) <br>
NLU-Elemente = 2 Dateneinheiten × 3 Aufbereitungen = 6 NLU-Elemente

- Schritt 4: Gesamtzahl von NLU-Elementen berechnen <br>
Gesamtzahl von NLU-Elementen = (Anzahl von Anforderungen oder Dokumenten) × (Anzahl von NLU-Elementen) <br>
Gesamtzahl von NLU-Elementen = 50.000 Anforderungen × 6 NLU-Elemente = 300.000 NLU-Elemente

- Schritt 5: Voraussichtlichen Preis für die Gesamtzahl von NLU-Elementen als Kostenschätzung berechnen <br>
Für die ersten 250.000 NLU-Elemente werden jeweils $ 0,003 pro Element berechnet<br>
Alle weiteren NLU-Elemente bis zum Element 5.000.000 werden mit $ 0,001 pro Element berechnet<br>
Geschätzter Preis = (250.000 NLU-Elemente × $ 0,003) + (50.000 NLU-Elemente × $ 0,001) <br>
Geschätzter Preis = $ 750 + $ 50


**Gesamtkosten = $ 800**

### Wie berechne ich den Preis für 15.000 NLU-Elemente für den Tarifplan 'Standard'?
- Da für die ersten 250.000 NLU-Elemente jeweils $ 0,003 pro Element berechnet werden, wird für Ihre 15.000 NLU-Elemente $ 0,003 pro Element berechnet (Preisstufe 1). Der geschätzte Preis würde sich auf $ 45 belaufen. 

### Wie berechne ich den Preis für 6.000.000 NLU-Elemente für den Tarifplan 'Standard'?
- Da es sich um mehr als 5.000.000 NLU-Elemente handelt, wird für die ersten 250.000 NLU-Elemente jeweils $ 0,003 pro Element berechnet (Preisstufe 1) berechnet. Für die nächsten 4.750.000 NLU-Elemente wird $ 0,001 pro Element (Preisstufe 2) berechnet und für die restlichen 1.000.000 NLU-Elemente wird $ 0,0002 pro Element berechnet (Preisstufe 3). Der geschätzte Preis würde sich auf $ 5.700 belaufen. 



