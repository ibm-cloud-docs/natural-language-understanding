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

# Nutzungsbeschränkungen
{: #usage-limits}

Für {{site.data.keyword.nlushort}}-Serviceinstanzen gelten folgende Nutzungsbeschränkungen und Einschränkungen.
{: shortdesc}

## Begrenzung für analysierten Text
{: #analyzed-text}

{{site.data.keyword.nlushort}} schneidet analysierten Text ab, der mehr als 50.000 Einzelbyte- oder Mehrbytezeichen enthält. Zur Anzeige von Text in Ihren Anforderungen, der sich diesem Grenzwert nähert, setzen Sie den Parameter `return_analyzed_text` auf `true`.

Mit dem Parameter `limit_text_characters` können einen niedrigeren Grenzwert für die Zeichenbegrenzung festlegen. Wenn Sie nur einen kleinen Anteil Ihres Inhalts analysieren möchten, können Sie auf diese Weise übermäßige Kosten vermeiden.

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

## Grenzwert für die Anzahl gleichzeitiger Anforderungen
{: #concurrent-requests}

Für jede {{site.data.keyword.nlushort}}-Serviceinstanz gilt ein Grenzwert von 30 gleichzeitigen Anforderungen. Bei Serviceinstanzen des Lite- und des Standard-Plans kann dieser Grenzwert sinken, wenn im System außergewöhnlich hoher Datenverkehr auftritt. Eine Anwendung, die 35 gleichzeitige Anforderungen von einer einzigen Serviceinstanz stellt, überschreitet  zum Beispiel den Grenzwert für gleichzeitige Anforderungen um fünf Anforderungen. Aus diesem Grund wird für fünf Anforderungen der Fehler `429: Zu viele Anforderungen` zurückgegeben.

Wenn Sie einen höheren Grenzwert für gleichzeitige Anforderungen festlegen wollen, [öffnen Sie ein Support-Ticket](https://ibm.biz/ibmcloudsupport).

## Größenbegrenzung des angepassten Modells für Lite-Preistarife
{: #custom-models}

Für angepasste {{site.data.keyword.knowledgestudioshort}}-Modelle, die im Rahmen von Lite-Preistarifen auf Serviceinstanzen von {{site.data.keyword.nlushort}} bereitgestellt werden, gelten Größenbeschränkungen. Diese Größenbeschränkung für angepasste Modelle können Sie entfernen, indem Sie für Ihre Serviceinstanz von {{site.data.keyword.nlushort}} ein Upgrade auf einen gebührenpflichtigen Preistarif durchführen. Ihre Serviceinstanzen werden auf der {{site.data.keyword.cloud_notm}} [Seite 'Ressourcen'](https://{DomainName}/resources) aufgelistet.

## Sprachunterstützung
{: #language-support}

Je nach Art der Nutzung des Service gelten unterschiedliche Spracheinschränkungen. Details hierzu finden Sie auf der Seite [Sprachunterstützung](/docs/services/natural-language-understanding?topic=natural-language-understanding-language-support).


