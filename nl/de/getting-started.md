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

# Einführung - Lernprogramm
Dieses Lernprogramm bietet eine Einführung in {{site.data.keyword.nlushort}}. Hierzu wird Beispieltext analysiert, um Stimmungen zu erkennen.
{:shortdesc}

## Vorbereitende Schritte
{: #before-you-begin}

- Erstellen Sie eine Instanz des Service:
    - {: download} Wenn Ihnen dies angezeigt wird, haben Sie Ihre Serviceinstanz erstellt. Rufen Sie jetzt Ihre Berechtigungsnachweise ab.
    - Erstellen Sie ein Projekt aus einem Service:
        1.  Wechseln Sie in der {{site.data.keyword.watson}}-Entwicklerkonsole zur Seite [Services ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.{DomainName}/developer/watson/services){: new_window}.
        1.  Wählen Sie {{site.data.keyword.nlushort}} aus, klicken Sie auf **Services hinzufügen** und registrieren Sie sich entweder für ein kostenloses {{site.data.keyword.Bluemix_notm}}-Konto oder melden Sie sich an.
        1.  Geben Sie als Projektname `sentiment-tutorial` ein und klicken Sie auf **Projekt erstellen**.
- Kopieren Sie die Berechtigungsnachweise, um sich bei Ihrer Serviceinstanz zu authentifizieren:
    - {: download} Im Service-Dashboard (das Ihnen jetzt angezeigt wird) gehen Sie folgendermaßen vor:
        1.  Klicken Sie auf die Registerkarte **Serviceberechtigungsnachweise**.
        1.  Klicken Sie auf **Berechtigungsnachweise anzeigen** unter **Aktionen**.
        1.  Kopieren Sie die Werte für `Benutzername`, `Kennwort` und `URL`.
        {: download}
    - Kopieren Sie aus dem Projekt **sentiment-tutorial** in der Entwicklerkonsole die Werte für `Benutzername`, `Kennwort` und `URL` für `"natural_language_understanding"` aus dem Abschnitt **Berechtigungsnachweise**.
- Stellen Sie sicher, dass Sie cURL haben:
    - Die Beispiele verwenden cURL für den Aufruf von Methoden von der HTTP-Schnittstelle. Installieren Sie die Version für Ihr Betriebssystem aus [curl.haxx.se ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://curl.haxx.se/){: new_window}. Installieren Sie die Version, die das Secure Sockets Layer (SSL)-Protokoll unterstützt. Achten Sie darauf, die Binärdatei für die Installation in Ihre Pfadumgebungsvariable (`PATH`) einzubeziehen.

<!-- Remove this text after dedicated instances have the Developer Console: begin -->

Wenn Sie {{site.data.keyword.Bluemix_dedicated_notm}} verwenden, erstellen Sie Ihre Serviceinstanz über die Seite [{{site.data.keyword.nlushort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.{DomainName}/catalog/services/natural-language-understanding/){: new_window} im Katalog. Genauere Informationen über das Suchen nach Serviceberechtigungsnachweisen finden Sie unter [Serviceberechtigungsnachweise für Watson-Services ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/watson/getting-started-credentials.html#getting-credentials-manually){: new_window}.

<!-- Remove this text after dedicated instances have the Developer Console: end -->

## Schritt 1: Beispielinhalt analysieren, um Stimmungen zu erkennen
{: #analyze-sample}

Analysieren Sie zuerst die Stimmung eines Beispieltexts. Öffnen Sie eine Befehlszeilenschnittstelle und führen Sie den folgenden Befehl aus, um die Methode `GET /v1/analyze` aufzurufen, mit der der Beispieltext auf Stimmung und Schlüsselwörter analysiert wird. Ersetzen Sie `{username}` und `{password}` durch die Serviceberechtigungsnachweise, die Sie im vorherigen Schritt kopiert haben:

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords"
```
{:pre}

## Schritt 2: Schlüsselwortinformationen zurückgeben
{: #analyze-keywords}

Mit dem vorherigen Aufruf wurden Informationen zu Stimmungen für den gesamten Text zurückgegeben. Nun können Sie die Ergebnisse erweitern und eine Stimmungsanalyse speziell für die einzelnen Schlüsselwörter zurückgeben. Geben Sie den Parameter **keywords.sentiment** an und legen Sie dafür den Wert `true` fest. Ersetzen Sie `{username}` und `{password}` durch Ihre entsprechenden Informationen.

```bash
curl --user "{username}":"{password}" \
"https://gateway.watsonplatform.net/natural-language-understanding/api/v1/analyze?version=2017-02-27&text=I%20still%20have%20a%20dream%2C%20a%20dream%20deeply%20rooted%20in%20the%20American%20dream%20%E2%80%93%20one%20day%20this%20nation%20will%20rise%20up%20and%20live%20up%20to%20its%20creed%2C%20%22We%20hold%20these%20truths%20to%20be%20self%20evident%3A%20that%20all%20men%20are%20created%20equal.&features=sentiment,keywords&keywords.sentiment=true"
```
{:pre}

## Schritt 3: Analyse für einem bestimmten Ausdruck ausführen
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

- Details und Beispiele zu den einzelnen Parametern finden Sie in der [API-Referenz![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1/){: new_window}.
- Informieren Sie sich, wie [angepasste Entitäten und Beziehungen](/docs/services/natural-language-understanding/customizing.html) ermittelt werden.
