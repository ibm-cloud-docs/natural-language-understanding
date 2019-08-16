---

copyright:
  years: 2015, 2018
lastupdated: "2018-12-19"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:go: .ph data-hd-programlang='go'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}
{:download: .download}
{:apikey: data-credential-placeholder='apikey'}
{:url: data-credential-placeholder='url'}
{:hide-dashboard: .hide-dashboard}

# Einführung - Lernprogramm
{: #getting-started}

In diesem kurzen Lernprogramm wird die {{site.data.keyword.nlushort}}-API mit Beispielanforderungen und Links zu weiteren Ressourcen vorgestellt.
{:shortdesc}

## Vorbereitende Schritte
{: #before-you-begin}

- {: hide-dashboard} Erstellen Sie eine Instanz des Service:
    1.  Rufen Sie im {{site.data.keyword.Bluemix_notm}}-Katalog die Seite für [{{site.data.keyword.nlushort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/catalog/services/natural-language-understanding){: new_window} auf.
    2.  Registrieren Sie sich entweder für ein kostenloses {{site.data.keyword.Bluemix_notm}}-Konto oder melden Sie sich an.
    3.  Klicken Sie auf **Erstellen**.
- Kopieren Sie die Berechtigungsnachweise, um sich bei Ihrer Serviceinstanz zu authentifizieren:
    1.  Klicken Sie auf der Seite **Verwalten** auf **Anzeigen**, damit Ihre Berechtigungsnachweise angezeigt werden.
    2.  Kopieren Sie die Werte für `API-Schlüssel` und `URL`.
- Stellen Sie sicher, dass Sie über den `curl`-Befehl verfügen:
    - In den Beispielen wird der `curl`-Befehl verwendet, um Methoden der HTTP-Schnittstelle aufzurufen. Installieren Sie die Version für Ihr Betriebssystem aus [curl.haxx.se ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://curl.haxx.se/){: new_window}. Installieren Sie die Version, die das Secure Sockets Layer (SSL)-Protokoll unterstützt. Achten Sie darauf, die Binärdatei für die Installation in Ihre Pfadumgebungsvariable (`PATH`) einzubeziehen.

In diesem Lernprogramm erfahren Sie, wie Sie die {{site.data.keyword.nlushort}}-API über eine Befehlszeilenschnittstelle verwenden. Wenn Sie Clientbibliotheken für unterschiedliche Programmiersprachen herunterladen wollen, informieren Sie sich anhand der Informationen zu den [Watson-SDKs](/docs/services/natural-language-understanding?topic=watson-using-sdks#using-sdks).
{:tip}

## Schritt 1: Webseite analysieren
{: #analyze-sample}

Führen Sie den folgenden Befehl zum Analysieren einer Webseite aus, um Stimmung, Konzepte, Kategorien, Entitäten und Schlüsselwörter abzurufen. <span class="hide-dashboard">Ersetzen Sie dabei `{apikey}` und `{url}` durch die entsprechenden Berechtigungsnachweise für Ihren Service.</span>

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--header "Content-Type: application/json" \
--data '{
  "url": "http://newsroom.ibm.com/Guerbet-and-IBM-Watson-Health-Announce-Strategic-Partnership-for-Artificial-Intelligence-in-Medical-Imaging-Liver",
  "features": {
    "sentiment": {},
    "categories": {},
    "concepts": {},
    "entities": {},
    "keywords": {}
  }
}'
```
{: pre}

Der nächste Schritt veranschaulicht, wie Optionen angegeben werden, um die Analyse für die einzelnen Features entsprechend anzupassen.

## Schritt 2: Zielausdrücke und Schlüsselwörter analysieren
{: #analyze-phrase}

{{site.data.keyword.nlushort}} kann Zielausdrücke im Kontext des umgebenden Textes analysieren, um fokussierte Stimmungs- und Emotionsergebnisse zu erzielen. Im nachfolgenden Beispiel wird dem Service mit der Option **targets** für die Stimmung mitgeteilt, dass er nach den Zielen 'apples', 'oranges' und 'broccoli' suchen soll. Da im Text sowohl der Ausdruck 'apples' als auch der Ausdruck 'oranges' vorkommt, werden für diese Ziele Stimmungsbewertungen zurückgegeben.

Für Entitäten und Schlüsselwörter, die in Ihrem Text erkannt werden, können Sie auch Stimmungs- und Emotionsergebnisse abrufen. Im nachfolgenden Beispiel wird der Service mit der Option **emotion** für Schlüsselwörter angewiesen, jedes erkannte Schlüsselwort auf Emotionsergebnisse hin zu analysieren.

```bash
curl -X POST -u "apikey:{apikey}"{: apikey} \
"{url}/v1/analyze?version=2018-11-16"{: url} \
--request POST \
--header "Content-Type: application/json" \
--data '{
  "text": "I love apples! I do not like oranges.",
  "features": {
    "sentiment": {
      "targets": [
        "apples",
        "oranges",
        "broccoli"
      ]
    },
    "keywords": {
      "emotion": true
    }
  }
}'
```
{: pre}

## Weitere Schritte
{: #next-steps}

- Konsultieren Sie die [API-Referenz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/apidocs/natural-language-understanding){: new_window}.
- Informieren Sie sich, wie [angepasste Entitäten und Beziehungen](/docs/services/natural-language-understanding?topic=natural-language-understanding-customizing) ermittelt werden.
