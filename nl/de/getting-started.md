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

# Einführung - Lernprogramm
Dieses Lernprogramm bietet eine Einführung in {{site.data.keyword.nlushort}}. Hierzu wird Beispieltext analysiert, um Stimmungen zu erkennen.
{:shortdesc}

## Schritt 1: Anmelden, Serviceinstanz erstellen und Berechtigungsnachweise abrufen
{: #create-service}

Wenn Ihre Berechtigungsnachweise für die {{site.data.keyword.nlushort}}-Serviceinstanz bereits vorliegen, können Sie diesen Schritt überspringen.
{: tip}

1.  Rufen Sie den [{{site.data.keyword.nlushort}}-Service](https://console.{DomainName}/catalog/services/natural-language-understanding/) auf und melden Sie sich entweder für ein kostenfreies {{site.data.keyword.Bluemix_notm}}-Konto an oder führen Sie eine Anmeldung durch.
1.  Geben Sie nach der Anmeldung `sentiment-tutorial` im Feld **Servicename** ein und klicken Sie auf **Erstellen**.
1.  Kopieren Sie Ihre Berechtigungsnachweise:
    1.  Klicken Sie auf **Serviceberechtigungsnachweise**.
    1.  Klicken Sie auf **Berechtigungsnachweise anzeigen** unter **Aktionen**.
    1.  Kopieren Sie die Werte für den `Benutzernamen` und das `Kennwort`.

## Schritt 2: Beispielinhalt analysieren, um Stimmungen zu erkennen
{: #analyze-sample}

Analysieren Sie zuerst die Stimmung eines Beispieltexts. Geben Sie diesen Befehl ein, um die Methode `GET /v1/analyze` aufzurufen, mit der der Beispieltext analysiert wird, um Stimmungen und Schlüsselwörter zu erkennen. Ersetzen Sie `{username}` und `{password}` durch die Serviceberechtigungsnachweise, die Sie im vorherigen Schritt kopiert haben:

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## Schritt 3: Schlüsselwortinformationen zurückgeben
{: #analyze-keywords}

Mit dem vorherigen Aufruf wurden Informationen zu Stimmungen für den gesamten Text zurückgegeben. Nun können Sie die Ergebnisse erweitern und eine Stimmungsanalyse speziell für die einzelnen Schlüsselwörter zurückgeben. Geben Sie den Parameter **keywords.sentiment** an und legen Sie dafür den Wert `true` fest. Ersetzen Sie `{username}` und `{password}` durch Ihre entsprechenden Informationen.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## Schritt 4: Analyse für einem bestimmten Ausdruck ausführen
{: #analyze-phrase}

Nun können Sie einen bestimmen Inhalt als Ziel der Analyse angeben und so eine Analyse auf Satz- oder Ausdrucksebene (anstelle einer Dokument- oder Schlüsselwortanalyse) durchführen. Geben Sie hierzu den Ausdruck `the%20American%20dream%20` im Parameter **sentiment.targets** an. Denken Sie daran, `{username}` und `{password}` durch Ihre entsprechenden Informationen zu ersetzen. 

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%20We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true&sentiment.targets=the%20American%20dream"
```
{:pre}

## Weitere Schritte
{: #next-steps}

Fertig! Dieses Lernprogramm vermittelt nur einen ersten Eindruck dessen, was mit {{site.data.keyword.nlushort}} alles möglich ist. Weitere Informationen zu den Features der API finden Sie in den folgenden Ressourcen:

- Details und Beispiele zu den einzelnen Parametern finden Sie in der [API-Referenz![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/ "Symbol für externen Link"){: new_window}.
- Lesen Sie die Informationen zum Identifizieren von [angepassten Entitäten und Beziehungen![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding/customizing.html "Symbol für externen Link"){: new_window}.
