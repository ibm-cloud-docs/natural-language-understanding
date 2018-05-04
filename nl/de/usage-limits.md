---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-16"

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

# Nutzungsbeschränkungen

Für {{site.data.keyword.nlushort}}-Serviceinstanzen gelten folgende Nutzungsbeschränkungen und Einschränkungen.
{: shortdesc}

## Begrenzung für analysierten Text

{{site.data.keyword.nlushort}} schneidet analysierten Text ab, der mehr als 50.000 Einzelbyte- oder Mehrbytezeichen enthält. Zur Anzeige von Text in Ihren Anforderungen, der sich diesem Grenzwert nähert, setzen Sie den Parameter `return_analyzed_text` auf `true`.

Mit dem Parameter `limit_text_characters` können Sie die Zeichenbegrenzung verringern. Wenn Sie nur einen kleinen Anteil Ihres Inhalts analysieren müssen, können Sie auf diese Weise übermäßige Kosten vermeiden.

Objekt mit Beispielparametern:
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

## Begrenzung für gleichzeitige Anforderungen

Jede {{site.data.keyword.nlushort}}-Serviceinstanz ist auf 30 gleichzeitige Anforderungen begrenzt. Diese Begrenzung kann sich bei Serviceinstanzen des Lite- und des Standard-Plans und bei der Verarbeitung von außergewöhnlich hohem Datenverkehr durch das System verringert sein. Eine Anwendung zum Beispiel, die 35 gleichzeitige Anforderungen an eine einzige Serviceinstanz stellt, überschreitet den Grenzwert für gleichzeitige Anforderungen um fünf Anforderungen, weshalb für fünf dieser Anforderungen der Fehler `429: Zu viele Anforderungen` zurückgegeben wird.

Um die Begrenzung für gleichzeitige Anforderungen zu erhöhen, [öffnen Sie ein Support-Ticket](https://ibm.biz/ibmcloudsupport).


## Sprachunterstützung

Je nach Art der Nutzung des Service gelten unterschiedliche Spracheinschränkungen. Details hierzu finden Sie auf der Seite [Sprachunterstützung](language-support.html).


